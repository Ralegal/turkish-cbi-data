# Turkish Citizenship by Investment: Open Data

Machine-readable reference data on Türkiye's citizenship-by-investment
programme: qualifying thresholds and the instrument that set each one, the rules
attached to each route, government transaction costs, the documents an
application requires, and published statistics on acquisitions and foreign
property purchases.

Published and maintained by [Ra Legal](https://ralegal.com.tr), a law firm in
Istanbul. Licensed **CC BY 4.0**: reuse it anywhere, including commercially,
with attribution.

[![Licence: CC BY 4.0](https://img.shields.io/badge/licence-CC%20BY%204.0-blue.svg)](LICENSE)

## Why this exists

The figures that govern this programme are scattered across a statute, a
regulation amended five times, circulars of a general directorate that are never
published in the Resmî Gazete, monthly statistical bulletins, and ministerial
statements reported in the press. No published machine-readable reference for
them existed, and there was no single place recording which figures are published
and which are not.

So the numbers in circulation are often stale, often unsourced, and sometimes
wrong. Two things follow from that, and they shape everything here. Every figure
carries the instrument or publication it comes from and the date it speaks as of.
And where a figure is not published, this repository says so instead of filling
the gap: `data/statistics.json` carries a `notKnown` list of the gaps and a
`figuresInCirculationNotUsed` list of figures that are widely repeated and do not
reconcile with published data.

## At a glance

As of **8 November 2026**, under Law No. 5901 Art. 12(1)(b) and Art. 20 of the
implementing Regulation (BKK 2010/139):

| Route | Minimum | Holding period | Basis of the figure |
|---|---|---|---|
| Real estate | USD 400,000 | 3 years | Official SPK-licensed appraisal value, not the contract price |
| Bank deposit | USD 500,000 | 3 years | Turkish lira deposit in a bank operating in Türkiye, after the foreign currency is sold to the bank and by the bank to the Central Bank (Regulation Art. 20(10), since 6 January 2022) |
| Government bonds | USD 500,000 | 3 years | Certified by the Ministry of Treasury and Finance |
| Investment fund shares | USD 500,000 | 3 years | Real-estate or venture capital fund shares (GYF/GSYF) |
| Fixed capital investment | USD 500,000 | not applicable | Certified by the Ministry of Industry and Technology |
| Job creation | 50 employees | not applicable | Certified by the Ministry of Labour and Social Security |

A single qualifying investment covers the applicant, their spouse and children
under 18. Age is assessed at the application date, not the decision date. There
is no residence requirement, no language test and no interview. Funds must move
through the Turkish banking system, and a currency conversion certificate (döviz
alım belgesi) is mandatory.

## What is the minimum investment for Turkish citizenship?

USD 400,000 by the official appraisal value on the real estate route, or USD
500,000 on the deposit, government bond and investment fund routes, each held for
three years. The table above covers every route;
[`data/investment-thresholds.json`](data/investment-thresholds.json) is the
machine-readable version.

## How have the thresholds changed over time?

| Effective | Route | Minimum | Instrument |
|---|---|---|---|
| 2017-01-12 | Real estate | USD 1,000,000 | BKK 2016/9601, Resmî Gazete 12 January 2017 No. 29946 |
| 2017-01-12 | Bank deposit | USD 3,000,000 | BKK 2016/9601, Resmî Gazete 12 January 2017 No. 29946 |
| 2017-01-12 | Government bonds | USD 3,000,000 | BKK 2016/9601, Resmî Gazete 12 January 2017 No. 29946 |
| 2017-01-12 | Fixed capital investment | USD 2,000,000 | BKK 2016/9601, Resmî Gazete 12 January 2017 No. 29946 |
| 2017-01-12 | Job creation | 100 employees | BKK 2016/9601, Resmî Gazete 12 January 2017 No. 29946 |
| 2018-09-19 | Real estate | USD 250,000 | Presidential Decree 106, Resmî Gazete 19 September 2018 No. 30540 |
| 2018-09-19 | Bank deposit | USD 500,000 | Presidential Decree 106, Resmî Gazete 19 September 2018 No. 30540 |
| 2018-09-19 | Government bonds | USD 500,000 | Presidential Decree 106, Resmî Gazete 19 September 2018 No. 30540 |
| 2018-09-19 | Investment fund shares | USD 500,000 | Presidential Decree 106, Resmî Gazete 19 September 2018 No. 30540 |
| 2018-09-19 | Fixed capital investment | USD 500,000 | Presidential Decree 106, Resmî Gazete 19 September 2018 No. 30540 |
| 2018-09-19 | Job creation | 50 employees | Presidential Decree 106, Resmî Gazete 19 September 2018 No. 30540 |
| 2022-06-13 | Real estate | USD 400,000 | Presidential Decision 5554, Resmî Gazete 13 May 2022 No. 31834, in force 13 June 2022 |

## What does it cost beyond the investment?

[`data/government-costs.csv`](data/government-costs.csv) itemises the government
and third-party costs: title deed transfer tax (20 per thousand on the transferor
and 20 per thousand on the transferee separately under Fees Law No. 492 Tariff
No. 4, so 4% in total), VAT and the foreign-buyer exemption under VAT Law No.
3065 Art. 13(i), the SPK appraisal report, the currency conversion spread,
translations, and per-person application fees. Attorney fees are deliberately
excluded.

## Files

| File | Contents |
|---|---|
| [`data/investment-thresholds.json`](data/investment-thresholds.json) | Current and historical thresholds, route conditions, family rules |
| [`data/government-costs.csv`](data/government-costs.csv) | Government and third-party transaction costs |
| [`data/document-checklist.json`](data/document-checklist.json) | Required documents by family member, plus apostille status by country |
| [`data/statistics.json`](data/statistics.json) | Statistics tracker: 325 long-format observations across 36 series (citizenship acquisitions, investment-route totals, foreign property purchases by nationality and province, threshold and rule changes, 2026 enforcement action). Every record names a source and an as-of date; `value` is `null` and `published` is `false` where the figure is not published. |
| [`data/sources.json`](data/sources.json) | Index of every primary source behind the datasets: statute and regulation names, articles used, Resmî Gazete date and issue number where known, publisher, URL where known, and a verification status per citation |
| [`data/apostille-countries.json`](data/apostille-countries.json) | Hague Apostille Convention status: all 130 Contracting Parties with the date the Convention entered into force for each, by ISO 3166-1 alpha-2 code, plus the non-parties our guides name. Decides whether a civil status document takes an apostille or needs consular legalisation |
| [`data/processing-times.json`](data/processing-times.json) | Observed durations per stage of a file, and the end-to-end range. Marked `"basis": "observed"`, because no Turkish authority publishes an end-to-end processing time and no statute sets a deadline |
| [`data/investment-returns.json`](data/investment-returns.json) | Year-end index levels and rates (BIST 100, BIST REIT, gold in lira, lira and dollar deposit returns, housing) with USD/TRY, for expressing each route's outcome in dollars. Gross of taxes and fees, and not investment advice |

## Headline statistics

| Figure | Value | Source | As of |
|---|---|---|---|
| Citizenship acquisitions, 2025, all routes combined | 48,334 people | NVİ figures released through ministerial statements, reported by DW Türkçe | 2026-08-09 |
| Citizenship acquisitions, 2016 to 2025, cumulative | 562,701 people | NVİ figures, reported by DW Türkçe | 2026-08-09 |
| Investment route since 2018 | 174,567 people, of whom 51,762 principal investors and 122,805 spouses and children | Interior Minister Mustafa Çiftçi, statement of 29 May 2026 | 2026-05-29 |
| Investment attracted since 2018 | USD 16.074 billion | Interior Minister Mustafa Çiftçi, statement of 29 May 2026 | 2026-05-29 |
| Citizenships cancelled or withdrawn, cumulative | 6,134 people, covering 1,413 principal investors (5,391 on fraud grounds under Art. 31, 743 on public order or national security grounds under Art. 40) | Ministry of Interior written statement of 4 August 2026, restated 21 September 2026 | 2026-09-21 |
| Foreign house purchases, 2025 | 21,534 dwellings, 1.3% of all house sales (22,980 on the revised TÜİK series) | TÜİK annual bulletin, read through BMD Araştırma reproductions | 2026-01-22 |
| Foreign house purchases, January to September 2026 | 15,308 dwellings, down 4.3% year on year | TÜİK September 2026 bulletin, released 16 October 2026 | 2026-10-16 |
| Net real-estate acquisition by non-residents, 2025 | USD 2,342 million (provisional) | TCMB balance of payments, line 1.2.3 Gayrimenkul (Net) | 2026-10-31 |
| Real-estate threshold | USD 400,000, in force since 13 June 2022 | Presidential Decision 5554, Resmî Gazete 13 May 2022 No. 31834 | 2026-11-08 |
| Applications, approvals, rejections, backlog, processing time | not published | No official series exists | 2026-11-08 |

Figures are reported as their sources state them. The series are not mutually
substitutable: citizenship acquisitions cover all routes, and TÜİK foreign house
sales cover all foreign buyers, of whom roughly 19% were buying for citizenship
purposes in the first half of 2023 (EVA Gayrimenkul Değerleme analysis). The
`notKnown` and `figuresInCirculationNotUsed` arrays in `statistics.json` list the
gaps and the numbers in circulation that this dataset declines to carry.

## What Türkiye does not publish, and which circulating figures do not reconcile

Most of this dataset restates figures that exist elsewhere. This section does not.
It records the gaps and the disputed numbers, which is the part that cannot be
checked against another source because no other source states it.

**Not published by any Turkish authority:**

- Goc Idaresi Baskanligi publishes no citizenship-acquisition statistics series. Annual figures reach the public through ministerial statements and parliamentary answers.
- Annual citizenship acquisitions for 2018, 2022, 2023 and 2026 are not published. The series is non-monotonic, so it must not be interpolated.
- There is no annual investment-route series, and no published application, approval, rejection or backlog count.
- No Turkish authority publishes an end-to-end processing time for the investor route.
- TUIK 2025 nationality counts for China, Pakistan, Bangladesh, Kazakhstan, Saudi Arabia, Afghanistan and Kuwait are not published.
- No 2026 year-to-date nationality or province breakdown of foreign house sales is published.
- No official average transaction value for foreign property purchases is published by TUIK, TKGM or TCMB.
- The revised TUIK series year mapping for 2013 to 2021 is derived by ratio matching, not read off an official table.
- Appraisal report validity: the Kilavuz of 1 February 2024 states 3 months, post-2026 secondary reporting states 12 months. The sources disagree and the 9 December 2024 Kilavuz could not be read.
- The current status of the closed-neighbourhood regime for residence permits is unresolved. No official announcement lifting or restating the 2022 position was located.
- The legal instrument behind the USD 200,000 residence-permit property threshold of 16 October 2023 could not be identified.
- Overlap between the cumulative 6,134 cancellations and the 687 and 1,070 criminal-file identifications is unquantified.

**Figures in circulation that this dataset does not use, and why:**

- **January 2026 foreign house sales of 1,547** — not used. Inconsistent with five published TUIK cumulatives, which give 1,306.
- **China 41 units for full-year 2025** — not used. Implausible against 110 units in April 2026 alone; not used.
- **About 15,000 investment-route principals and 40,000 people to end-2025** — not used. Undated source with no primary link; contradicts the Interior Minister figures by a factor of about 3.5. Not used.
- **1,757 people in revocation proceedings** — not used. A derived sum of 687 and 1,070 published by a trade outlet, not by any authority, with overlap unclarified. Carried in the data only as a flagged derived record.
- **Automatic 25 per cent uplift on valuations** — not used. No primary text; described as unreliable by practitioners.
- **Real-estate threshold rising to USD 600,000 or USD 500,000** — not used. Never enacted. The consolidated Regulation still reads USD 400,000.

Each of these is a statement by Ra Legal, Istanbul, maintainer of this dataset.
Where a figure is absent the series must not be interpolated; where a circulating
figure is rejected the reason is given so the judgement can be disagreed with.

## Methodology and limits

Figures come from the primary instruments and official publications indexed in
[`data/sources.json`](data/sources.json). Each entry there carries a
`verification` status, so a reader can see which citations have been matched to
an official text and which still rest on secondary reporting, and an
`openQuestions` list records what is still unresolved.

Cost ranges are typical observed values, not quotes, and vary by property,
province and bank. Statistical records are reproduced as published, including
where published sources disagree with each other, in which case the disagreement
is recorded rather than resolved. Nothing here is legal or tax advice. Rules
change: check the `asOf` field in each file, and the Resmî Gazete for amendments.

## How to cite

GitHub renders a **Cite this repository** button from
[`CITATION.cff`](CITATION.cff). In text:

> Sevimli, R. and Ra Legal (2026). *Turkish Citizenship by Investment: Open
> Data*, version 1.2.0. https://ralegal.com.tr/data/turkish-cbi-open-data

BibTeX:

```bibtex
@dataset{ralegal_turkish_cbi_data_2026,
  title     = {Turkish Citizenship by Investment: Open Data},
  author    = {Sevimli, R{\\"u}zgar and {Ra Legal}},
  year      = {2026},
  version   = {1.2.0},
  publisher = {Ra Legal},
  address   = {Istanbul, T\"urkiye},
  license   = {CC-BY-4.0},
  url       = {https://ralegal.com.tr/data/turkish-cbi-open-data}
}
```

If you are citing a single figure, cite that record's own `source` field as well.
That is what the field is for.

## Explanatory guides

The datasets state the figures. The guides on ralegal.com.tr explain the
procedure around them.

- [Turkish citizenship by investment](https://ralegal.com.tr/turkish-citizenship-by-investment) (canonical guide)
- [Citizenship through real estate](https://ralegal.com.tr/insights/turkish-citizenship-by-real-estate)
- [Citizenship through a bank deposit](https://ralegal.com.tr/insights/turkish-citizenship-by-bank-deposit)
- [Total cost of Turkish citizenship](https://ralegal.com.tr/insights/turkish-citizenship-total-cost)
- [Which family members are included](https://ralegal.com.tr/insights/turkish-citizenship-family-members)
- [The children-under-18 rule](https://ralegal.com.tr/insights/turkish-citizenship-children-under-18-rule)
- [Source of funds requirements](https://ralegal.com.tr/source-of-funds-turkey-citizenship)
- [Title deed due diligence](https://ralegal.com.tr/insights/property-due-diligence-tapu)
- [Appealing a citizenship revocation](https://ralegal.com.tr/insights/citizenship-revocation-appeal)
- [How to verify a Turkish lawyer](https://ralegal.com.tr/insights/how-to-verify-a-turkish-lawyer)

Canonical page for the statistics: https://ralegal.com.tr/turkish-cbi-statistics

## Maintainers

This repository is maintained by **Ra Legal**, a law firm in Istanbul, Türkiye.
The attorneys who maintain it are registered with the Istanbul Bar Association
(İstanbul Barosu):

| Name | Role | Bar | Registration |
|---|---|---|---|
| Av. Rüzgar Sevimli | Founding Partner | Istanbul Bar Association | 69519 |

The registration number is published so that anyone relying on this data can
check who stands behind it against the Bar's own roll, rather than against an
assertion made here: https://www.istanbulbarosu.org.tr

Working languages: English, Turkish, Chinese, Arabic and Urdu.

Practice areas relevant to this data: Turkish citizenship by investment;
immigration, residence and work permits; real estate; banking and finance;
corporate; litigation.

**Address**
Ra Legal, Nurol Tower, Kat 21, İzzetpaşa Mahallesi, Yeni Yol Caddesi No: 3,
Şişli, Istanbul, Türkiye

**Contact**
info@ralegal.com.tr  ·  +90 537 734 82 63 (WhatsApp)  ·  https://ralegal.com.tr

Any attorney registered with a Turkish bar can be checked against that bar's own
records, which is the only reliable verification.
[How to verify a Turkish lawyer](https://ralegal.com.tr/insights/how-to-verify-a-turkish-lawyer)
sets out the steps.

## Contributing

Corrections are welcome, especially citations to primary sources. See
[CONTRIBUTING.md](CONTRIBUTING.md) for what makes a correction easy to verify,
then open an issue with the instrument and date you are relying on.

## Licence

Creative Commons Attribution 4.0 International (CC BY 4.0). See
[LICENSE](LICENSE).
