# 08 Common Mistakes

## Maturity Metadata

**Status:** Approved.

**Intended Use:** Authoritative AI-agent operating context; safe for repository navigation and contribution workflow decisions.


* Do not store business data such as orders, appointments, payments, customer profiles, loyalty status, pricing, or inventory.
* Do not duplicate consumer business logic in Lyra workflows.
* Do not skip documentation because a change appears small.
* Do not violate consumer contracts or silently reinterpret schema fields.
* Do not introduce protocol-specific behavior into core domain models.
* Do not create shortcuts that bypass validation, observability, tenant isolation, or review.
* Do not create examples that imply Lyra is the system of record.
* Do not add TODO placeholders instead of meaningful design content.
