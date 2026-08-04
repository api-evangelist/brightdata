# Bright Data (brightdata)

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

Bright Data is a web data platform providing a global proxy network (residential, datacenter, ISP, mobile), pre-built Web Scraper APIs for 100+ sites, a SERP API, the Web Unlocker, ready-made Datasets, and a Scraping Browser (Browser API) that exposes a real Chrome DevTools Protocol endpoint over WebSocket for Puppeteer, Playwright, and Selenium automation.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/brightdata/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/brightdata/refs/heads/main/apis.yml)

## Access Model (Honest Summary)

- **Two transports.** Bright Data has a **REST platform API** under `https://api.brightdata.com` (Web Scraper, SERP, Web Unlocker, Zone management, Datasets, Browser API session metadata) **and** a real **WebSocket API** — the Scraping Browser's Chrome DevTools Protocol (CDP) endpoint at `wss://brd.superproxy.io:9222`. The WebSocket surface is genuine and documented; it is modeled in [`asyncapi/brightdata-asyncapi.yml`](asyncapi/brightdata-asyncapi.yml).
- **Authentication is split.** REST calls use a **Bearer API token** (`Authorization: Bearer <API_KEY>`). Proxy zones and the Scraping Browser use **zone credentials** (`brd-customer-<CUSTOMER_ID>-zone-<ZONE>` + zone password) — for the Scraping Browser these are embedded in the `wss://` URL userinfo.
- **Grounded vs. modeled.** All paths, methods, hosts, the CDP `wss://` endpoint, custom CDP command names, and the auth model are grounded in Bright Data's live docs and skills references. Request/response **field schemas** in the OpenAPI file (snapshot record shapes, zone objects, trigger/progress responses) are **representative and flagged as modeled**, not exhaustively reconciled. Pricing and rate limits are **not reconciled** (`reconciled: false`).
- **Billing is per product, usage-based.** Proxies and the Scraping Browser are billed by bandwidth (per GB); Web Unlocker and SERP per 1,000 requests; Web Scraper per record. There is no single all-inclusive subscription.

## Tags

- Web Data
- Web Scraping
- Web Intelligence
- Proxy
- Data Extraction
- SERP
- Web Unlocker
- Datasets
- Data Collection
- Browser Automation

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Bright Data Web Scraper API

Pre-built scrapers for 100+ popular websites (Amazon, LinkedIn, Instagram, TikTok, and more). Trigger an asynchronous collection with `POST /datasets/v3/trigger`, poll `/datasets/v3/progress/{snapshot_id}`, and retrieve results from `/datasets/v3/snapshot/{snapshot_id}`; a synchronous `/datasets/v3/scrape` endpoint is also documented.

