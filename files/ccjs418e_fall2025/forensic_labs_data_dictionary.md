# Forensic Labs Data Dictionary

**Dataset:** `forensic_labs_clean.csv`
**Source:** Census of Publicly Funded Forensic Crime Laboratories, 2020 (Bureau of Justice Statistics)
**Rows:** 293 labs
**Columns:** 55

---

## Identifiers

| Column | Description |
|--------|-------------|
| `agency_id` | Unique lab identifier |
| `agency_name` | Name of the agency operating the lab |
| `lab_name` | Name of the individual lab facility |
| `state` | Two-letter state abbreviation |
| `region` | Geographic region: Northeast, Midwest, South, West, Other |
| `lab_type` | Type of government: City, County, State, Federal |
| `level_gov_code` | Numeric code for lab type (1=City, 2=County, 3=State, 4=Federal) |

---

## Overall Requests

| Column | Description |
|--------|-------------|
| `requests_2019` | Total requests for analysis received in 2019 |
| `requests_2020` | Total requests for analysis received in 2020 |
| `backlog_total` | Pending requests unreported for 30+ days (as of Jan 1, 2021) |

---

## Employees

| Column | Description |
|--------|-------------|
| `employees_ft_2019` | Full-time employees as of Dec 31, 2019 |
| `employees_pt_2019` | Part-time employees as of Dec 31, 2019 |
| `employees_ft_2020` | Full-time employees as of Dec 31, 2020 |
| `employees_pt_2020` | Part-time employees as of Dec 31, 2020 |

---

## Quality Assurance

| Column | Description |
|--------|-------------|
| `proficiency_testing` | Did the lab conduct proficiency testing in 2020? (Yes/No) |
| `competency_testing` | Did the lab conduct competency testing in 2020? (Yes/No) |
| `accredited` | Was the lab accredited as of Dec 31, 2020? (Yes/No) |

**What's the difference?**
- **Proficiency testing** = Testing the LAB's accuracy by comparing results to other labs on the same samples
- **Competency testing** = Testing individual EMPLOYEES on their skills and knowledge

---

## Requests by Evidence Type (2020)

For each evidence type, there are up to 4 columns:
- `_new` = New requests received in 2020
- `_completed` = Requests completed in 2020
- `_pending` = Requests still pending at end of 2020
- `_backlog` = Requests pending 30+ days (backlogged)

### Controlled Substances (Drugs)
| Column | Description |
|--------|-------------|
| `drugs_new` | New drug analysis requests |
| `drugs_completed` | Drug analysis requests completed |
| `drugs_pending` | Drug analysis requests pending |
| `drugs_backlog` | Drug analysis requests backlogged |

### Toxicology
| Column | Description |
|--------|-------------|
| `tox_new` | New toxicology requests (blood alcohol, drug testing) |
| `tox_completed` | Toxicology requests completed |
| `tox_pending` | Toxicology requests pending |
| `tox_backlog` | Toxicology requests backlogged |

### Trace Analysis
| Column | Description |
|--------|-------------|
| `trace_new` | New trace evidence requests (fibers, glass, paint, etc.) |
| `trace_completed` | Trace requests completed |
| `trace_pending` | Trace requests pending |
| `trace_backlog` | Trace requests backlogged |

### Impressions
| Column | Description |
|--------|-------------|
| `impressions_new` | New impression requests (footwear, tire tracks) |
| `impressions_completed` | Impression requests completed |
| `impressions_pending` | Impression requests pending |
| `impressions_backlog` | Impression requests backlogged |

### Firearms/Toolmarks
| Column | Description |
|--------|-------------|
| `firearms_new` | New firearms/toolmarks requests |
| `firearms_completed` | Firearms requests completed |
| `firearms_pending` | Firearms requests pending |
| `firearms_backlog` | Firearms requests backlogged |

### Digital/Multimedia
| Column | Description |
|--------|-------------|
| `digital_new` | New digital evidence requests (computers, phones) |
| `digital_completed` | Digital requests completed |
| `digital_pending` | Digital requests pending |
| `digital_backlog` | Digital requests backlogged |

### Latent Prints
| Column | Description |
|--------|-------------|
| `latent_prints_new` | New fingerprint analysis requests |
| `latent_prints_completed` | Latent print requests completed |
| `latent_prints_pending` | Latent print requests pending |
| `latent_prints_backlog` | Latent print requests backlogged |

### Questioned Documents
| Column | Description |
|--------|-------------|
| `documents_new` | New document analysis requests (handwriting, forgery) |
| `documents_completed` | Document requests completed |
| `documents_pending` | Document requests pending |
| `documents_backlog` | Document requests backlogged |

### Crime Scene
| Column | Description |
|--------|-------------|
| `crime_scene_new` | New crime scene investigation requests |
| `crime_scene_completed` | Crime scene requests completed |

### DNA/Forensic Biology
| Column | Description |
|--------|-------------|
| `dna_new` | New DNA/biology requests |
| `dna_completed` | DNA requests completed |
| `dna_pending` | DNA requests pending |
| `dna_backlog` | DNA requests backlogged |

---

## Missing Values

- `NaN` indicates missing or not reported data
- Some labs don't perform all evidence types, so those columns will be blank

---

## Possible Analyses

1. **Efficiency by lab type:** Compare completion rates (completed/new) across City, County, State, Federal
2. **Efficiency by region:** Compare backlog rates across Northeast, Midwest, South, West
3. **Efficiency by evidence type:** Which types have the highest backlogs?
4. **Quality and efficiency:** Do accredited labs have lower backlogs?
5. **Staffing and workload:** Requests per employee across lab types
6. **2019 vs 2020:** How did COVID affect request volumes?
