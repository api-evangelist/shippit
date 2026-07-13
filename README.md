# Shippit (shippit)

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
