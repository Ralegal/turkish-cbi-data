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

> Ra Legal (2026). *Turkish Citizenship by Investment: Open Data*, version 1.1.0.
> https://ralegal.com.tr/data/turkish-cbi-open-data

BibTeX:

```bibtex
@dataset{ralegal_turkish_cbi_data_2026,
  title     = {Turkish Citizenship by Investment: Open Data},
  author    = {{Ra Legal}},
  year      = {2026},
  version   = {1.1.0},
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

| Name | Role | Bar |
|---|---|---|
| Av. Rüzgar Sevimli | Founding Partner | Istanbul Bar Association |
| Av. Merve Elik | Attorney | Istanbul Bar Association |

<!--
TODO: add the Istanbul Bar Association registration (sicil) numbers for
Av. Rüzgar Sevimli and Av. Merve Elik once confirmed with the Bar. Do not
publish a number that has not been confirmed. The Bar's own records are the
reference: https://www.istanbulbarosu.org.tr
-->

Working languages: English and Turkish.

Practice areas relevant to this data: Turkish citizenship by investment;
immigration, residence and work permits; real estate; banking and finance;
corporate; litigation.

**Address**
Ra Legal, Cumhuriyet Mahallesi, İncirli Dede Caddesi No: 4/3705, Şişli,
Istanbul, Türkiye

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
