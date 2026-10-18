---
generated: '2026-10-18'
method: generated
name: fidc-loan-portability
description: Create a FIDC loan portability request and confirm or cancel it.
api: openapi/btg-pactual-fidc-portability-openapi.yml
operations:
- createPortability
- confirmPortability
- cancelPortability
source: Grounded in openapi/btg-pactual-fidc-portability-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# FIDC loan portability

Create a FIDC loan portability request and confirm or cancel it.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-fidc-portability-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `createPortability` — Create the portability request; keep portabilityId.
2. `confirmPortability` — Confirm the portability.
3. `cancelPortability` — Or cancel it.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
