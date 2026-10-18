---
generated: '2026-10-18'
method: generated
name: protest-a-bill
description: Schedule a protest (protesto) for an unpaid bill, singly or in batch, track it, fetch its document, or cancel it.
api: openapi/btg-pactual-banking-protest-openapi.yml
operations:
- createProtestSchedule
- createProtestScheduleBatch
- findProtest
- getProtestDocument
- cancelProtest
- cancelProtestBatch
source: Grounded in openapi/btg-pactual-banking-protest-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# Schedule and manage a bill protest

Schedule a protest (protesto) for an unpaid bill, singly or in batch, track it, fetch its document, or cancel it.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-banking-protest-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `createProtestSchedule` — Schedule a single protest.
2. `createProtestScheduleBatch` — Or schedule protests in batch.
3. `findProtest` — Track a protest by id.
4. `getProtestDocument` — Download the protest document.
5. `cancelProtest` — Cancel a single protest.
6. `cancelProtestBatch` — Cancel protests in batch.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
