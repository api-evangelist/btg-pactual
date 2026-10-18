---
generated: '2026-10-18'
method: generated
name: submit-supply-chain-bordero
description: 'Risco sacado (reverse factoring): register payees, submit a bordero of receivables, then follow receivables, operations and trades.'
api: openapi/btg-pactual-scf-risco-sacado-openapi.yml
operations:
- createCompany
- createBordero
- getReceivablesFromBordero
- cancelReceivablesFromBordero
- getOperationById
- getTrades
- getTradeById
source: Grounded in openapi/btg-pactual-scf-risco-sacado-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# Submit a supply-chain finance bordero

Risco sacado (reverse factoring): register payees, submit a bordero of receivables, then follow receivables, operations and trades.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-scf-risco-sacado-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `createCompany` — Register a payee (supplier) under the payer.
2. `createBordero` — Submit the bordero; keep the trackingId.
3. `getReceivablesFromBordero` — Read the bordero receivables.
4. `cancelReceivablesFromBordero` — Cancel receivables from the bordero if needed.
5. `getOperationById` — Follow the resulting operation.
6. `getTrades` — List trades; getTradeById for one.
7. `getTradeById` — Read a trade.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
