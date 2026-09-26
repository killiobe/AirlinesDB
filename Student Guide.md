# Week 8 Datasette Lite student guide

1. Open the [course Datasette Lite launch page](https://killiobe.github.io/AirlinesDB/).
2. Select your group and wait while the database downloads and Datasette starts.
3. Open the group database, then use **SQL** to enter a read-only query.
4. Save every final query in your supporting-calculations submission. A browser URL is convenient but is not a substitute for submitting the SQL text.

## Which data should I use?

- Use `flights` for detailed analysis of your assigned airline.
- Use `vw_flight_costs` for the course-scenario passenger-impact calculations.
- Use `vw_flights_labeled` when airport names, cities, or states make the result easier to interpret.
- Use the four `_benchmark` tables for comparisons with other airlines.
- Read `package_info` before beginning so that the scope and assumptions are clear.

## Definitions that still apply

- On time means `ARRIVAL_DELAY < 15` minutes.
- Exclude cancelled and diverted flights from on-time and average-arrival-delay denominators.
- Show flight volume behind important rates and averages.
- Scenario-dollar fields are estimates, not airline accounting costs, revenue, profit, actual passenger counts, or legally required compensation.
- The data describes 2015 operations and must not be presented as current performance.

## Query timeout

Datasette normally limits a SQL query to one second. Start with the benchmark tables when possible. If a valid detailed query times out, add `_timelimit=10000` to the query-result URL to allow up to ten seconds, or simplify the query before trying again.

## Example: assigned-airline monthly analysis

```sql
SELECT
    MONTH,
    COUNT(*) AS scheduled_flights,
    AVG(
        CASE
            WHEN CANCELLED = 0 AND DIVERTED = 0
            THEN CASE WHEN ARRIVAL_DELAY < 15 THEN 1.0 ELSE 0.0 END
        END
    ) AS on_time_rate,
    AVG(
        CASE
            WHEN CANCELLED = 0 AND DIVERTED = 0
            THEN ARRIVAL_DELAY
        END
    ) AS avg_arrival_delay_min,
    AVG(CANCELLED * 1.0) AS cancellation_rate
FROM flights
GROUP BY MONTH
ORDER BY MONTH;
```

## Example: compare annual airline benchmarks

```sql
SELECT
    AIRLINE,
    scheduled_flights,
    on_time_rate,
    avg_arrival_delay_min,
    cancellation_rate
FROM airline_benchmark
ORDER BY on_time_rate DESC;
```
