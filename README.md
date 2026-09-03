# New Bedford, MA — CSO discharge analysis

Analysis of verified combined sewer overflow (CSO) discharge events for New
Bedford, MA, from the [MassDEP CSO Data
Portal](https://www.mass.gov/info-details/combined-sewer-overflow-cso-notifications)
("Verified Data Report" events — measured volume, duration, and rainfall).

## What's here

| File | What it is |
|---|---|
| `new_bedford_cso_analysis.ipynb` | The analysis: discharge volume over time by outfall, totals by outfall / month / water body, individual Summer 2025 events, and volume-vs-rainfall regressions per water body. |
| `new_bedford_cso_discharges.csv` | Raw pull from the MassDEP portal. |
| `new_bedford_cso_discharges_verified.csv` | Filtered to verified events; the notebook reads this one. Its `rainfall_in` column is the MassDEP per-event gauge reading (two physically impossible rows are dropped in-notebook with `rainfall_in <= 20`). |
| `data/newbedford_daily_precip.csv` | Vendored gridded/gauge daily precipitation at New Bedford (`time, imerg_in, aorc_in, gauge_in`), for comparison against the CSO-report rainfall. |

## Precipitation data

Precipitation products are developed in a separate repo,
[`rsignell/buzzards-bay-precip`](https://github.com/rsignell/buzzards-bay-precip)
(NASA IMERG, NOAA AORC, HRRR forecast, and CoCoRaHS over the Buzzards Bay
watershed). This repo *consumes* those outputs: `data/newbedford_daily_precip.csv`
is a hand-refreshed copy of that repo's `precip_comparison_daily.csv`
(produced by its `compare_precip.py`). Re-copy it when the upstream product
is updated.
