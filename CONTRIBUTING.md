# Contributing

This dataset is maintained, not dumped. Corrections are welcome, and a
correction that names its primary source will be applied quickly.

## What makes a correction easy to act on

Every figure in this repository is traceable to an entry in
[`data/sources.json`](data/sources.json). A correction is easiest to verify when
it is framed the same way:

1. **The file and field you are correcting.** For example
   `data/investment-thresholds.json`, `current[0].minimum`.
2. **The value you believe is right.**
3. **The primary source.** For a legal change, the instrument and its Resmî
   Gazete date and issue number, or a link to the consolidated text on
   [mevzuat.gov.tr](https://www.mevzuat.gov.tr). For a statistic, the publishing
   body, the bulletin and its release date. For a circular that is not published
   in the Resmî Gazete, its number and date.
4. **The date the source speaks as of.** Figures here carry an `asOf` field
   because thresholds and statistics both move.

A link to a news article or a blog post is still useful, but it will be recorded
as a secondary source and flagged for confirmation until the primary text is
located. The `verification` field in `data/sources.json` says which standing a
given citation currently has.

## Things we will not merge

- Figures without a source.
- Interpolated or estimated values presented as published ones. Where a figure
  is not published, this repository says so rather than filling the gap. See the
  `notKnown` list in `data/statistics.json`.
- Promotional material of any kind, including links added for marketing.
- Attorney or agency fees. The cost dataset deliberately covers government and
  third-party transaction costs only.

## Reporting a figure that is in circulation but wrong

If a number is widely repeated and we have excluded it, it will usually appear
in the `figuresInCirculationNotUsed` list in `data/statistics.json` with the
reason. If you think an exclusion is wrong, say which published figures the
number should be reconciled against.

## How to open a correction

Open an issue at
<https://github.com/Ralegal/turkish-cbi-data/issues>, or a pull request if you
can edit the JSON directly. Keep JSON files valid; every file in `data/` is
expected to parse:

```sh
for f in data/*.json; do python3 -c "import json,sys; json.load(open(sys.argv[1]))" "$f" || echo "INVALID: $f"; done
```

Please keep the existing field names. Identifiers in `data/sources.json` are
stable once published and are referenced from the datasets.

## Scope, and a note on legal advice

This repository is reference data: what the instruments say, what the
authorities have published, and what has not been published. It is not legal
advice, and the issue tracker is not a channel for advice on an individual
matter. Questions about a specific file or transaction cannot be answered here.

## Licence

Contributions are accepted under the repository licence, Creative Commons
Attribution 4.0 International (CC BY 4.0). By opening a pull request you confirm
you are able to contribute the material on those terms.
