# Civvix — Tennessee 95-County ROI Model

A single self-contained HTML page that models the return a Tennessee county
would see from tangible personal property (TPP) and business license
compliance discovery. Open `index.html` in any browser — no server, no build
step, no dependencies, no network calls.

**Live:** https://civvix.github.io/Civvix-ROI-Calc/

---

## What it does

Pick any of Tennessee's 95 counties. The model pulls that county's real
per-return TPP figures and audited collection rate, applies your assumptions
about lead volume and quality, and reports the county's year-one return
against Civvix's fee.

Every input is encoded in the URL, so **"Copy shareable link" produces a link
that reopens the exact scenario** — useful for sending a specific set of
assumptions to a colleague or a county.

## Where the data comes from

| Figure | Source |
|---|---|
| TPP schedule counts per county | Tennessee Comptroller, response to a Public Records Act request, "Schedules Filed Per County" (86 of 95 counties) |
| TPP assessed values | State Board of Equalization, *Tax Aggregate Report*, Table I, 2023–2025 |
| County tax rates | UT County Technical Assistance Service, County Profile System |
| Audited collection rates | County annual financial reports published by the Comptroller's Division of Local Government Audit — the allowance-for-uncollectible note in each county's audited statements (83 of 95 counties; statewide median of 98.78% for the rest) |
| County boundaries | US Atlas TopoJSON, projected to Albers and inlined as SVG |

`tn_counties_dataset.csv` contains everything the page has baked in, so
any figure on screen can be traced back to a row.

## Known gaps

Nine counties — Chester, Davidson, Hamilton, Hickman, Knox, Montgomery,
Rutherford, Shelby and Williamson — are absent from the Comptroller's
return-count production and together hold **49.1%** of the state's TPP
assessed value. Their per-return figures default to the 86-county state
average and are labelled as estimates throughout, including on the map.

Four fields are flagged red on the page as user-supplied and are placeholders
until real figures are loaded: active business licenses, active businesses in
the county, average new business formations per month, and average business
age from Secretary of State registration dates.

The "Data that would sharpen this model" panel near the bottom lists the ten
outstanding items in priority order.

## Statutory constants

| Constant | Authority |
|---|---|
| 30% assessment ratio on commercial/industrial TPP | Tenn. Code Ann. § 67-5-901(a)(2) |
| Forced assessment on failure to file a schedule | § 67-5-903(c) |
| Back-assessment reach capped at 3 years | § 67-1-1005(a) |
| $15 county business license fee | § 67-4-723 |
| Certification floors of $2,000 / $10,000 | § 67-5-903(b), as amended by 2023 Pub. Ch. 341 |

## On the fee

The Civvix fee is a fixed $10 per record delivered, billed once. That is a
deliberate design constraint rather than a pricing decision: **Tenn. Code Ann.
§ 67-5-507(c)(2) voids any contract in which compensation is "conditioned upon
or measured directly or indirectly by an increase or a reduction in
assessments."** No output of this model feeds any fee, and the page is a
proposal aid, not a payment formula.

## Updating the published page

1. In this repository, click **Add file → Upload files**
2. Drop in the new `index.html` (same filename replaces the old one)
3. **Commit changes**
4. GitHub Pages rebuilds in about a minute

## Disclaimer

Not legal or tax advice. Outputs are illustrative projections built from
user-supplied assumptions, not guaranteed results.
