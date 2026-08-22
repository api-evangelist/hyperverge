# HyperVerge (hyperverge)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

HyperVerge is an AI-based identity verification and customer onboarding platform (India-HQ, global) providing document OCR / KYC extraction, face match, passive liveness, government/central database verification, and field matching. Its REST APIs extract and verify Indian identity documents (PAN, Aadhaar, Passport, Voter ID, Driving License), match a selfie against an ID photo, and validate user input against central databases for onboarding, AML, and fraud prevention.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/hyperverge/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/hyperverge/refs/heads/main/apis.yml)

## Access Model (Read First)

HyperVerge's APIs are **enterprise / onboarding-gated**, not self-serve:

- **Authentication:** every request carries an `appId` and `appKey` pair issued by the HyperVerge team after commercial onboarding. On the Face Match host the headers are lowercase `appid` / `appkey`. HyperVerge explicitly warns not to expose these credentials in browser applications. Invalid credentials return HTTP `401`.
- **Region hosts:** the API is region-hosted. India uses `ind-*` hosts; other geographies have their own (for example `apac.faceid.hyperverge.co` for Face Match in APAC). Only the India hosts are cataloged here:
  - `https://ind-docs.hyperverge.co/v2.0` — KYC document OCR / extraction (multipart form-data).
  - `https://ind-verify.hyperverge.co` — database verification, input validation, and matching (JSON).
  - `https://ind-faceid.hyperverge.co` — face match (multipart form-data).
- **Pricing:** quote-based. HyperVerge publishes tiers (Start / Grow / Enterprise) but no public per-verification rate; you request a quote sized to your verification volume. See `plans/` and `finops/`.
- **Liveness:** passive liveness / presentation-attack detection is a core product, but it is delivered through HyperVerge's mobile SDKs and hosted onboarding Workflow rather than a confirmed standalone public REST endpoint — see the note under APIs below.

## Tags

- Identity Verification
- KYC
- Face Authentication
- Liveness
- Document Verification
- India
- AML
- Onboarding
- Fraud Prevention
- AI

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### HyperVerge KYC OCR API

Image/PDF OCR and KYC extraction for Indian identity documents. `readKYC` auto-detects the document type; dedicated endpoints extract PAN, Aadhaar, Passport, and Voter ID fields. Supports quality checks, face presence checks, and cropped image output.

- **Human URL:** [https://documentation.hyperverge.co/](https://documentation.hyperverge.co/)
- **Base URL:** `https://ind-docs.hyperverge.co/v2.0`

#### Tags

- KYC
- OCR
- Document Verification
- India

#### Properties

- [Documentation](https://github.com/hyperverge/kyc-india-rest-api)
- [API Reference](https://github.com/hyperverge/kyc-india-rest-api/blob/master/README.md)
- [OpenAPI](openapi/hyperverge-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperverge.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hyperverge.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### HyperVerge Database Verification API

Central-database (government source) verification for Indian documents — verify a PAN with name and date of birth, fetch the registered name from a PAN, validate a Driving License, check a Voter ID (EPIC), and verify bank account details via IFSC and account number.

- **Human URL:** [https://documentation.hyperverge.co/](https://documentation.hyperverge.co/)
- **Base URL:** `https://ind-verify.hyperverge.co`

#### Tags

- Database Verification
- PAN
- Driving License
- Voter ID
- AML

#### Properties

- [Documentation](https://github.com/hyperverge/db-verification-india-rest-api)
- [API Reference](https://github.com/hyperverge/db-verification-india-rest-api/blob/master/README.md)
- [OpenAPI](openapi/hyperverge-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperverge.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hyperverge.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### HyperVerge Input Validation API

Cross-validates user-entered identity details against OCR (or QR) output for PAN, Aadhaar, Passport, and Voter ID during onboarding, returning per-field match results.

- **Human URL:** [https://documentation.hyperverge.co/](https://documentation.hyperverge.co/)
- **Base URL:** `https://ind-verify.hyperverge.co`

#### Tags

- Validation
- KYC
- Onboarding
- India

#### Properties

- [Documentation](https://github.com/hyperverge/validation-india-rest-api)
- [API Reference](https://github.com/hyperverge/validation-india-rest-api/blob/master/README.md)
- [OpenAPI](openapi/hyperverge-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperverge.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hyperverge.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### HyperVerge Matching API

Compares two values across supported identity fields via `matchFields` — fuzzy matching for name and address, direct matching for fields such as DOB, PAN, Aadhaar, Passport, Voter ID, phone, and gender — returning per-field and overall match flags.

- **Human URL:** [https://documentation.hyperverge.co/](https://documentation.hyperverge.co/)
- **Base URL:** `https://ind-verify.hyperverge.co`

#### Tags

- Matching
- Fuzzy Match
- Onboarding

#### Properties

- [Documentation](https://github.com/hyperverge/matching-india-rest-api)
- [API Reference](https://github.com/hyperverge/matching-india-rest-api/blob/master/README.md)
- [OpenAPI](openapi/hyperverge-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperverge.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hyperverge.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### HyperVerge Face Match API

Determines whether two face images belong to the same person via `POST /v1/photo/verifyPair` — selfie-to-ID or selfie-to-selfie — returning a match score. APAC region is served at `apac.faceid.hyperverge.co`.

- **Human URL:** [https://documentation.hyperverge.co/](https://documentation.hyperverge.co/)
- **Base URL:** `https://ind-faceid.hyperverge.co`

#### Tags

- Face Authentication
- Face Match
- Biometrics

#### Properties

- [Documentation](https://github.com/hyperverge/face-match-india-rest-api)
- [API Reference](https://github.com/hyperverge/face-match-india-rest-api/blob/master/README.md)
- [OpenAPI](openapi/hyperverge-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/hyperverge.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/hyperverge.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### HyperVerge Liveness Detection

Passive liveness / presentation-attack detection from a single selfie, trained on 850M+ liveness checks. Delivered primarily through HyperVerge's mobile SDKs and the hosted onboarding Workflow. A standalone documented public REST endpoint for liveness was **not confirmed** in HyperVerge's published REST-API repositories at review time, so no OpenAPI operation is asserted for it — it is listed here as a documentation link only.

- **Human URL:** [https://hyperverge.co/in/integrations-marketplace/facial-recognition-api/](https://hyperverge.co/in/integrations-marketplace/facial-recognition-api/)
- **Base URL:** `https://ind-faceid.hyperverge.co`

#### Tags

- Liveness
- Face Authentication
- Fraud Prevention

#### Properties

- [Documentation](https://hyperverge.co/in/integrations-marketplace/facial-recognition-api/)

## Common Properties

- [Domain Security](security/hyperverge-domain-security.yml)
- [Authentication](authentication/hyperverge-authentication.yml)
- [GitHub Organization](https://github.com/hyperverge)
- [LinkedIn](https://www.linkedin.com/company/hyperverge)
- [Website](https://hyperverge.co)
- [Documentation](https://documentation.hyperverge.co/)
- [Plans](plans/hyperverge-plans-pricing.yml)
- [Rate Limits](rate-limits/hyperverge-rate-limits.yml)
- [Fin Ops](finops/hyperverge-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
