# MyShipTracking (myshiptracking)

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

MyShipTracking is a real-time terrestrial AIS vessel-tracking platform. Its REST API delivers live vessel positions, voyage and static particulars, vessels within a geographic zone or near a reference ship, historical tracks, port details, port calls, estimated arrivals, and fleet management - all returned in a standardized JSON or XML envelope.

## Access Model (Read First)

This is a **paid, credit-metered API**. There is no free-forever tier - only a limited free trial.

- **Authentication is required on every call.** Register at MyShipTracking.com, generate an API Key and Secret Key on your account page, and pass the key as either `Authorization: Bearer YOUR_API_KEY` or the `x-api-key` header.
- **Credit-based billing.** Every successful call deducts credits based on the endpoint and response detail. Simple responses cost 1 credit; extended responses cost 3 credits; history and port-call queries cost 5 credits per distinct date. No credits are charged when a request returns no results.
- **Per-request cap.** You are never charged more than 500 credits for a single request, and never more than your available balance (overuse protection).
- **Two account models.** A pay-per-use "Coin Charge" model, or a monthly "Subscription" with a fixed monthly credit allowance. Subscription credits do not roll over month to month.
- **Free trial.** One trial API key per user, limited to 2,000 coins and a maximum active period of 10 days, capped at 90 calls per minute.
- **Terrestrial AIS only.** Coverage is nearshore; vessels can be out of range for extended periods and historical tracks may be incomplete. Verify coverage against your use case during the trial.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/myshiptracking/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/myshiptracking/refs/heads/main/apis.yml)

## Tags

- Vessel Tracking
- AIS
- Maritime
- Ship Tracking
- Real-Time Data
- Ships
- Port Calls
- Maritime Data
- Location
- Fleet Tracking

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### MyShipTracking Vessel Position API

Retrieve the latest AIS position and voyage details for a specific vessel by MMSI or IMO (`GET /vessel`), or for many vessels in one request (`GET /vessel/bulk`). Simple responses return position, course, speed, and navigation status; extended responses add static particulars and voyage data.

- **Human URL:** [https://api.myshiptracking.com/docs/vessel-current-position-api](https://api.myshiptracking.com/docs/vessel-current-position-api)
- **Base URL:** `https://api.myshiptracking.com/api/v2`

#### Tags

- Vessel Position
- AIS
- Real-Time Data

#### Properties

- [Documentation](https://api.myshiptracking.com/docs/vessel-current-position-api)
- [API Reference](https://api.myshiptracking.com/docs/vessels-current-position-api)
- [OpenAPI](openapi/myshiptracking-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myshiptracking.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myshiptracking.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyShipTracking Vessels in Area API

List vessels inside a geographic bounding box (`GET /vessel/zone` with minlon/maxlon/minlat/maxlat) or within a nautical-mile radius of a reference vessel (`GET /vessel/nearby`). Credits are charged per vessel returned, one for simple and three for extended responses.

- **Human URL:** [https://api.myshiptracking.com/docs/vessels-in-zone](https://api.myshiptracking.com/docs/vessels-in-zone)
- **Base URL:** `https://api.myshiptracking.com/api/v2`

#### Tags

- Vessels In Zone
- Bounding Box
- Nearby

#### Properties

- [Documentation](https://api.myshiptracking.com/docs/vessels-in-zone)
- [API Reference](https://api.myshiptracking.com/docs/vessels-nearby)
- [OpenAPI](openapi/myshiptracking-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myshiptracking.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myshiptracking.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyShipTracking Vessel Search API

Search for vessels by name (`GET /vessel/search`, minimum three characters, up to 40 records). Returns vessel name, MMSI, IMO, type code and label, flag, and last-detected area. One credit per request.

- **Human URL:** [https://api.myshiptracking.com/docs/vessel-search](https://api.myshiptracking.com/docs/vessel-search)
- **Base URL:** `https://api.myshiptracking.com/api/v2`

#### Tags

- Vessel Search
- Lookup
- Ships

#### Properties

- [Documentation](https://api.myshiptracking.com/docs/vessel-search)
- [OpenAPI](openapi/myshiptracking-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myshiptracking.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myshiptracking.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyShipTracking Vessel Particulars API

Static vessel particulars - callsign, vessel type, AIS type, dimensions, draught, flag, gross tonnage, deadweight, and year built - are returned by the extended response of the Vessel Status endpoint. Historical movement is available via `GET /vessel/track` over a date range with configurable time grouping.

- **Human URL:** [https://api.myshiptracking.com/docs/vessel-current-position-api](https://api.myshiptracking.com/docs/vessel-current-position-api)
- **Base URL:** `https://api.myshiptracking.com/api/v2`

#### Tags

- Vessel Particulars
- Static Data
- History Track

#### Properties

- [Documentation](https://api.myshiptracking.com/docs/vessel-current-position-api)
- [API Reference](https://api.myshiptracking.com/docs/vessel-historical-track-api)
- [OpenAPI](openapi/myshiptracking-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myshiptracking.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myshiptracking.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyShipTracking Port Calls API

Retrieve historical port call events - arrivals and departures - for a port (by port_id or UN/LOCODE) or a vessel (by MMSI) over a lookback window or date range (`GET /port/calls`). Port metadata is available via `GET /port`. Charged five credits per distinct date in the returned records.

- **Human URL:** [https://api.myshiptracking.com/docs/port-calls](https://api.myshiptracking.com/docs/port-calls)
- **Base URL:** `https://api.myshiptracking.com/api/v2`

#### Tags

- Port Calls
- Arrivals
- Departures

#### Properties

- [Documentation](https://api.myshiptracking.com/docs/port-calls)
- [API Reference](https://api.myshiptracking.com/docs/port-details)
- [OpenAPI](openapi/myshiptracking-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myshiptracking.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myshiptracking.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### MyShipTracking ETA API

Obtain estimated arrival times for vessels heading to a given port (`GET /port/estimate` by port_id or UN/LOCODE). Each record includes vessel identity and particulars plus `eta_utc` and `eta_local`. One credit per record returned.

- **Human URL:** [https://api.myshiptracking.com/docs/port-estimate-arrivals](https://api.myshiptracking.com/docs/port-estimate-arrivals)
- **Base URL:** `https://api.myshiptracking.com/api/v2`

#### Tags

- ETA
- Expected Arrivals
- Port Estimate

#### Properties

- [Documentation](https://api.myshiptracking.com/docs/port-estimate-arrivals)
- [OpenAPI](openapi/myshiptracking-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/myshiptracking.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/myshiptracking.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/myshiptracking-domain-security.yml)
- [Authentication](authentication/myshiptracking-authentication.yml)
- [Website](https://www.myshiptracking.com)
- [Documentation](https://api.myshiptracking.com/)
- [Plans](plans/myshiptracking-plans-pricing.yml)
- [Rate Limits](rate-limits/myshiptracking-rate-limits.yml)
- [Fin Ops](finops/myshiptracking-finops.yml)
- [LinkedIn](https://www.linkedin.com/company/myshiptracking)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
