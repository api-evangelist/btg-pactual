---
generated: '2026-10-18'
method: generated
name: anticipate-card-receivables
description: 'For sub-acquirers (subcredenciadoras): read a merchant''s credit-card receivables, get an anticipation quote, then request the anticipation.'
api: openapi/btg-pactual-antecred-subcredenciadores-openapi.yml
operations:
- getCreditCardReceivablesCedente
- getReceivablesQuote
- createReceivablesAnticipation
source: Grounded in openapi/btg-pactual-antecred-subcredenciadores-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# Anticipate card receivables

For sub-acquirers (subcredenciadoras): read a merchant's credit-card receivables, get an anticipation quote, then request the anticipation.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-antecred-subcredenciadores-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `getCreditCardReceivablesCedente` — Read the cedente's credit-card receivables.
2. `getReceivablesQuote` — Request an anticipation quote (cotação).
3. `createReceivablesAnticipation` — Confirm the anticipation.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
