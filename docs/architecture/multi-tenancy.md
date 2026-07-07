# Multi-Tenancy Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design and specifications for Lyra tenant isolation and data partitioning.

## Purpose

Define the logical and physical mechanisms governing multi-tenant isolation, database structures, object storage partitioning, and credential segregation to guarantee data privacy and compliance.

## Multi-Tenancy Principles

Lyra is a multi-tenant platform designed to host multiple organizations, projects, and environments on shared compute resources. Separation of tenant data must be guaranteed at the database, file storage, cache, and credential storage layers.

```
       +------------------------------------------------------+
       | API Ingress Route Filter                             |
       | (Extracts tenant_id and organization_id from token) |
       +--------------------------+---------------------------+
                                  |
                                  v
+---------------------------------+---------------------------------+
| System Execution Boundary                                         |
|                                                                   |
|  +---------------------+  +-----------------+  +---------------+  |
|  | PostgreSQL DB       |  | S3 Object Store |  | HashiCorp     |  |
|  |                     |  |                 |  | Vault         |  |
|  | Enforces Row-Level  |  | Bucket Key      |  | Tenant-Scoped |  |
|  | Security (RLS) keys |  | Partition Paths |  | Secrets Paths |  |
|  +---------------------+  +-----------------+  +---------------+  |
|                                                                   |
+-------------------------------------------------------------------+
```

### 1. Database Row-Level Security (RLS)
The metadata RDBMS (PostgreSQL) uses Logical Isolation:
* Every table schema contains a mandatory `tenant_id` and `organization_id` foreign key.
* PostgreSQL Row-Level Security (RLS) policies are active on all tables.
* Every database session connection initialized by Lyra microservices must set the tenant context parameter:
  ```sql
  SET LOCAL app.current_tenant_id = 'tenant-xyz';
  ```
* Queries without a valid tenant context fail automatically.

### 2. Object Storage Partitioning (S3)
Raw transcripts and audio recordings are stored in a centralized S3-compatible object store. Key paths enforce separation by prefix:
```
s3://[bucket_name]/[organization_id]/[project_id]/[environment]/[session_id]/[filename]
```
Example partition:
```
s3://lyra-audio-logs/org_health_care/proj_scheduler/production/a90d8a6b-c743/turn_001_input.wav
```
Downstream IAM policies and key-encryption-keys (KEK) restrict access to these paths using condition-key constraints matched to the tenant namespace.

### 3. Cache Isolation
In-memory caches (Redis) partition keys using tenant-scoped namespaces:
```
lyra:{organization_id}:{project_id}:{environment}:{cache_category}:{key}
```
Example Redis key:
```
lyra:org_health_care:proj_scheduler:prod:session:a90d8a6b:turns
```

### 4. Secret Namespacing
Tenant credentials used to access external consumer applications (e.g. API keys or OAuth2 secrets) are stored in HashiCorp Vault:
* Each organization is assigned a distinct Vault namespace policy.
* Access paths restrict read permissions to the specific tenant ID:
  ```
  secret/data/organizations/[organization_id]/projects/[project_id]/[environment]/credentials
  ```
* Pod service accounts retrieve these tokens via Kubernetes Vault Agent sidecars.
