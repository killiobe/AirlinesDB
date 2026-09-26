# Instructor hosting guide

## Current deployment

- Student launch page: https://killiobe.github.io/AirlinesDB/
- Repository: https://github.com/killiobe/AirlinesDB
- GitHub Pages source: `main`, repository root
- Eighth airline: Alaska Airlines (`AS`)

The site and all eight databases were published September 25, 2026. The live database response was checked for a successful HTTP response, the required cross-origin header, the expected file size, and the SQLite file signature.

## Static-host workflow used

1. The folder contents were committed to the `AirlinesDB` repository using Git on the command line. GitHub's browser uploader is not suitable for these database sizes.
2. Every database file was kept below GitHub's enforced 100 MiB per-file limit.
3. GitHub Pages was enabled from the repository root on the `main` branch.
4. Post only the student launch-page URL in the LMS.

The generated `manifest.csv` records size, expected row count, integrity status, and SHA-256 for each database. Re-run `../build_group_lite_databases.py` whenever the full source database changes.

## Suggested spot checks before release

- Confirm that each database opens from the published site.
- Confirm that `package_info` shows the correct group and airline.
- Run one query against `flights` and one against `airline_benchmark`.
- Confirm the raw table contains only the assigned airline.
- Confirm the benchmark table lists 14 airlines.
- Test from both Chrome and Safari/Edge if those browsers are common in the class.

## Bandwidth note

Every browser downloads its assigned database. GitHub Pages has a soft monthly bandwidth limit, so this approach is intended for a class-sized audience rather than an unrestricted public data portal.
