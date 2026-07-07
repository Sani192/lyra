# API Documentation

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative directory mapping for API interfaces, generated OpenAPI specifications, and protocol adapter routing.

## Purpose

This directory acts as the centralized catalog for all public and internal API interface descriptions exposed by Lyra.

## Contents & Scope

During the Product Engineering phase, this directory will host:
* Generated OpenAPI v3 specification files (`openapi.json`, `swagger.yaml`).
* Route configuration manifests mapping public endpoints to internal Conversation and Workflow Engine controllers.
* Protocol adapter definitions converting edge streaming WebSockets or REST requests into platform-neutral event payloads.

## References

All API structures must trace back to the requirements defined in:
* [Public API Specification](../specifications/18-public-api.md)
* [Protocol Layer Specification](../specifications/15-protocol-layer.md)
