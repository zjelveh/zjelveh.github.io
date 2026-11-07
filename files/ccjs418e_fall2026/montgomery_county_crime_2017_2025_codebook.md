# Codebook: Montgomery County, Maryland, Crime Records, 2017–2025

**File:** `montgomery_county_crime_2017_2025.csv` · 447,988 rows · 14 columns · 70 MB

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/zjelveh/zjelveh.github.io/refs/heads/master/files/ccjs418e_fall2026/montgomery_county_crime_2017_2025.csv'
moco = pd.read_csv(filepath_or_buffer=url)
```

## About the Data

**One row represents one offense within a reported incident.** An incident with two offenses, such as a burglary and a theft, has two rows with the same `incident_id`. The file holds 411,867 incidents; 381,677 of them have one offense.

| Year | Rows | Year | Rows | Year | Rows |
|---|---|---|---|---|---|
| 2017 | 56,356 | 2020 | 45,376 | 2023 | 47,840 |
| 2018 | 54,468 | 2021 | 44,922 | 2024 | 50,167 |
| 2019 | 52,665 | 2022 | 48,814 | 2025 | 47,380 |

- **Source:** Montgomery County dataMontgomery portal, [Crime](https://data.montgomerycountymd.gov/Public-Safety/Crime/icn6-v9z3). Downloaded November 6, 2026.
- **What the county includes:** founded crimes reported after July 1, 2016, classified under the FBI's National Incident-Based Reporting System (NIBRS). Records come from the county police and from the Rockville, Gaithersburg, and Takoma Park police departments. No names or other personal information are released.
- **The county's caution:** records rest on preliminary information from the people who reported them. Classifications can change after investigation, and the records can include attempted crimes.

## How This File Was Prepared

- Selected offenses whose start date falls between January 1, 2017, and December 31, 2025.
- Kept 14 of the portal's 30 columns. Removed:
  - `offence_code`, `nibrs_code`, and `police_district_number`: codes that match `offense`, `offense_type`, and `district` one to one.
  - `case_number`: the police report number, one per incident, like `incident_id`.
  - `date` (dispatch time; blank for 9% of rows) and `end_date` (blank for 56%).
  - `location` (block-level address) and its five address-part columns, `state`, `pra` (the patrol area inside a beat), `latitude`, `longitude`, and `geolocation`.
- Renamed `crimename1` to `crime_against`, `crimename2` to `offense_type`, and `crimename3` to `offense`, and shortened the `crime_against` values: `Crime Against Property` became `Property`.
- Added `year`, taken from `start_date`.
- Wrote `0` in the 1,302 blank `zip_code` cells.
- Sorted rows by `start_date`.

## Columns

| Column | Type | Meaning | Example |
|---|---|---|---|
| `incident_id` | number | Incident number, shared by every offense in the same incident | `201115214` |
| `year` | number | Year of `start_date`, 2017–2025 | `2017` |
| `start_date` | text (date and time) | When the offense began; filled in for every row | `2017-01-01 00:00:00` |
| `crime_against` | text | Broad NIBRS group: `Property`, `Society`, `Person`, or `Not a Crime` | `Property` |
| `offense_type` | text | NIBRS offense category (54 categories) | `Theft of Motor Vehicle Parts or Accessories` |
| `offense` | text | Detailed county offense (355 offenses) | `LARCENY - AUTO PARTS` |
| `victims` | number | Number of victims of this offense | `1` |
| `place` | text | Type of place (100 types) | `Residence -Townhouse/Duplex` |
| `agency` | text | Reporting agency (table below) | `MCPD` |
| `district` | text | Police district name (table below); blank for 1,419 rows | `GERMANTOWN` |
| `sector` | text | Police sector, a letter for an area inside a district | `N` |
| `beat` | text | Police beat inside a sector: district number, sector letter, beat number | `5N1` |
| `city` | text | City in the mailing address; blank for 37 rows | `GERMANTOWN` |
| `zip_code` | number | Zip code; `0` means unknown | `20874` |

`start_date` loads as text. Convert it with `pd.to_datetime()` before extracting the month, weekday, or hour.

## Groups and Codes

**`crime_against`**

| Value | Rows | Most common `offense_type` values |
|---|---|---|
| `Property` | 218,952 | Theft From Motor Vehicle, Shoplifting, Destruction/Damage/Vandalism of Property |
| `Society` | 176,436 | All Other Offenses, Drug/Narcotic Violations, Driving Under the Influence |
| `Person` | 47,286 | Simple Assault, Aggravated Assault, Forcible Rape |
| `Not a Crime` | 5,314 | Runaway (5,299 rows), Justifiable Homicide |

**`district`**

| District | Number | Sectors | Rows |
|---|---|---|---|
| `ROCKVILLE` | 1 | A, B | 60,687 |
| `BETHESDA` | 2 | D, E | 64,190 |
| `SILVER SPRING` | 3 | G, H, I | 93,899 |
| `WHEATON` | 4 | J, K, L | 82,991 |
| `GERMANTOWN` | 5 | M, N | 56,462 |
| `MONTGOMERY VILLAGE` | 6 | P, R | 75,007 |
| `TAKOMA PARK` | Takoma Park police | T | 13,319 |
| `OTHER` | | | 14 |
| blank | | | 1,419 |

**`agency`**

| Code | Agency | Rows |
|---|---|---|
| `MCPD` | Montgomery County Police Department | 383,609 |
| `RCPD` | Rockville City Police Department | 25,081 |
| `GPD` | Gaithersburg Police Department | 24,835 |
| `TPPD` | Takoma Park Police Department | 13,244 |
| `MCFM` | Montgomery County Fire Marshal | 1,083 |
| `MCSO` | Montgomery County Sheriff's Office | 129 |
| `OTHR`, `P` | Other | 7 |

## Things to Know

- **Rows count offenses.** To count incidents, count unique incident numbers: `moco['incident_id'].nunique()`.
- **`All Other Offenses` holds police service calls.** It is the largest `offense_type` (106,272 rows). Its most common `offense` values are `POLICE INFORMATION`, `MENTAL ILLNESS - EMERGENCY PETITION`, `LOST PROPERTY`, `SUDDEN DEATH`, and `MISSING PERSON`. Check the `offense` column to decide which records belong in your question.
- **`start_date` marks when the offense began.** An offense discovered later, such as a fraud, can start weeks or months before anyone reports it; among offenses with a dispatch time in the portal, 3.7% were dispatched more than 30 days after their start date.
- **Rounded times.** 4.4% of offenses start at exactly midnight. Many of these record an unknown time, which matters for questions about the hour of day.
- **Mailing cities.** `city` comes from the mailing address, so it covers different areas from the police districts: 155,789 rows list `SILVER SPRING` as the city, and 93,899 fall in the Silver Spring police district. A few rows name places outside the county.
- **Zip codes.** Six rows hold incomplete zip codes, such as `2902`.
