# Onlia (onlia)

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
