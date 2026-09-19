# borecky-agency-reporting

GOAL onboarding and website/SEO reports for **The Borecky Agency** (Patrick Borecky — Little Rock, AR).

Deployed as a static site on Vercel.

## Contents

| Path | Report |
| --- | --- |
| `index.html` | Landing page: one card per report in two sections, "Campaign Reporting" and "Website & SEO" |
| `reports/campaign-overview.html` | Campaign Overview: setup at a glance, campaigns, geography, lead delivery (Sept 18, 2026) |
| `reports/home-campaign.html` | Home Campaign: shopper targeting, geography, budget (Sept 18, 2026) |
| `reports/auto-home-bundle-campaign.html` | Auto-Home Bundle Campaign: shopper targeting, geography (Sept 18, 2026) |
| `reports/seo-keyword-research-2026-09.html` | Keyword Research & On-Page SEO: on-page metrics and page-by-page checks for the 7 current pages, the 6 on-page recommendations, 99 recommended keywords in 13 clusters, a 10-page sitemap with titles, H1s and meta descriptions, the full filterable keyword list with the autocomplete seeds each phrase was seen for, and the items to confirm before copy is written (Sept 18–19, 2026) |
| `reports/seo-audit-2026-09.html` | Technical SEO Audit: boreckyagency.com key metrics, passing checks, Lighthouse scores and load timings, the 6 technical recommendations (Sept 18, 2026) |

`index.html` is the landing page, with a card for each report grouped into "Campaign
Reporting" (the three campaign reports) and "Website & SEO" (the two SEO reports). Every
report has an "← All Reports" button at the top of its sidebar that links back to it, and
the five reports also link to each other in the sidebar under the same two group labels.
The SEO report was split on Sept 19: the keyword, copy and on-page material is in
`seo-keyword-research-2026-09.html`, and `seo-audit-2026-09.html` keeps the technical
audit, so the original audit link still works. Each one is a single self-contained HTML file: charts are inline and the
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

Put the new HTML file in `reports/` and use a lowercase, hyphenated filename. Then:

1. Add a card for it to the right section's grid in `index.html` ("Campaign Reporting"
   or "Website & SEO"), plus a matching numbered link under the same label in the hub's
   sidebar nav. Update the report count pill in that section's heading.
2. Give the report the "← All Reports" button as the first element of its sidebar:
   `<a class="back" href="../index.html">&larr; All Reports</a>`, with the `.side .back`
   CSS copied from any existing report.
3. Add it under the matching group label ("Campaign reporting" or "Website & SEO") in
   the sidebar nav of every file in `reports/`. Links between reports are plain
   filenames, such as `home-campaign.html`.

## Previewing locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```
