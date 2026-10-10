# Dataset Documentation

## Overview

This project uses a fixed snapshot of Washington State's Electric
Vehicle Population Data.

Each row represents a vehicle record. The dataset contains battery
electric vehicles (BEVs) and plug-in hybrid electric vehicles (PHEVs).

| Item | Value |
|---|---|
| File | `raw/EV_Population_WA_Data.csv` |
| Original records | 200,048 |
| Original columns | 17 |
| Records with a Washington address | 199,606 |
| Records excluded by the state filter | 442 |

## Source

The dataset originates from the Washington State Department of
Licensing's Electric Vehicle Population Data.

The supplied CSV is retained as the project's analysis snapshot.
Its exact extraction date has not been established. Results describe
this file and should not be interpreted as current population totals.

## Main Fields

| Field | Use |
|---|---|
| Make and Model | Manufacturer and model comparisons |
| Model Year | Model-year distribution |
| Electric Vehicle Type | Separate BEV and PHEV comparisons |
| Electric Range | Recorded electric-only range in miles |
| Base MSRP | Recorded manufacturer suggested retail price |
| City and County | Geographic comparisons |
| State | Restrict analysis to Washington addresses |
| DOL Vehicle ID | Check vehicle identifier uniqueness |
| CAFV Eligibility | Context for unresearched range values |

## Data Handling

- The original CSV remains unchanged.
- Analysis includes only records where `State` equals `WA`.
- Missing geographic values are retained without imputation.
- Zero electric ranges correspond to records marked as having
  unresearched battery range.
- `Electric Range Known` contains positive recorded ranges and
  excludes zeros from range statistics.
- Zero MSRP values are treated as unavailable pricing information.
- `Base MSRP Known` contains positive recorded MSRP values.
- No duplicate rows or duplicate vehicle IDs were found in the
  Washington subset.

## Coverage and Limitations

Within the Washington subset:

- 90,413 records have positive electric range information.
- 109,193 records (54.70%) have unresearched range.
- 3,311 records have positive MSRP information.
- 196,295 records (98.34%) have unavailable MSRP.
- Four records have missing vehicle locations.

Known-range and pricing subsets may not represent the full population.
Model year is not registration year, and geographic counts are not
population-adjusted adoption rates.

## Reproducibility

Keep the CSV at its documented path to reproduce the notebook's results.
Using a newer source snapshot may change counts, coverage, and findings.