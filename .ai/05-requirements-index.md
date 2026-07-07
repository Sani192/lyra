# 05 Requirements Index

## Purpose

This file defines requirement ID conventions and how implementation traces back to specifications.

## ID Conventions

| Prefix | Meaning | Example |
| --- | --- | --- |
| `LYRA-FR` | Functional requirement | `LYRA-FR-001` |
| `LYRA-NFR` | Non-functional requirement | `LYRA-NFR-001` |
| `LYRA-SEC` | Security requirement | `LYRA-SEC-001` |
| `LYRA-CIF` | Capability Intelligence Framework requirement | `LYRA-CIF-001` |
| `LYRA-API` | Public API requirement | `LYRA-API-001` |
| `LYRA-UI` | Dashboard or UI requirement | `LYRA-UI-001` |
| `LYRA-OBS` | Observability requirement | `LYRA-OBS-001` |
| `LYRA-DEP` | Deployment requirement | `LYRA-DEP-001` |

## Traceability Rule

Every implementation, schema, contract, example, test, and ADR that changes behavior must reference at least one requirement ID. If no ID exists, update the relevant specification before implementing.

## Source Documents

Functional requirements live in `docs/specifications/06-functional-requirements.md`; NFRs in `07-non-functional-requirements.md`; security, API, UI, observability, deployment, and CIF requirements live in their numbered specification chapters.
