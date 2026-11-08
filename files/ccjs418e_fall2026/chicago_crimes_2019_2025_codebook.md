# Codebook: Chicago Police Department Crime Records, 2019–2025

**File:** `chicago_crimes_2019_2025.csv` · 1,687,355 rows · 7 columns · 86 MB

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/zjelveh/zjelveh.github.io/refs/heads/master/files/ccjs418e_fall2026/chicago_crimes_2019_2025.csv'
chicago = pd.read_csv(filepath_or_buffer=url)
```

## About the Data

**One row represents one reported crime incident.** The file holds every incident dated from January 1, 2019, through December 31, 2025.

| Year | Rows | Year | Rows |
|---|---|---|---|
| 2019 | 261,944 | 2023 | 263,880 |
| 2020 | 213,089 | 2024 | 259,686 |
| 2021 | 210,028 | 2025 | 238,211 |
| 2022 | 240,517 | | |

- **Source:** City of Chicago Data Portal, [Crimes – 2001 to Present](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2), published by the Chicago Police Department. Downloaded November 8, 2026.
- **What the city includes:** reported incidents of crime, drawn from the department's CLEAR records system. Homicides appear once per victim. Addresses are rounded to the block to protect victims' privacy.
- **The city's caution:** classifications come from preliminary information and can change after investigation. The department warns against treating the records as an exact measure of change over time. A comparison across years describes recorded incidents, which reflect both crime and reporting.

## How This File Was Prepared

- Selected incidents dated 2019 through 2025.
- Kept 7 of the portal's 22 columns so the file stays under GitHub's 100 MB limit for a single file. The portal's other columns include the offense description, type of place, domestic flag, beat, ward, block address, and map coordinates; the full records are on the portal.
- Stored `district` and `community_area` as whole numbers. The portal writes district 1 as `001`.
- Wrote `0` in the blank `community_area` cells. The portal already uses `0` for an unknown community area.
- Sorted rows by `date`.

## Columns

| Column | Type | Meaning | Example |
|---|---|---|---|
| `date` | text (date and time) | When the incident occurred; sometimes a best estimate | `2019-01-01 00:00:00` |
| `iucr` | text | Illinois Uniform Crime Reporting code, the most detailed offense code | `0486` |
| `primary_type` | text | Offense category (33 categories) | `BATTERY` |
| `fbi_code` | text | FBI offense classification (table below) | `08B` |
| `arrest` | True/False | `True` if an arrest was made | `False` |
| `district` | number | Police district (22 districts) | `9` |
| `community_area` | number | Community area, 1–77 (names below); `0` means unknown | `58` |

`date` loads as text. Convert it with `pd.to_datetime()`, then extract the year, month, day of the month, weekday, or hour with `.dt.year`, `.dt.month`, `.dt.day`, `.dt.day_name()`, or `.dt.hour`.

## FBI Codes

The Chicago Police Department groups the index codes into violent and property crime. The last column lists the most common `primary_type` values in this file.

| Code | Classification | Index crime | Rows | Most common `primary_type` |
|---|---|---|---|---|
| `01A` | Homicide, first and second degree | Violent | 4,485 | HOMICIDE |
| `01B` | Involuntary manslaughter | | 48 | HOMICIDE |
| `02` | Criminal sexual assault | Violent | 13,510 | CRIMINAL SEXUAL ASSAULT |
| `03` | Robbery | Violent | 58,746 | ROBBERY |
| `04A` | Aggravated assault | Violent | 48,845 | ASSAULT |
| `04B` | Aggravated battery | Violent | 55,486 | BATTERY |
| `05` | Burglary | Property | 54,020 | BURGLARY |
| `06` | Larceny (theft) | Property | 377,213 | THEFT |
| `07` | Motor vehicle theft | Property | 119,254 | MOTOR VEHICLE THEFT |
| `08A` | Simple assault | | 126,031 | ASSAULT, OTHER OFFENSE |
| `08B` | Simple battery | | 253,860 | BATTERY |
| `09` | Arson | Property | 3,284 | ARSON |
| `10` | Forgery and counterfeiting | | 10,602 | DECEPTIVE PRACTICE |
| `11` | Fraud | | 111,659 | DECEPTIVE PRACTICE |
| `12` | Embezzlement | | 259 | DECEPTIVE PRACTICE |
| `13` | Stolen property | | 396 | DECEPTIVE PRACTICE |
| `14` | Vandalism | | 188,823 | CRIMINAL DAMAGE |
| `15` | Weapons violation | | 55,844 | WEAPONS VIOLATION |
| `16` | Prostitution | | 2,044 | PROSTITUTION |
| `17` | Criminal sexual abuse | | 12,709 | SEX OFFENSE |
| `18` | Drug abuse | | 51,609 | NARCOTICS |
| `19` | Gambling | | 243 | GAMBLING |
| `20` | Offenses against family | | 4,888 | OFFENSE INVOLVING CHILDREN |
| `22` | Liquor license | | 1,345 | LIQUOR LAW VIOLATION |
| `24` | Disorderly conduct | | 12,015 | PUBLIC PEACE VIOLATION |
| `26` | Miscellaneous non-index offense | | 120,137 | OTHER OFFENSE, CRIMINAL TRESPASS |

Source of the classifications: [Chicago Police Department crime details](https://gis.chicagopolice.org/pages/crime_details). The full list of IUCR codes, with the description of each, is on the [city portal](https://data.cityofchicago.org/d/c7ck-438e).

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

- **One offense name changed.** Chicago renamed `CRIM SEXUAL ASSAULT` to `CRIMINAL SEXUAL ASSAULT`; 2019 and 2020 records use both names. Use `fbi_code` `02` or `iucr` to count sexual assaults across years.
- **Unknown places.** 2,223 rows have `0` for `community_area`. Districts 31 (91 rows) and 61 (2,047 rows) fall outside the 22 standard districts; every district 61 row has an unknown community area.
- **Rounded times and dates.** 3.4% of incidents are timed at exactly midnight and 2.5% at exactly noon, more than the surrounding minutes, and the 1st of the month holds 4.1% of incidents, more than the other days. Many of these record an unknown time or date, which matters for questions about the hour or the day of the month.
- **Months have different lengths.** Only seven months have a 31st, so a raw count makes the 31st look quiet. To compare days of the month, divide each day's count by the number of months that include that day.
- **Arrest rates changed.** The share of incidents with an arrest fell from 21.5% in 2019 to 11.8% in 2022 and rose to 16.1% in 2025.
