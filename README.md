# Shippit (shippit)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Shippit is an Australian multi-carrier shipping and fulfillment platform for retailers and e-commerce merchants across Australia, New Zealand, and Southeast Asia. Its REST API (v3) lets merchants request live carrier quotes, create and cancel orders, book consignments with carriers, retrieve A6 shipping labels and pick slips, and track parcels via pull requests or push webhooks.

## Access Model (Honest Up Front)

- **Merchant account required.** The API operates on the authenticated merchant's own shipments; there is no open/self-serve public data API.
- **Authentication:** a per-merchant **API key** (called the "API Secret" in Shippit's docs) passed as an HTTP **Bearer token** — `Authorization: Bearer YOUR_API_KEY`. No HMAC request signing is documented. Shippit also recommends sending `user-agent` and `x-shippit-platform` headers.
- **Environments:** a **staging sandbox** at `https://app.staging.shippit.com/api/3` and **production** at `https://app.shippit.com/api/3`. Use a staging key against staging and a production key against production.
- **Fidelity note:** the base URLs, Bearer auth, and the pull tracking path (`GET /orders/{tracking_number}/tracking`) are grounded in Shippit's published developer docs. Other endpoint request/response **schemas in the OpenAPI are modeled** from Shippit's endpoint descriptions and should be reconciled against the live Developer Centre before generating client code.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/shippit/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/shippit/refs/heads/main/apis.yml)

## Tags

- Shipping
- Logistics
- Fulfillment
- Australia
- APAC
- Multi-Carrier
- Labels
- Tracking
- Parcels
- E-commerce Logistics
- SaaS

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Shippit Quote API

Request live shipping quotes from the carriers configured on a merchant account. Given a delivery location and one or more parcel attributes, returns priced service options (courier, service level, and price) to present at checkout.

- **Human URL:** [https://developer.shippit.com/](https://developer.shippit.com/)
- **Base URL:** `https://app.shippit.com/api/3`

#### Tags

- Quotes
- Rates
- Multi-Carrier

#### Properties

- [Documentation](https://developer.shippit.com/)
- [API Reference](https://developer.shippit.com/dev_guide/using_apis/using_apis.html)
- [OpenAPI](openapi/shippit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/shippit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/shippit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Shippit Orders API

Create, retrieve, update, and cancel shipping orders. Submitting an order with delivery, user, and parcel details lets Shippit generate the order, allocate a courier, and fill the origin from merchant configuration.

- **Human URL:** [https://developer.shippit.com/dev_guide/create_order/order_flow.html](https://developer.shippit.com/dev_guide/create_order/order_flow.html)
- **Base URL:** `https://app.shippit.com/api/3`

#### Tags

- Orders
- Consignments
- Fulfillment

#### Properties

- [Documentation](https://developer.shippit.com/dev_guide/create_order/order_flow.html)
- [API Reference](https://developer.shippit.com/dev_guide/order_types/order_types.html)
- [OpenAPI](openapi/shippit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/shippit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/shippit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Shippit Book API

Initiate a booking with the respective carriers for one or more orders. Given an array of orders, this triggers the consignment booking with each order's allocated courier so labels and manifests can be produced.

- **Human URL:** [https://developer.shippit.com/dev_guide/create_order/order_flow.html](https://developer.shippit.com/dev_guide/create_order/order_flow.html)
- **Base URL:** `https://app.shippit.com/api/3`

#### Tags

- Booking
- Carriers
- Manifest

#### Properties

- [Documentation](https://developer.shippit.com/dev_guide/create_order/order_flow.html)
- [OpenAPI](openapi/shippit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/shippit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/shippit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Shippit Label API

Return a URL to the shipping documents for an order - A6 PDF shipping labels, A4 PDF pick slips, ZPL where required, plus dangerous goods and commercial invoice documentation.

- **Human URL:** [https://developer.shippit.com/dev_guide/using_apis/using_apis.html](https://developer.shippit.com/dev_guide/using_apis/using_apis.html)
- **Base URL:** `https://app.shippit.com/api/3`

#### Tags

- Labels
- Documents
- PDF

#### Properties

- [Documentation](https://developer.shippit.com/dev_guide/using_apis/using_apis.html)
- [OpenAPI](openapi/shippit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/shippit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/shippit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Shippit Tracking API

Track an order's delivery status with a pull-based request against the order's tracking number, or subscribe to push-based webhook updates that Shippit posts to your endpoint as a parcel moves through the carrier network.

- **Human URL:** [https://developer.shippit.com/dev_guide/tracking/tracking_updates.html](https://developer.shippit.com/dev_guide/tracking/tracking_updates.html)
- **Base URL:** `https://app.shippit.com/api/3`

#### Tags

- Tracking
- Webhooks
- Delivery Status

#### Properties

- [Documentation](https://developer.shippit.com/dev_guide/tracking/tracking_updates.html)
- [API Reference](https://developer.shippit.com/api_guide/webhook.html)
- [OpenAPI](openapi/shippit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/shippit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/shippit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Shippit Merchant API

Query and update merchant account settings, including operating hours and webhook subscriptions, so integrations can read and manage account-level configuration programmatically.

- **Human URL:** [https://developer.shippit.com/dev_guide/using_apis/using_apis.html](https://developer.shippit.com/dev_guide/using_apis/using_apis.html)
- **Base URL:** `https://app.shippit.com/api/3`

#### Tags

- Merchant
- Settings
- Configuration

#### Properties

- [Documentation](https://developer.shippit.com/dev_guide/using_apis/using_apis.html)
- [API Reference](https://developer.shippit.com/api_guide/webhook.html)
- [OpenAPI](openapi/shippit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/shippit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/shippit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/shippit-domain-security.yml)
- [Authentication](authentication/shippit-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/shippit)
- [Website](https://www.shippit.com)
- [Documentation](https://developer.shippit.com/)
- [Plans](plans/shippit-plans-pricing.yml)
- [Rate Limits](rate-limits/shippit-rate-limits.yml)
- [Fin Ops](finops/shippit-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
