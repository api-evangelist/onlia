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

## Review

See [review.yml](review.yml) for the full API Evangelist review, including every probed URL with its HTTP status.
