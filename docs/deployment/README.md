# Deployment Documentation

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative directory mapping for Kubernetes configs, environment parameters, and container configuration rules.

## Purpose

This directory acts as the centralized catalog for hosting, orchestrating, and configuring Lyra microservices in staging and production environments.

## Contents & Scope

This directory scopes:
* **Infrastructure Manifests:** Kubernetes deployment files, Helm charts, and ingress routing rules.
* **Environment Configuration Templates:** Sample configurations defining environment variable keys, port maps, and required secret tags.
* **Vault Integration Schemas:** Structural namespaces for HashiCorp Vault integrations to securely inject consumer API keys into runtime container environments.

## References

* [Deployment Specification](../specifications/22-deployment.md)
* [System Overview Architecture](../architecture/system-overview.md)