- **Human URL:** [https://docs.brightdata.com/api-reference/rest-api/scraper/asynchronous-requests](https://docs.brightdata.com/api-reference/rest-api/scraper/asynchronous-requests)
- **Base URL:** `https://api.brightdata.com`

#### Properties

- [Documentation](https://docs.brightdata.com/scraping-automation/web-scraper-api/overview)
- [API Reference](https://docs.brightdata.com/api-reference/rest-api/scraper/asynchronous-requests)
- [OpenAPI](openapi/brightdata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/brightdata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/brightdata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bright Data SERP API

Structured search-engine results (Google, Bing, and others) via a single `POST /request` call carrying a SERP zone, target search URL, and the desired response format (raw HTML or parsed JSON).

- **Human URL:** [https://docs.brightdata.com/api-reference/rest-api/serp/serp-api](https://docs.brightdata.com/api-reference/rest-api/serp/serp-api)
- **Base URL:** `https://api.brightdata.com`

#### Properties

- [Documentation](https://docs.brightdata.com/scraping-automation/serp-api/overview)
- [API Reference](https://docs.brightdata.com/api-reference/rest-api/serp/serp-api)
- [OpenAPI](openapi/brightdata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/brightdata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/brightdata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bright Data Web Unlocker API

Fetches a single hard-to-reach page via `POST /request` with an unlocker zone, handling proxy rotation, CAPTCHA solving, and JavaScript rendering; supports raw, JSON, markdown, and screenshot response formats and an optional async mode.

- **Human URL:** [https://docs.brightdata.com/api-reference/rest-api/unlocker/unlock-website](https://docs.brightdata.com/api-reference/rest-api/unlocker/unlock-website)
- **Base URL:** `https://api.brightdata.com`

#### Properties

- [Documentation](https://docs.brightdata.com/scraping-automation/web-unlocker/introduction)
- [API Reference](https://docs.brightdata.com/api-reference/rest-api/unlocker/unlock-website)
- [OpenAPI](openapi/brightdata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/brightdata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/brightdata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bright Data Proxy & Zone Management API

Account-management API for provisioning proxy products — add a zone (`POST /zone`), read zone configuration and status (`GET /zone`), and manage static datacenter/ISP IPs. Proxy traffic itself is routed through the superproxy gateway (`brd.superproxy.io`).

- **Human URL:** [https://docs.brightdata.com/api-reference/account-management-api/Add_a_Zone](https://docs.brightdata.com/api-reference/account-management-api/Add_a_Zone)
- **Base URL:** `https://api.brightdata.com`

#### Properties

- [Documentation](https://docs.brightdata.com/api-reference/account-management-api/introduction)
- [API Reference](https://docs.brightdata.com/api-reference/account-management-api/Add_a_Zone)
- [OpenAPI](openapi/brightdata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/brightdata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/brightdata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bright Data Datasets API

Marketplace dataset access — list available datasets, search or filter a dataset, read dataset metadata, and deliver a snapshot to external storage or a webhook.

- **Human URL:** [https://docs.brightdata.com/api-reference/marketplace-dataset-api/get-dataset-list](https://docs.brightdata.com/api-reference/marketplace-dataset-api/get-dataset-list)
- **Base URL:** `https://api.brightdata.com`

#### Properties

- [Documentation](https://docs.brightdata.com/datasets/marketplace-datasets/overview)
- [API Reference](https://docs.brightdata.com/api-reference/marketplace-dataset-api/get-dataset-list)
- [OpenAPI](openapi/brightdata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/brightdata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/brightdata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bright Data Browser API (Scraping Browser)

A cloud headless-browser fleet with built-in unblocking that speaks the Chrome DevTools Protocol (CDP) over a real WebSocket endpoint — `wss://brd.superproxy.io:9222` — for Puppeteer, Playwright, and Selenium, plus Bright Data custom CDP commands (`Captcha.solve`, `Browser.getSessionId`, `Proxy.useSession`). Session metadata is read over REST at `/browser_sessions/{session_id}`.

- **Human URL:** [https://docs.brightdata.com/scraping-automation/scraping-browser/overview](https://docs.brightdata.com/scraping-automation/scraping-browser/overview)
- **Base URL:** `https://api.brightdata.com`

#### Properties

- [Documentation](https://docs.brightdata.com/scraping-automation/scraping-browser/overview)
- [API Reference](https://docs.brightdata.com/scraping-automation/scraping-browser/cdp-functions/standard)
- [AsyncAPI](asyncapi/brightdata-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [OpenAPI](openapi/brightdata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Domain Security](security/brightdata-domain-security.yml)
- [Authentication](authentication/brightdata-authentication.yml)
- [GitHub Organization](https://github.com/brightdata)
- [LinkedIn](https://www.linkedin.com/company/bright-data)
- [Website](https://brightdata.com/)
- [Documentation](https://docs.brightdata.com)
- [Plans](plans/brightdata-plans-pricing.yml)
- [Rate Limits](rate-limits/brightdata-rate-limits.yml)
- [Fin Ops](finops/brightdata-finops.yml)
- [Blog](https://brightdata.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
