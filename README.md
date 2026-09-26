# Week 8 group-specific Datasette Lite databases

These databases are a browser-friendly alternative to loading the complete 848 MB `airline.db` into Datasette Lite.

- **Student launch page:** https://killiobe.github.io/AirlinesDB/
- **GitHub repository:** https://github.com/killiobe/AirlinesDB

Each group database contains:

- Detailed 2015 flight rows for the group's assigned airline.
- All 14 airline lookup records and all 322 airport lookup records.
- `vw_flight_costs`, using the common course-scenario assumptions.
- `vw_flights_labeled`, which adds airport names, cities, and states.
- `airline_benchmark`: full-year metrics for all 14 airlines.
- `airline_monthly_benchmark`: monthly metrics for all 14 airlines.
- `airline_origin_benchmark`: origin-airport metrics for all 14 airlines.
- `airline_route_benchmark`: route metrics for all 14 airlines.
- `package_info`: scope, definitions, and assumptions for the specific file.

The raw `flights` table intentionally omits tail number and actual clock-event fields. It retains the fields needed for the stated project dimensions: date, day of week, scheduled time, airline, flight number, route, distance, operational duration, departure/arrival delay, cancellation/diversion, and delay causes.

## Group assignments

| Group | Code | Airline |
|---:|---|---|
| 1 | WN | Southwest Airlines |
| 2 | OO | SkyWest Airlines |
| 3 | EV | Atlantic Southeast Airlines |
| 4 | DL | Delta Air Lines |
| 5 | AA | American Airlines |
| 6 | UA | United Airlines |
| 7 | B6 | JetBlue Airways |
| 8 | AS | Alaska Airlines |

## Important analytical distinction

The `flights`, `vw_flight_costs`, and `vw_flights_labeled` objects contain only the assigned airline's detailed records. Tables whose names end in `_benchmark` contain summarized results for all 14 airlines and support fair competitor comparisons.

The benchmark tables are evidence sources, not required analysis checklists. Students should select comparisons that support their management decision.

## Hosting requirement

Datasette Lite loads SQLite files by URL. The host must return `Access-Control-Allow-Origin: *`. GitHub Pages does this automatically.

The published `index.html` is available at https://killiobe.github.io/AirlinesDB/. Its buttons construct the appropriate Datasette Lite URL automatically.

See `manifest.csv` for file sizes, row counts, integrity checks, and SHA-256 hashes. The instructor's course-material workspace retains the reproducible database build script and complete source database.
