# HyperVerge (hyperverge)

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
