# Codebook: Montgomery County Speeding and Reckless Driving Violations, October 2024–September 2026

**File:** `montgomery_speeding_citations_2024_2026.csv` · 46,733 rows · 46 columns · 18 MB

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/zjelveh/zjelveh.github.io/refs/heads/master/files/ccjs418e_fall2026/montgomery_speeding_citations_2024_2026.csv'
traffic = pd.read_csv(filepath_or_buffer=url)
```

## About the Data

**One row represents one violation written at a traffic stop.** A stop with several violations has several rows with the same `seq_id`; the file holds 42,215 stops.

- **Coverage:** every speeding violation (Maryland Transportation Article §21-801) and every reckless, negligent, or aggressive driving violation (§21-901) recorded by Montgomery County Police from October 1, 2024, through September 30, 2026. These are the twelve months before and the twelve months after the Sergeant Patrick Kepp Act took effect on October 1, 2025.
- **Source:** Montgomery County dataMontgomery portal, [Traffic Violations](https://data.montgomerycountymd.gov/Public-Safety/Traffic-Violations/4mse-ku6q), which lists every electronic traffic violation issued in the county. The county removes information that identifies the vehicle, its owner, or the officer. Downloaded November 8, 2026.
- **What the records measure:** each row is a police decision to stop a driver and write a warning or citation. The counts reflect where and how often police enforce the law as well as how people drive.

## How This File Was Prepared

- Selected violations whose `charge` begins with `21-801` or `21-901` and whose `date_of_stop` falls from October 1, 2024, through September 30, 2026.
- Kept every portal column except `geolocation`, which repeats `latitude` and `longitude`.
- Wrote `date_of_stop` as `YYYY-MM-DD`.
- Added four columns:
  - `recorded_speed` and `posted_limit`, read from descriptions of the form `EXCEEDING POSTED MAXIMUM SPEED LIMIT: 44 MPH IN A POSTED 35 MPH ZONE`; blank when the description gives no speed.
  - `mph_over`, equal to `recorded_speed` minus `posted_limit`.
  - `after_law`, `True` for stops on or after October 1, 2025.
- Sorted rows by `date_of_stop` and `time_of_stop`.

## Columns

**The stop and the violation**

| Column | Meaning | Example |
|---|---|---|
| `seq_id` | Traffic stop ID, shared by every violation written at the same stop | `ce7dbab3-…` |
| `date_of_stop` | Date of the stop | `2024-10-01` |
| `time_of_stop` | Time of the stop | `06:43:00` |
| `agency` | Issuing agency; `MCP` (Montgomery County Police) for every row | `MCP` |
| `subagency` | District or unit the officer is assigned to (table below) | `1st District, Rockville` |
| `description` | Text of the charge | `EXCEEDING THE POSTED SPEED LIMIT OF 35 MPH` |
| `charge` | Section of Maryland law (table below) | `21-801.1` |
| `article` | Body of state law; `Transportation Article` | `Transportation Article` |
| `violation_type` | `Warning` or `Citation` | `Warning` |
| `arrest_type` | Kind of patrol or speed measurement recorded for the stop, such as `A - Marked Patrol`, `Q - Marked Laser`, `E - Marked Stationary Radar` | `Q - Marked Laser` |
| `location` | Block or intersection | `1300 BLK ROCKVILLE PIKE SB` |
| `latitude`, `longitude` | Map coordinates of the stop | `39.0669` |

**Speeds and the law (added columns)**

| Column | Meaning | Example |
|---|---|---|
| `recorded_speed` | Speed written in the description, in mph; blank for 39,160 rows | `44` |
| `posted_limit` | Speed limit written in the description, in mph | `35` |
| `mph_over` | `recorded_speed` minus `posted_limit` | `9` |
| `after_law` | `True` on or after October 1, 2025 | `False` |

**Circumstances** (`Yes` or `No` unless noted)

| Column | Meaning |
|---|---|
| `accident` | The violation involved a crash |
| `contributed_to_accident` | `True` if the violation contributed to a crash |
| `belts` | Seat belts were in use, recorded in crash cases |
| `personal_injury`, `property_damage`, `fatal` | The violation involved an injury, property damage, or a death |
| `alcohol` | The violation included an alcohol-related suspension |
| `work_zone` | The violation happened in a work zone |
| `commercial_license`, `commercial_vehicle`, `hazmat` | Commercial driver's license, commercial vehicle, hazardous materials |

**Searches** (blank for 29,512 rows)

| Column | Meaning |
|---|---|
| `search_conducted` | `Yes` if a search was conducted |
| `search_disposition`, `search_reason`, `search_reason_for_stop`, `search_type`, `search_arrest_reason` | Details of the search, filled in when one took place |
| `search_outcome` | Outcome recorded with the stop: `Warning`, `Citation`, or `Arrest` |

**Vehicle and driver**

| Column | Meaning | Example |
|---|---|---|
| `state` | State of the vehicle registration | `MD` |
| `vehicle_type` | Kind of vehicle | `02 - Automobile` |
| `year`, `make`, `model`, `color` | Vehicle model year, maker, model, and color | `2017`, `LEXS` |
| `race` | Race of the driver: `WHITE`, `BLACK`, `HISPANIC`, `ASIAN`, `NATIVE AMERICAN`, `OTHER` | `BLACK` |
| `gender` | `M`, `F`, or `U` (unknown) | `F` |
| `driver_city`, `driver_state` | City and state of the driver's home address | `MONTGOMERY VILLAGE` |
| `dl_state` | State that issued the driver's license | `MD` |

## Charges

| `charge` | Description | Rows |
|---|---|---|
| `21-801.1` | Exceeding the posted speed limit | 35,516 |
| `21-801(a)` | Driving faster than is reasonable and prudent | 4,250 |
| `21-801(b)` | Failure to control speed to avoid a collision | 2,233 |
| `21-801(c)`–`(h)` | Failure to reduce speed at an intersection, curve, hill, narrow road, or in dangerous conditions | 90 |
| `21-901.1(a)`, `21-901.1(A)` | Reckless driving, including the charge for exceeding the limit by 30 mph or more | 2,079 |
| `21-901.1(b)`, `21-901.1(B)` | Negligent driving | 2,412 |
| `21-901.2`, `21-901.2(A)` | Aggressive driving | 142 |
| `21-901.3(b)` | Causing serious injury or death of a vulnerable individual | 11 |

The same section sometimes appears with an uppercase and a lowercase letter, as in `21-901.1(a)` and `21-901.1(A)`. Use `description` to tell the charges apart.

## Districts

| `subagency` | Rows |
|---|---|
| Headquarters and Special Operations | 22,004 |
| 5th District, Germantown | 5,789 |
| 6th District, Gaithersburg / Montgomery Village | 5,673 |
| 1st District, Rockville | 4,481 |
| 2nd District, Bethesda | 3,545 |
| 3rd District, Silver Spring | 2,993 |
| 4th District, Wheaton | 2,248 |

`subagency` records the district or unit the officer is assigned to, which can differ from where the stop happened.

## Things to Know

- **The law's new charge starts on October 1, 2025.** The description `RECKLESS DRIVING VEH. BY EXCEEDING POSTED SPEED LIMIT BY 30 MPH AND OVER` (and the variant `... EXCEEDING SPD LIMIT BY 30 MPH & OVER`) first appears on that date, under `21-901.1(a)` and `21-901.1(A)`, and covers 566 rows through September 2026. The charge has no earlier records, so a before-and-after comparison of drivers going 30 mph or more over the limit needs another measure for the year before the law, such as `mph_over`.
- **Recorded speeds cover some rows.** 7,573 rows (16%) have a `recorded_speed`, almost all of them `21-801.1` violations. The most common `mph_over` value is 9, which accounts for 56% of the recorded speeds.
- **Warnings and citations.** 71% of rows are warnings. Decide whether your question counts warnings, citations, or both.
- **Violations and stops.** Counting rows counts violations. To count stops, count unique stop IDs: `traffic['seq_id'].nunique()`.
- **Enforcement changes the counts.** The number of violations depends on how many officers are on traffic duty, where they patrol, and what they choose to enforce. A change in counts after the law can reflect a change in enforcement, in driving, or both.
