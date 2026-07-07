# Security Architecture

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative architectural design, threat boundaries, and security specifications for Lyra.

## Purpose

Define the platform's security framework, outlining threat boundaries, credential management policies, encryption standards, and data protection/redaction rules to maintain system integrity.

## Threat Boundaries and Data Flows

Lyra establishes strict security boundaries where untrusted external clients (such as voice channels and web portals) connect to protocol adapters, while internal services interact under a zero-trust model.

```
 [ Untrusted Client ]
       | Voice Stream (TLS 1.3 / WSS)
       v
=======|================================================================
 Boundary 1: Edge TLS & Ingress Security
=======|================================================================
       v
 [ Protocol Adapter ]
       | Internal Event (mTLS)
       v
 [ Conversation Engine / Workflow Engine ]
       | Check Contract (mTLS)
       v
=======|================================================================
 Boundary 2: Tenant Isolation & Credential Access
=======|================================================================
       v
 [ Capability Registry ] ---> Fetches secrets from [ HashiCorp Vault ]
       | Injects Bearer Token
       v
 [ External Consumer REST API ]
```

### 1. Data Encryption Standards
* **Encryption in Transit:** All public network interfaces enforce TLS 1.3 (with fallback to TLS 1.2 using secure cipher suites: e.g., ECDHE-RSA-AES256-GCM-SHA384). WebSocket connections use secure `wss://` endpoints.
* **Encryption at Rest:**
  * PostgreSQL databases use Transparent Data Encryption (TDE).
  * S3 buckets use server-side encryption (SSE-KMS) with customer-managed keys (CMK) configured in AWS KMS or equivalent cloud key vaults.
  * Audit logs and active turn histories are encrypted at rest using AES-256.

### 2. Authentication & Authorization
* **External Client APIs:** Access to Lyra REST interfaces requires JWT (JSON Web Tokens) signed by Lyra's central authentication service or tenant-configured OAuth2 providers.
* **Service-to-Service Communication:** All internal microservices communication within the Kubernetes cluster is encrypted and authenticated using mutual TLS (mTLS) enforced via service mesh sidecars (e.g., Istio or Linkerd).
* **Consumer API Keys:** Credentials used to authenticate outgoing calls to consumer systems are retrieved just-in-time from HashiCorp Vault and are never cached in plain text or written to log files.

### 3. Audio & Transcript PII Redaction
To ensure compliance with strict privacy standards (such as HIPAA and GDPR):
* Transcripts are routed through a PII Redaction service post-turn.
* Standard regular expressions and named-entity-recognition (NER) models identify and redact patient/customer names, social security numbers, credit card details, and insurance identifiers.
* Only the redacted transcript is persisted to S3 for archiving.
* Raw audio files are subject to retention policies automatically deleting them after 30 days unless a tenant policy explicitly overrides it.
