# EnergySavers (energysavers.shmor.ai)

A Shmor marketplace (shared rules in `../../CLAUDE.md`): its own brand, design and SEO. Compare UK gas, electricity and water suppliers, tariffs and price cap changes, with money-saving guides, grants and the latest energy news. Repo: `Shmorai/shmor-energysavers` (private until launch). Status: **building**. Replaced the planned "energy" (solar/heat pumps) card; those topics are covered by `solar-panels` and `heat-pumps`.

## Where things are
| What | Where |
|---|---|
| Card on shmor.ai, search keywords, **referral links**, offers, SEO defaults | `shmor-site.json` |
| Pages (1 JSON file = 1 Google landing page) | `content/` (`home.json` = homepage) |
| Design: header, logo, footer, **price cap ticker** | `templates/layout.html` |
| Design: styles | `assets/site.css` (kit defaults, then the EnergySavers theme block at the bottom) |
| Generated output (don't edit by hand) | `index.html`, `*/index.html`, `sitemap.xml`, `robots.txt`, `404.html`, `search/` |

## Pages (22)
Home · energy-price-cap · energy-suppliers (supplier cards with filter tabs) · energy-tariffs (tariff cards with filter tabs) · compare-energy-deals · switch-energy-supplier · water-bills (table of every water company) · energy-grants · energy-saving-tips · energy-bill-changes (key dates, Budget, laws) · smart-meters-and-ev-tariffs · solar-panels · heat-pumps · blog + 8 posts (october-2026-price-cap, electricity-vat-cut-explained, autumn-budget-2026-energy, eon-ovo-takeover, should-you-fix-energy-winter-2026, warm-home-discount-2026-27, water-bills-2026-reform, landlords-epc-c-2030).
Top menu (navOrder): Price cap, Suppliers, Tariffs, Deals, Water, Grants & help, Save energy, What’s changing, News. Pages link to each other heavily and to official sources (Ofgem, GOV.UK, HMRC, CCW, Citizens Advice); supplier and water company cards link to their own websites (`rel="nofollow noopener"`).

## Design
"Live grid": mint-white pages #F5FAF7, deep grid-green #062A23 / #0B3F33 hero, bands and footer with rounded bottom corners, electric-mint #2EE59D buttons with dark text (hover #12B97A, soft #E2FAF0), amber #FFC531 lightning-bolt details (eyebrows, list bullets, highlight icons, big figures, CTA watermark, ticker tag), links #047857. Space Grotesk 700 headings + Inter body. Logo = grid-green rounded square with a mint bolt and amber spark dot + "Energy**Savers**" (Savers in mint). Favicon = same mark. A price cap ticker sits above the sticky header.
Helpers inside `html`: tables in `<div class="table-wrap">`; tips `<p class="callout">`; big numbers `<div class="figure-row"><div class="figure"><b>£1,723</b><span>label</span></div></div>`; source lines `<p class="source-note">`. Checked at 375px (no horizontal scroll).
**Photos:** free-licence Unsplash images, credited, in each page's "image".

## Quarterly update (each Ofgem announcement: late Feb, May, Aug, Nov)
Update the cap figures in `templates/layout.html` (ticker), `content/energy-price-cap.json` (figures, table, history, forecast), `content/home.json` (first section) and `content/energy-bill-changes.json`, then add a news post. Source: Ofgem's price cap pages. Also update after the Autumn Budget (28 Oct 2026) and before 31 Mar 2027 (end of 0% VAT on electricity), and when the E.ON–OVO deal completes.

## Content rules for this site
Official figures only, each with a source link. No invented prices, deals, savings amounts, supplier ratings or reviews (point to Citizens Advice's supplier ranking instead). Forecasts are labelled as forecasts and attributed (e.g. Cornwall Insight). No live tariff prices (they change daily): deal pages explain how to compare and will show partner links once added. Pre-Budget reports are written as speculation until confirmed. Not financial advice (footer disclaimer).
Facts used (checked 15 Oct 2026): cap 1 Oct–31 Dec 2026 £1,723 (+4%), electricity 26.32p/kWh + 54.83p/day, gas 7.97p/kWh + 29.68p/day; Jul–Sep 2026 £1,663 (26.11p, 57.19p, 7.33p, 29.04p); Apr–Jun 2026 £1,641 (−7%); 0% VAT on GB household electricity 1 Oct 2026–31 Mar 2027 (not NI), gas stays 5%, ~£45/yr saving (gov estimate); Autumn Budget 28 Oct 2026; Cornwall Insight 23 Sep forecast ~£1,872 for Jan–Mar 2027; E.ON buying OVO, competition clearance early Oct 2026, completion pending; Ofgem lower standing charge pilot from Apr 2026 (EDF, E.ON, Octopus, British Gas); WHD £150 for winter 2026/27; Winter Fuel Payment £100–£300, born on/before 27 Jun 1960, clawback over £35k; BUS £7,500, £9,000 for oil/LPG homes 21 Jul 2026–31 Mar 2027; rental EPC C by 1 Oct 2030, £10k cost cap; Ofwat to be abolished (announced Jul 2025), water white paper Jan 2026; Water UK April 2026 forecast avg +£33 (5.4%) to ~£639.

## Commands (run here)
```bash
node tools/build.js           # rebuild after ANY change to content/, templates/ or shmor-site.json
node tools/serve.js <port>    # local preview (see the "energysavers" preview config)
```
After changing `shmor-site.json`, also run `node tools/sync-network.js` in `../../shmor-ai`.

## Referral links
None yet. Candidates: Ofgem-accredited price comparison sites and suppliers with affiliate programmes (Awin/CJ/Impact), solar and heat pump installer lead partners, smart thermostat and insulation retailers. Paste exact links from the user only.
Add to `shmor-site.json` → `"links"`, list slugs in a page's `"partners"` (compare-energy-deals already has the title "Compare live energy deals") or add `"offers"`, rebuild, sync the master, then commit both repos.
