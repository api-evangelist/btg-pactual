---
generated: '2026-10-18'
method: generated
name: manage-payment-splitters
description: Look up, update and remove splitter configurations that divide received payments between parties.
api: openapi/btg-pactual-banking-split-openapi.yml
operations:
- listSplitters
- findSplitterByTaxId
- findSplitterById
- updateSplitter
- findSplitById
- deleteSplitter
source: Grounded in openapi/btg-pactual-banking-split-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# Manage payment splitters

Look up, update and remove splitter configurations that divide received payments between parties.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-banking-split-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `listSplitters` — List the company splitters.
2. `findSplitterByTaxId` — Find a splitter by the beneficiary tax id.
3. `findSplitterById` — Read one splitter.
4. `updateSplitter` — Update the splitter.
5. `findSplitById` — Inspect a resulting split.
6. `deleteSplitter` — Delete a splitter.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
