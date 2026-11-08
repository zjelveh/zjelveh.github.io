# Codebook: Chicago Community Area Socioeconomic Data, 2020–2024

**File:** `chicago_community_area_ses_2020_2024.csv` · 77 rows · 18 columns

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/zjelveh/zjelveh.github.io/refs/heads/master/files/ccjs418e_fall2026/chicago_community_area_ses_2020_2024.csv'
ses = pd.read_csv(filepath_or_buffer=url)
```

**Unit:** one row per Chicago community area, numbered 1–77 as in the City of Chicago's official community area list.

**Source:** Chicago Metropolitan Agency for Planning (CMAP), [Community Data Snapshots](https://www.cmap.illinois.gov/data/community-snapshots), 2026 release, community area table. Downloaded November 8, 2026.

**Period:** American Community Survey 2020–2024 five-year estimates. Each value describes the five years combined.

## Columns

| Column | Meaning |
|---|---|
| `community_area` | Community area number, 1–77 |
| `community_area_name` | Community area name |
| `population` | Total population |
| `households` | Total households |
| `median_household_income` | Median household income, in dollars |
| `per_capita_income` | Income per person, in dollars |
| `households_income_under_25k` | Households with income under $25,000 |
| `pct_households_income_under_25k` | Percentage of households with income under $25,000 |
| `labor_force` | Residents 16 and older who are working or looking for work |
| `unemployed` | Residents in the labor force without a job |
| `unemployment_rate` | Percentage of the labor force that is unemployed |
| `renter_households` | Households that rent their home |
| `owner_households` | Households that own their home |
| `pct_renter_households` | Percentage of households that rent |
| `median_gross_rent` | Median monthly rent including utilities, in dollars |
| `adults_25_and_over` | Residents 25 and older |
| `adults_without_hs_diploma` | Residents 25 and older without a high school diploma |
| `pct_adults_without_hs_diploma` | Percentage of residents 25 and older without a high school diploma |

## Notes

- The figures are survey estimates with margins of error, largest for community areas with small populations.
- CMAP builds community area totals by adding up census tract and block group estimates. Counts are rounded to whole numbers, and percentages to one decimal place.
- The percentage columns were calculated from the counts in the same row.
