# Onlia (onlia)

Onlia is a Canadian digital insurance brokerage, operating as the registered business name of Onlia Agency Inc. and backed by Southampton Financial Inc. It sells personal lines direct to consumers online and by phone — auto (car, motorcycle, ATV, snowmobile, trailer, motorhome), property (home, condo, tenant, landlord, second home, mobile home) and lifestyle lines (boat, pet, life, travel, seasonal) — plus group and bundle programs. Onlia does not underwrite; it places business with a panel of Canadian carriers disclosed on its broker-disclosure page.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/onlia/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/onlia/refs/heads/main/apis.yml)

## Tags

- Insurance
- Canada
- Property and Casualty
- Insurtech
- Broker
- Personal Lines
- Auto Insurance
- Home Insurance
- Direct to Consumer
- Ontario

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

**None.** Onlia publishes no public API.

There is no developer portal, no API reference, and no machine-readable API description of any kind. Every conventional developer host under `onlia.ca` fails to resolve (`developer.`, `developers.`, `docs.`, `api.` — the last has a historical TLS certificate in Certificate Transparency logs but no live host today), and every conventional developer path on the marketing site returns 404 (`/developers`, `/developer`, `/api`, `/integrations`).

The only quote / bind / issue and self-service surface is [app.onlia.ca](https://app.onlia.ca/), a consumer-facing Angular single-page application running on a white-labelled Ignite Insurance policy administration platform. Its backing REST API is private to that app — undocumented, unversioned publicly, and not offered to third parties. Claims are reported by phone and through the [claims page](https://www.onlia.ca/claims); there is no FNOL API.

**What is behind the app (2026-07-25 enrichment round).** The publicly served Angular bundle names the backend Onlia's own app calls: a set of MuleSoft Anypoint Platform (CloudHub) ESB applications in `us-e2` — auto policy management, a home policy router, authentication/registration, documents, VIN and MVR/AutoPlus lookups, Salesforce-backed claims, and a logging sink — plus an Ignite Insurance user-authentication service at `prod-jws.sys.igniteinsurance.ca`. Probed anonymously these hosts publish no machine-readable contract (no OpenAPI/Swagger/RAML at any conventional path; `/console` answers 200 with an empty body). This does not change the verdict: it is first-party plumbing for Onlia's own SPA, with no documentation, no published base URL, no third-party auth model, and no way to get credentials. The capability to expose a partner API clearly exists; the company does not offer one. See `findings.privateBackend` in [review.yml](review.yml).

The one "partner" surface, [/partners](https://www.onlia.ca/partners), is a B2B marketing page inviting affinity and group-discount partnerships by email. It contains no API, SDK, sandbox, or technical onboarding language.

**ACORD posture:** no ACORD reference found. Nothing on the site, the blog, the broker-disclosure page, or the app shell mentions ACORD, AL3, ACORD XML, NGDS, IVANS, agency download, Applied Epic, or Vertafore AMS360. (The word "swagger" appears twice on the About page — as brand copy, "a little swagger" — and is not a reference to the Swagger specification.)

This absence is the finding, and it is the expected one. Canada has no open-insurance mandate, and Consumer-Driven Banking — Canada's open-banking framework — excludes insurance entirely. Nothing compels a personal-lines brokerage to publish an API, and Onlia does not.

## Links

- [Website](https://www.onlia.ca/)
- [About](https://www.onlia.ca/about)
- [Blog](https://www.onlia.ca/magazine/blogs) · [RSS](https://www.onlia.ca/magazine/blogs?format=rss)
- [Support](https://www.onlia.ca/support)
- [Claims](https://www.onlia.ca/claims)
- [Customer Portal](https://app.onlia.ca/)
- [Partners](https://www.onlia.ca/partners)
- [Broker Disclosure](https://www.onlia.ca/broker-disclosure)
- [Privacy Notice](https://www.onlia.ca/about/privacy-notice)

## Artifacts

- [llms/onlia-llms.txt](llms/onlia-llms.txt) — generated llms.txt (Onlia serves none; `/llms.txt` is 404 on both hosts).
- [security/onlia-domain-security.yml](security/onlia-domain-security.yml) — probed TLS/HSTS/DNSSEC/CAA/SPF/DMARC posture. HSTS on `www` (6 months) but not on `app`; no DNSSEC, no CAA, SPF and DMARC present with `p=none`.
- [well-known/onlia-well-known.yml](well-known/onlia-well-known.yml) — recorded negative result: no `/.well-known/` document of any kind is served on `www.onlia.ca` or `app.onlia.ca`.

No `packages/`, `openapi/`, `mcp/`, `skills/`, `scopes/`, `authentication/`, `changelog/`, `sandbox/` or `asyncapi/` artifacts exist, because none of the underlying things exist: no first-party SDK on npm/PyPI/any registry, no spec to ground them in, no event surface, no public auth model. Recording that honestly is the point.

## Review

See [review.yml](review.yml) for the full API Evangelist review, including every probed URL with its HTTP status.
