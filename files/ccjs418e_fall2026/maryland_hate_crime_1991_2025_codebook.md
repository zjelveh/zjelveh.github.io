# Codebook: Maryland Hate Crime Incidents, 1991–2025 (FBI)

**File:** `maryland_hate_crime_1991_2025.csv` · 6,890 rows · 28 columns · 2 MB

```python
import pandas as pd

url = 'https://raw.githubusercontent.com/zjelveh/zjelveh.github.io/refs/heads/master/files/ccjs418e_fall2026/maryland_hate_crime_1991_2025.csv'
hate = pd.read_csv(filepath_or_buffer=url)
```

## Read This First: The Counts Track Reporting

The FBI publishes the hate crimes that police agencies choose to report to it. The number of Maryland agencies reporting changes a great deal from year to year, and the yearly counts rise and fall with it.

| Year | Incidents | Agencies | Year | Incidents | Agencies | Year | Incidents | Agencies |
|---|---|---|---|---|---|---|---|---|
| 1991 | 431 | 41 | 2003 | 248 | 31 | 2015 | 41 | 11 |
| 1992 | 492 | 45 | 2004 | 245 | 32 | 2016 | 39 | 10 |
| 1993 | 405 | 41 | 2005 | 195 | 29 | 2017 | 102 | 19 |
| 1994 | 330 | 34 | 2006 | 212 | 34 | 2018 | 48 | 20 |
| 1995 | 352 | 40 | 2007 | 151 | 25 | 2019 | 19 | 10 |
| 1996 | 386 | 36 | 2008 | 100 | 23 | 2020 | 45 | 14 |
| 1997 | 323 | 34 | 2009 | 102 | 18 | 2021 | 149 | 24 |
| 1998 | 282 | 32 | 2010 | 80 | 16 | 2022 | 259 | 48 |
| 1999 | 230 | 33 | 2011 | 49 | 19 | 2023 | 262 | 50 |
| 2000 | 218 | 33 | 2012 | 35 | 16 | 2024 | 261 | 44 |
| 2001 | 240 | 29 | 2013 | 51 | 20 | 2025 | 275 | 52 |
| 2002 | 217 | 26 | 2014 | 16 | 9 | | | |

**Agencies** counts the agencies with at least one incident that year. Agencies that reported zero hate crimes do not appear in this file.

- Large agencies move in and out of the counts. Baltimore County Police reported 0–11 incidents a year from 2015 to 2020 and 55–71 a year from 2021 to 2025. Montgomery County Police reported 58 in 2017 and 1–5 a year from 2020 to 2025.
- The jump in 2021–2022 coincides with the FBI's January 2021 move to collecting crime data only through its incident-based system (NIBRS).
- The FBI fills in nothing for agencies that report partially or not at all, and it cautions against comparing years because participation differs from year to year.

**Comparisons that hold up better:**

- **2022–2025:** four years in which 44–52 agencies reported about 260–275 incidents each year.
- **Shares within a year:** the percentage of a year's incidents with each bias type depends less on how many agencies reported than the raw count does.
- **The same agencies over time:** filter to agencies that report in every year you compare, using `ori`.

## About the Data

**One row represents one hate crime incident reported by a Maryland law enforcement agency.** An incident can include several offenses, victims, and offenders.

- **Source:** FBI Crime Data Explorer, [Downloads](https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/downloads), "Hate Crime" dataset, which covers every state from 1991 to 2025. Downloaded November 7, 2026. The download includes the FBI's *Hate Crime Statistics Methodology*.
- **What counts as a hate crime:** a criminal offense motivated, in whole or in part, by the offender's bias against the victim's race/ethnicity/ancestry, gender, gender identity, religion, disability, or sexual orientation. An agency reports an incident as a hate crime when its investigation finds enough evidence to lead a reasonable and prudent person to that conclusion.

## How This File Was Prepared

- Kept the FBI rows whose `state_abbr` is `MD`: 6,890 of the national file's 277,135 incidents.
- Kept all 28 columns with the FBI's names and values unchanged. `pug_agency_name` is the FBI's own spelling of "published agency name."
- Sorted rows by `incident_date`.

## Columns

