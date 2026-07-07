# 15. Protocol Layer

## Maturity Metadata

**Status:** Draft.

**Intended Use:** Design specifications for API adapters and protocols.

## Purpose

Define the Protocol Layer, adapter routing, REST mapping, and Model Context Protocol (MCP) integrations.

## Scope

Covers edge transport APIs.

## Business Motivation

Ensures seamless compatibility with legacy REST endpoints and modern MCP toolservers.

## Assumptions

- Adapters translate payload structures but do not modify business values.

## Dependencies

- None.

## References

- [PROJECT.md](../../PROJECT.md)
- [ADR-0005: Why REST, OpenAPI, and MCP Are First-Class Protocols](../decisions/ADR-0005.md)

## Planned Requirement Categories

- `LYRA-FR-PROT` (Protocol mapping specifications)

## Future Expansion Guidance

Provide websocket handshake rules and MCP endpoint definitions.
