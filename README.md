<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="docs/readme/banner-dark.svg">
    <img alt="Enacted — District of Columbia. What changed. What’s current. Who to ask." src="docs/readme/banner-light.svg" width="100%">
  </picture>
</p>

<p align="center">
  <img alt="Records: Markdown + YAML" src="docs/readme/badge-records.svg">
  <img alt="Provenance: SHA-256 per source" src="docs/readme/badge-provenance.svg">
  <img alt="Models in pipeline: none" src="docs/readme/badge-models.svg">
  <img alt="Checks: Python 3.12+" src="docs/readme/badge-python.svg">
  <a href="LICENSE-DATA"><img alt="Records licence: CC0 1.0" src="docs/readme/badge-license-data.svg"></a>
  <a href="LICENSE"><img alt="Code: MIT" src="docs/readme/badge-license-code.svg"></a>
</p>

# Enacted: District of Columbia records

This repository records the enacted law. It does not advise, approve, determine, or certify anything.

Nothing here is legal advice, and using it does not create an attorney-client relationship with anyone. The government source cited in each record controls: a record may have been amended, superseded or corrected since it was fetched. If a decision depends on a rule, read the cited source and, where it matters, ask the office named for that jurisdiction or a licensed professional there.

Browse these records on **[enacted.app](https://enacted.app/coverage/?jur=dc/district_of_columbia)**, or follow the District by feed at **[enacted.app/feeds](https://enacted.app/feeds/)**. Both are free.

## What's in it

| Path | What it holds |
| :-- | :-- |
| `district_of_columbia/council_bills/` | Zoning and land-use legislation from the Council of the District of Columbia, one Markdown file per bill |
| `district_of_columbia/authority.yaml` | Who to ask: the Office of the Zoning Administrator's public line, quoted from the District's own contact page, with that page's SHA-256 |
| `water/measurements/dc_water/` | DC Water's published lead and copper tap results, one file per parameter and year |
| `.cache/` | Saved copy of the contact page, so its hash can be recomputed |
| `coverage.json` | The jurisdiction this repository tracks |
| `verify_corpus_integrity.py`, `tests/`, `scripts/` | The checks, and the deterministic tools that fetch records |

## Coverage

| Jurisdiction | Folder | Status |
| :-- | :-- | :-- |
| District of Columbia | [`district_of_columbia/`](district_of_columbia/) | Records |

Records are added and refreshed by deterministic fetch scripts run by hand. Scheduled fetch-and-check workflows are staged in `.github/workflows-pending/` and are not switched on yet, so a change at the source appears here only after the next run.

## How a record is made

- **From the government's own site.** Each record names its source (`primary_source_url`, and `source_pdf` where the instrument is a file), the SHA-256 of the exact file fetched (`source_sha256`) and when it was fetched, in UTC (`source_fetched_at`).
- **Quoted, not summarised.** Quoted text is copied mechanically from that file. Where a title or summary page differs from the enacted text, the enacted text controls and the difference is noted in the record.
- **No commercial code publishers.** Sites such as Municode, American Legal Publishing, eCode360 and enCodePlus are not used. When a jurisdiction's code is published only there, its folder holds a `SOURCING_BLOCKED.md` saying what was checked, and no records.
- **No news or commentary.** Articles and opinion pieces are never cited.
- **No AI models.** Nothing in fetching, building, comparing or sending these records calls a model.

## Checking the records yourself

```bash
pip install pyyaml pytest
python verify_corpus_integrity.py   # re-fetches cited sources, so it needs network access
python -m pytest tests
```

Every hash can also be checked by hand: download the file a record cites (or open the matching page in `.cache/`) and compare its SHA-256 with the record's `source_sha256`.

## Reuse and licences

- **Records: CC0 1.0** ([LICENSE-DATA](LICENSE-DATA)). The record files and their YAML metadata, the contact files, the feeds, `coverage.json` and the documentation are dedicated to the public domain. Use them for anything, with no permission or credit needed. If you do give credit, a link to the cited government source is the most useful kind.
- **Code: MIT** ([LICENSE](LICENSE)). `verify_corpus_integrity.py`, `scripts/`, `tests/` and the workflow files. Keep the copyright notice when you copy them.
- **Not covered by either.** Text quoted from a government document keeps whatever status it has at its source; the dedication covers what Swapp Technologies added (the selection, structure and metadata). The saved pages in `.cache/` belong to their publishers and are kept only so their hashes can be recomputed. The Enacted name, its mark and the images in `docs/readme/` are not licensed.

## Corrections

If you find an error (a wrong date, a broken source link, a quote that doesn't match its source), open an issue on this repository with the record's path and the source you checked. A correction goes through the same checks as every other record.

Enacted can't say whether or how a rule applies to a particular property, project or license. The office listed in that jurisdiction's `authority.yaml` can.

## About

Published by Swapp Technologies LLC (Maryland). The site that presents these records is [enacted.app](https://enacted.app).

Related repositories: [enacted-state-md](https://github.com/Swapp-Technologies-LLC/enacted-state-md) · [enacted-state-va](https://github.com/Swapp-Technologies-LLC/enacted-state-va) · [enacted-federal](https://github.com/Swapp-Technologies-LLC/enacted-federal)
