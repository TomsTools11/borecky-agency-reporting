# borecky-agency-reporting

GOAL onboarding and SEO reports for **The Borecky Agency** (Patrick Borecky — Little Rock, AR).

Deployed as a static site on Vercel.

## Contents

| Path | Report |
| --- | --- |
| `index.html` | Campaign Overview: setup at a glance, campaigns, geography, lead delivery (Sept 18, 2026) |
| `reports/home-campaign.html` | Home Campaign: shopper targeting, geography, budget (Sept 18, 2026) |
| `reports/auto-home-bundle-campaign.html` | Auto-Home Bundle Campaign: shopper targeting, geography (Sept 18, 2026) |
| `reports/seo-audit-2026-09.html` | SEO Audit: boreckyagency.com key metrics, page-by-page checks, Lighthouse scores, recommendations (Sept 18, 2026) |

The Campaign Overview is the landing page. All four reports share a sidebar that links
to each other. Each one is a single self-contained HTML file: charts are inline and the
logo is an inline base64 image. The only external request is the Inter webfont from
Google Fonts. There is no build step and there are no dependencies.

## Deploying on Vercel

`vercel.json` serves the repo root as a static site (`framework: null`,
`outputDirectory: "."`, `cleanUrls: true`), so `/reports/home-campaign` works without
the `.html` extension. Every push to `main` publishes to production, and every other
branch or PR gets its own preview URL.

Search engines are blocked with an `X-Robots-Tag: noindex` header and `robots.txt`
because these are client reports.

To connect the repo, import it at [vercel.com/new](https://vercel.com/new) and keep
the defaults. The Framework Preset shows as "Other", and the build and output settings
come from `vercel.json`.

## Adding another report

Put the new HTML file in `reports/` and use a lowercase, hyphenated filename. Then add
it to the sidebar nav in `index.html` and in every file in `reports/`. From the overview
the link is `reports/<name>.html`. From another report it is `<name>.html`, and the link
back to the overview is `../index.html`.

## Previewing locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```
