---
name: Look up Beyond Bank banking products (CDR PRD)
description: >-
  Browse Beyond Bank Australia's publicly offered banking products and fetch full
  product detail (rates, fees, features, eligibility) via the public, unauthenticated
  CDR Product Reference Data API. No API key or OAuth required.
api: openapi/beyond-bank-cds-banking-products-openapi.yml
operations:
  - listBankingProducts
  - getBankingProductDetail
generated: '2026-07-20'
method: generated
---

# Look up Beyond Bank banking products

Beyond Bank Australia exposes a public, **unauthenticated** Consumer Data Right (CDR)
Product Reference Data (PRD) API. Use it to list the products the bank currently
offers and to read full detail for any one product. There is no sign-up, API key, or
OAuth — the two operations below are open.

Base URL: `https://public.cdr.api.beyondbank.com.au/cds-au/v1`

## Required headers

- `x-v` — **required** on every request. It selects the endpoint major version.
  - `listBankingProducts` currently serves `x-v: 5`
  - `getBankingProductDetail` currently serves `x-v: 7`
  - An unsupported `x-v` returns **HTTP 406 UnsupportedVersion**; the supported version
    is advertised on the `x-v` response header — read it and retry.
- `x-min-v` — optional; lowest major version you will accept.

## Steps

1. **List products** — call `listBankingProducts`
   (`GET /banking/products`) with header `x-v: 5`.
   - Optional filters: `product-category`, `effective` (`CURRENT`/`FUTURE`/`ALL`),
     `updated-since` (RFC 3339), `brand`.
   - Paginate with `page` (1-based) and `page-size` (default 25). Follow
     `links.next` until absent; `meta.totalRecords` / `meta.totalPages` give totals.
   - Each item in `data.products[]` carries a `productId`.

2. **Get product detail** — call `getBankingProductDetail`
   (`GET /banking/products/{productId}`) with header `x-v: 7`, passing a `productId`
   from step 1.
   - The response includes `bundles`, `features`, `constraints`, `eligibility`,
     `fees`, `depositRates`, `lendingRates`, and `instalments`.
   - An unknown `productId` returns **HTTP 404 Invalid Banking Product** — only use
     ids returned by `listBankingProducts`.

## Error handling

Errors use the CDS **ErrorV2** envelope (not RFC 9457): a top-level `errors[]` array
whose members have `code` (a `urn:au-cds:error:v2:*` URN), `title`, `detail`, `meta`.
See `errors/beyond-bank-problem-types.yml`. Common codes: `Header/Missing` and
`Header/InvalidVersion` (400), `Header/UnsupportedVersion` (406),
`Resource/Invalid` (404), and `Field/*` for bad query parameters.

## Scope note

Only these two Product Reference Data operations are public. Any account, balance,
transaction, payee, or scheduled-payment data requires CDR consumer consent through an
**accredited Data Recipient** under the OAuth2/OIDC FAPI profile (PAR + mTLS) — that is
not part of this skill and cannot be reached with an unauthenticated call.
