# Instructor hosting guide

## Recommended static-host workflow

1. Create a GitHub repository for the Week 8 database launcher.
2. Add the contents of this folder using Git on the command line. GitHub's browser uploader is not suitable for these database sizes.
3. Keep every database file below GitHub's enforced 100 MiB per-file limit.
4. Enable GitHub Pages for the repository and publish from the repository root.
5. Open the published `index.html` page and test all eight buttons in a private browser window.
6. Post only the launch-page URL in the LMS.

The generated `manifest.csv` records size, expected row count, integrity status, and SHA-256 for each database. Re-run `../build_group_lite_databases.py` whenever the full source database changes.

## Suggested verification before release

- Confirm that each database opens from the published site.
- Confirm that `package_info` shows the correct group and airline.
- Run one query against `flights` and one against `airline_benchmark`.
- Confirm the raw table contains only the assigned airline.
- Confirm the benchmark table lists 14 airlines.
- Test from both Chrome and Safari/Edge if those browsers are common in the class.

## Bandwidth note

Every browser downloads its assigned database. GitHub Pages has a soft monthly bandwidth limit, so this approach is intended for a class-sized audience rather than an unrestricted public data portal.
