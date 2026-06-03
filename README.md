# solaroperator.org marketing site

Static site for Solar Operator. Deployed to Netlify.

## Files
- `index.html` — landing page
- `signup.html` — redirects to onboarding wizard
- `welcome.html` — post-purchase welcome page (legacy)
- `account.html` — legacy account portal (superseded by the /accounts SPA)
- `privacy.html` — privacy policy
- `_redirects` — Netlify redirect/proxy rules

## Proxies (`_redirects`)
The two product SPAs live in the solar-operator API repo and are served by
FastAPI on Railway. Netlify status-200 proxies give them clean URLs on the
marketing domain (address bar stays on solaroperator.org):

- `solaroperator.org/onboarding` → Railway `/onboarding/*` (signup wizard)
- `solaroperator.org/accounts`   → Railway `/app/*` (customer dashboard)
- `solaroperator.org/v1/*`       → Railway `/v1/*` (API the SPAs call)

The SPAs fetch the API with relative `/v1/...` paths, so the `/v1` proxy is
required for them to function from the marketing domain.

## Onboarding flow
"Get started" → `https://solaroperator.org/onboarding/`