| Column | Meaning | Example |
|---|---|---|
| `incident_id` | Unique incident number | `452` |
| `data_year` | Year of the incident | `1991` |
| `ori` | Agency identifier (ORI code), the same for an agency in every year | `MD0030100` |
| `pug_agency_name` | Agency name | `Baltimore County Police Department` |
| `pub_agency_unit` | Unit or area within the agency, filled in for agencies such as the University of Maryland (`College Park`) and the Park Police (`Montgomery County`); blank for most rows | `College Park` |
| `agency_type_name` | Kind of agency: `County`, `City`, `University or College`, `State Police`, `Other`, `Other State Agency` | `County` |
| `state_abbr`, `state_name` | `MD`, `Maryland` | `MD` |
| `division_name`, `region_name` | Census division and region: `South Atlantic`, `South` | `South Atlantic` |
| `population_group_code`, `population_group_description` | Size group of the agency's jurisdiction (table below) | `9A`, `MSA counties 100,000 or over` |
| `incident_date` | Date of the incident; text in the form `YYYY-MM-DD` | `1991-01-01` |
| `adult_victim_count`, `juvenile_victim_count` | Victims 18 and older, and under 18; blank before 2013 and in 2015 | `1.0` |
| `total_offender_count` | Number of offenders; `0` when nothing is known about them, and every such row has `offender_race` `Unknown` or `Not Specified` | `1` |
| `adult_offender_count`, `juvenile_offender_count` | Offenders 18 and older, and under 18; blank before 2013, in 2015, and for 31–43% of rows from 2021 on | `1.0` |
| `offender_race` | Race of the offenders as a group: `White`, `Black or African American`, `Asian`, `American Indian or Alaska Native`, `Multiple`, `Unknown`, `Not Specified` | `Unknown` |
| `offender_ethnicity` | `Hispanic or Latino`, `Not Hispanic or Latino`, `Multiple`, `Unknown`, `Not Specified`; mostly `Not Specified` | `Not Specified` |
| `victim_count` | Number of victims of every kind: people, businesses, government, religious organizations, society | `1` |
| `offense_name` | Offense or offenses; several are joined with `;` | `Destruction/Damage/Vandalism of Property` |
| `total_individual_victims` | Number of victims who are people | `0.0` |
| `location_name` | Type of place; several are joined with `;` | `Residence/Home` |
| `bias_desc` | Bias motivation or motivations; several are joined with `;` | `Anti-Jewish` |
| `victim_types` | Kind of victim; several are joined with `;` | `Individual` |
| `multiple_offense` | `S` for one offense type, `M` for more than one | `S` |
| `multiple_bias` | `S` for one bias, `M` for more than one | `S` |

`incident_date` loads as text. Convert it with `pd.to_datetime()` before extracting the month or weekday.

## Bias Types

The ten most common values of `bias_desc` from 2015 to 2025:

| `bias_desc` | Incidents, 2015–2025 |
|---|---|
| Anti-Black or African American | 493 |
| Anti-Jewish | 217 |
| Anti-White | 108 |
| Anti-Gay (Male) | 102 |
| Anti-Lesbian, Gay, Bisexual, or Transgender (Mixed Group) | 92 |
| Anti-Hispanic or Latino | 80 |
| Anti-Multiple Races, Group | 42 |
| Anti-Transgender | 39 |
| Anti-Islamic (Muslim) | 32 |
| Anti-Other Race/Ethnicity/Ancestry | 29 |

**Categories changed over time.** The FBI added disability bias in 1997. In 2013 it revised the sexual-orientation categories, added gender (`Anti-Male`, `Anti-Female`) and gender identity (`Anti-Transgender`, `Anti-Gender Non-Conforming`), and allowed several biases per offense. In 2015 it added religious categories such as `Anti-Sikh`, `Anti-Hindu`, and `Anti-Other Christian`, and made `Anti-Arab` part of the race/ethnicity/ancestry group. The file labels every year with today's category names, while the choices open to agencies changed in 1997, 2013, and 2015. Bias-type comparisons are most consistent from 2015 onward.

**Several biases in one incident.** 69 incidents have more than one bias (`multiple_bias` is `M`); their `bias_desc` lists each one, joined with `;`, such as `Anti-Black or African American;Anti-Jewish`. Decide whether to count these incidents under each bias or as their own group, and say which you chose.

**Grouping categories.** The FBI groups biases into race/ethnicity/ancestry, religion, sexual orientation, gender identity, gender, and disability. To compare groups, create a new column that assigns each `bias_desc` value to its group.

## Population Groups

| Code | Description | Code | Description |
|---|---|---|---|
| `1B` | Cities from 500,000 thru 999,999 | `8A` | Non-MSA counties 100,000 or over |
| `3` | Cities from 50,000 thru 99,999 | `8B` | Non-MSA counties from 25,000 thru 99,999 |
| `4` | Cities from 25,000 thru 49,999 | `8C` | Non-MSA counties from 10,000 thru 24,999 |
| `5` | Cities from 10,000 thru 24,999 | `8D` | Non-MSA counties under 10,000 |
| `6` | Cities from 2,500 thru 9,999 | `9A` | MSA counties 100,000 or over |
| `7` | Cities under 2,500 | `9B`–`9D` | MSA counties under 100,000 |

MSA stands for Metropolitan Statistical Area. Baltimore City is the only Maryland agency in group `1B`.

## Agencies With the Most Incidents, 1991–2025

| `pug_agency_name` | Incidents |
|---|---|
| Baltimore County Police Department | 1,780 |
| Montgomery County Police Department | 1,275 |
| Baltimore (Baltimore City Police) | 683 |
| Howard County Police Department | 519 |
| Prince George's County Police Department | 362 |
| Anne Arundel County Police Department | 331 |
| State Police: | 274 |
| Maryland-National Capital Park Police: | 187 |

137 Maryland agencies appear at least once.
