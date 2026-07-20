# Beyond Bank Australia (beyond-bank)

Beyond Bank Australia Limited (ABN 15 087 651 143, AFSL/Australian Credit Licence 237856) is one of the country's largest customer-owned (mutual) banks, owned by its members rather than shareholders, and the first bank in Australia to become a certified B Corp. It serves roughly 280,000 members from around 56 branches across South Australia, Victoria, the ACT, Western Australia, and New South Wales, with more than nine billion dollars in funds under management. As an Authorised Deposit-taking Institution (ADI) it participates in Australia's Consumer Data Right (CDR / Open Banking), exposing a public, unauthenticated Product Reference Data (PRD) API built to the Data Standards Body (DSB) Consumer Data Standards.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/beyond-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/beyond-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Australia
- Customer Owned
- Product Reference Data

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Beyond Bank Australia CDR Product Reference Data API

Public, unauthenticated Consumer Data Right (CDR) Product Reference Data API exposing Beyond Bank's banking product catalogue. `GET /banking/products` returns a paginated list of products and `GET /banking/products/{productId}` returns full product detail (rates, fees, features, eligibility, constraints). Confirmed live returning HTTP 200 with a `data.products` array and an `x-v` response header of 5 (49 products at time of review). Built to the DSB Consumer Data Standards; no API key or authorization is required for product reference data.

- **Human URL:** [https://www.beyondbank.com.au/open-banking/product-api.html](https://www.beyondbank.com.au/open-banking/product-api.html)
- **Base URL:** `https://public.cdr.api.beyondbank.com.au/cds-au/v1/banking/products`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Australia

#### Properties

- [Documentation](https://www.beyondbank.com.au/open-banking/product-api.html)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [OpenAPI](openapi/beyond-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.beyondbank.com.au/)
- [Documentation](https://www.beyondbank.com.au/open-banking/)
- [Blog](https://www.beyondbank.com.au/blog/)
- [LinkedIn](https://www.linkedin.com/company/beyond-bank-australia)
- [Privacy Policy](https://www.beyondbank.com.au/privacy/)
- [Terms of Service](https://www.beyondbank.com.au/terms-of-use/)
- [Support](https://www.beyondbank.com.au/help-and-contact/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
