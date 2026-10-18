---
generated: '2026-10-18'
method: generated
name: run-payroll-batch
description: Onboard employees to BTG Pactual Empresas payroll, submit a payment batch, then track or cancel it.
api: openapi/btg-pactual-banking-payroll-openapi.yml
operations:
- listIssuers
- submitOnboardingEmployees
- listEmployees
- getEmployeeAccount
- submitPaymentBatch
- getPaymentBatch
- cancelPaymentBatch
source: Grounded in openapi/btg-pactual-banking-payroll-openapi.yml (OpenAPI 3.0.3); every operationId verified verbatim in the spec.
---

# Run a payroll payment batch

Onboard employees to BTG Pactual Empresas payroll, submit a payment batch, then track or cancel it.

## Auth
BTG Id OAuth 2.0 access token (see the security schemes declared in openapi/btg-pactual-banking-payroll-openapi.yml and https://developers.empresas.btgpactual.com/docs/intro). Test first in the sandbox: https://developers.empresas.btgpactual.com/entrar/sandbox

## Steps
1. `listIssuers` — List the payroll issuers available to the company.
2. `submitOnboardingEmployees` — Onboard employees onto payroll.
3. `listEmployees` — Confirm employees are registered; use getEmployee / getEmployeeAccount for one.
4. `getEmployeeAccount` — Check the employee account that will receive the payment.
5. `submitPaymentBatch` — Submit the payment batch; keep the returned identifier.
6. `getPaymentBatch` — Poll the batch status.
7. `cancelPaymentBatch` — Cancel the batch by requestId if needed.

## Rules
- Path parameters (companyId, taxId, ids) are required; take them from earlier responses, never guess.
- The spec does not document an idempotency key: do not blindly retry POSTs on timeout; read state first.
- Check https://status.empresas.btgpactual.com/ on persistent 5xx.
