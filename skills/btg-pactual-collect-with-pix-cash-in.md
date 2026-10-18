---
generated: '2026-10-18'
method: generated
name: collect-with-pix-cash-in
description: Create a Pix location and an instant collection (cobrança imediata) for a company, then list collections to reconcile.
api: openapi/btg-pactual-banking-pixcashin-openapi.yml
operations:
- CreateLocation
- CreateInstantCollection
- GetInstantCollections
- GetLocations
- UnlinkLocation
source: Grounded in openapi/btg-pactual-banking-pixcashin-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# Collect with Pix cash-in

Create a Pix location and an instant collection (cobrança imediata) for a company, then list collections to reconcile.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-banking-pixcashin-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `CreateLocation` — Create a Pix location (payload location) for the company.
2. `CreateInstantCollection` — Create the instant collection to be paid by the payer.
3. `GetInstantCollections` — List instant collections to reconcile payments.
4. `GetLocations` — List locations; UnlinkLocation removes one no longer needed.
5. `UnlinkLocation` — Unlink a location.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
