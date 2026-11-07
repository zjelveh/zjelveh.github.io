# Codebook: Chicago Police Department Crime Records, 2019 and 2025

**File:** `chicago_crimes_2019_2025.csv` · 500,148 rows · 14 columns · 54 MB

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/zjelveh/zjelveh.github.io/refs/heads/master/files/ccjs418e_fall2026/chicago_crimes_2019_2025.csv'
chicago = pd.read_csv(filepath_or_buffer=url)
```

## About the Data

**One row represents one reported crime incident.** The file holds every incident dated in 2019 (261,943 rows) or 2025 (238,205 rows).

- **Source:** City of Chicago Data Portal, [Crimes – 2001 to Present](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2), published by the Chicago Police Department. Downloaded November 6, 2026.
- **What the city includes:** reported incidents of crime, drawn from the department's CLEAR records system. Homicides appear once per victim. Addresses are rounded to the block to protect victims' privacy.
- **The city's caution:** classifications come from preliminary information and can change after investigation. The department warns against treating the records as an exact measure of change over time. A comparison of 2019 and 2025 describes recorded incidents, which reflect both crime and reporting.

## How This File Was Prepared

- Selected incidents whose `year` is 2019 or 2025.
- Kept 14 of the portal's 22 columns. Removed: `case_number` (the police report number), `block` (block-level address), `x_coordinate`, `y_coordinate`, `latitude`, `longitude`, `location` (map coordinates), and `updated_on` (when the record was last edited).
- Stored `district`, `beat`, `ward`, and `community_area` as whole numbers. The portal writes district 1 as `001` and beat 111 as `0111`.
- Wrote `0` in the 16 blank `ward` cells and 25 blank `community_area` cells. The portal already uses `0` for an unknown ward or community area.
- Sorted rows by `date`.

## Columns

| Column | Type | Meaning | Example |
|---|---|---|---|
| `id` | number | Unique record number | `11552667` |
| `date` | text (date and time) | When the incident occurred; sometimes a best estimate | `2019-01-01 00:00:00` |
| `year` | number | Year of `date`: 2019 or 2025 | `2019` |
| `iucr` | text | Illinois Uniform Crime Reporting code; one code for each `primary_type` and `description` pair | `0486` |
| `primary_type` | text | Offense category (32 categories) | `BATTERY` |
| `description` | text | Offense subcategory within `primary_type` | `DOMESTIC BATTERY SIMPLE` |
| `fbi_code` | text | FBI offense classification (table below) | `08B` |
| `location_description` | text | Type of place; blank for 2,638 rows | `APARTMENT` |
| `arrest` | True/False | `True` if an arrest was made | `False` |
| `domestic` | True/False | `True` if the incident was domestic-related under the Illinois Domestic Violence Act | `True` |
| `district` | number | Police district (22 districts) | `9` |
| `beat` | number | Police beat, the smallest patrol area (275 beats); the digits before the last two give the district | `922` |
| `ward` | number | City Council ward, 1–50; `0` means unknown | `15` |
| `community_area` | number | Community area, 1–77 (names below); `0` means unknown | `58` |

`date` loads as text. Convert it with `pd.to_datetime()` before extracting the month, weekday, or hour.

## FBI Codes

The Chicago Police Department groups the index codes into violent and property crime. The last column lists the most common `primary_type` values in this file.

| Code | Classification | Index crime | Rows | Most common `primary_type` |
|---|---|---|---|---|
| `01A` | Homicide, first and second degree | Violent | 935 | HOMICIDE |
| `01B` | Involuntary manslaughter | | 15 | HOMICIDE |
| `02` | Criminal sexual assault | Violent | 3,994 | CRIMINAL SEXUAL ASSAULT, CRIM SEXUAL ASSAULT |
| `03` | Robbery | Violent | 13,813 | ROBBERY |
| `04A` | Aggravated assault | Violent | 12,430 | ASSAULT |
| `04B` | Aggravated battery | Violent | 14,995 | BATTERY |
| `05` | Burglary | Property | 15,852 | BURGLARY |
| `06` | Larceny (theft) | Property | 121,239 | THEFT |
| `07` | Motor vehicle theft | Property | 26,240 | MOTOR VEHICLE THEFT |
| `08A` | Simple assault | | 37,353 | ASSAULT, OTHER OFFENSE |
| `08B` | Simple battery | | 78,377 | BATTERY |
| `09` | Arson | Property | 750 | ARSON |
| `10` | Forgery and counterfeiting | | 2,562 | DECEPTIVE PRACTICE |
| `11` | Fraud | | 31,975 | DECEPTIVE PRACTICE |
| `12` | Embezzlement | | 68 | DECEPTIVE PRACTICE |
| `13` | Stolen property | | 108 | DECEPTIVE PRACTICE |
| `14` | Vandalism | | 52,933 | CRIMINAL DAMAGE |
| `15` | Weapons violation | | 12,285 | WEAPONS VIOLATION |
| `16` | Prostitution | | 871 | PROSTITUTION |
| `17` | Criminal sexual abuse | | 3,866 | SEX OFFENSE |
| `18` | Drug abuse | | 22,492 | NARCOTICS |
| `19` | Gambling | | 157 | GAMBLING |
| `20` | Offenses against family | | 1,482 | OFFENSE INVOLVING CHILDREN |
| `22` | Liquor license | | 432 | LIQUOR LAW VIOLATION |
| `24` | Disorderly conduct | | 5,014 | PUBLIC PEACE VIOLATION |
| `26` | Miscellaneous non-index offense | | 39,910 | OTHER OFFENSE, CRIMINAL TRESPASS |

Source of the classifications: [Chicago Police Department crime details](https://gis.chicagopolice.org/pages/crime_details). The full list of IUCR codes is on the [city portal](https://data.cityofchicago.org/d/c7ck-438e).

## Community Areas

| # | Name | # | Name | # | Name | # | Name |
|---|---|---|---|---|---|---|---|
| 1 | Rogers Park | 21 | Avondale | 41 | Hyde Park | 61 | New City |
| 2 | West Ridge | 22 | Logan Square | 42 | Woodlawn | 62 | West Elsdon |
| 3 | Uptown | 23 | Humboldt Park | 43 | South Shore | 63 | Gage Park |
| 4 | Lincoln Square | 24 | West Town | 44 | Chatham | 64 | Clearing |
| 5 | North Center | 25 | Austin | 45 | Avalon Park | 65 | West Lawn |
| 6 | Lake View | 26 | West Garfield Park | 46 | South Chicago | 66 | Chicago Lawn |
| 7 | Lincoln Park | 27 | East Garfield Park | 47 | Burnside | 67 | West Englewood |
| 8 | Near North Side | 28 | Near West Side | 48 | Calumet Heights | 68 | Englewood |
| 9 | Edison Park | 29 | North Lawndale | 49 | Roseland | 69 | Greater Grand Crossing |
| 10 | Norwood Park | 30 | South Lawndale | 50 | Pullman | 70 | Ashburn |
| 11 | Jefferson Park | 31 | Lower West Side | 51 | South Deering | 71 | Auburn Gresham |
| 12 | Forest Glen | 32 | Loop | 52 | East Side | 72 | Beverly |
| 13 | North Park | 33 | Near South Side | 53 | West Pullman | 73 | Washington Heights |
| 14 | Albany Park | 34 | Armour Square | 54 | Riverdale | 74 | Mount Greenwood |
| 15 | Portage Park | 35 | Douglas | 55 | Hegewisch | 75 | Morgan Park |
| 16 | Irving Park | 36 | Oakland | 56 | Garfield Ridge | 76 | O'Hare |
| 17 | Dunning | 37 | Fuller Park | 57 | Archer Heights | 77 | Edgewater |
| 18 | Montclare | 38 | Grand Boulevard | 58 | Brighton Park | | |
| 19 | Belmont Cragin | 39 | Kenwood | 59 | McKinley Park | | |
| 20 | Hermosa | 40 | Washington Park | 60 | Bridgeport | | |

Source: City of Chicago, [Boundaries – Community Areas](https://data.cityofchicago.org/d/igwz-8jzy).

## Things to Know

- **Offense names changed between the years.** Chicago reworded the `description` for 142 IUCR codes, for example `AGGRAVATED: HANDGUN` in 2019 became `AGGRAVATED - HANDGUN` in 2025. The `primary_type` `CRIM SEXUAL ASSAULT` in 2019 became `CRIMINAL SEXUAL ASSAULT`. The `iucr` code stays the same in both years, so use `iucr` or `fbi_code` to match an offense across 2019 and 2025.
- **Wards were redrawn in 2023.** A ward number covers different blocks in 2019 and 2025. Community areas keep the same boundaries in both years, so use them for place comparisons across years.
- **Unknown places.** 530 rows have `0` for `ward` and 539 have `0` for `community_area`, mostly the same rows. Districts 31 (27 rows) and 61 (506 rows) fall outside the 22 standard districts; every district 61 row has beat 6100 and an unknown ward and community area.
- **Rounded times.** 2.6% of incidents are timed at exactly midnight and 2.4% at exactly noon, more than the surrounding minutes. Many of these record an unknown time, which matters for questions about the hour of day.
