---
title: Using MIMIC data
layout: default
nav_order: 20
parent: FAQ
---

# Using MIMIC data

{: .note }
> **Can't find your question?** Search through the [issues on GitHub](https://github.com/MIT-LCP/mimic-code/issues).

## How do I link patients across modules?

Understanding how to join data across different MIMIC modules and tables.

### Key Identifiers

#### Patient Level
- `subject_id`: Unique patient identifier across all modules
- Links: All tables contain this identifier

#### Hospital Admission Level
- `hadm_id`: Hospital admission identifier
- Links: Hospital and ICU modules

#### ICU Stay Level
- `stay_id`: ICU stay identifier
- Links: ICU-specific tables

### Common Linking Patterns

#### Hospital to ICU Data
```sql
-- Example: Link admissions to ICU stays
SELECT a.*, i.*
FROM mimiciv_hosp.admissions a
LEFT JOIN mimiciv_icu.icustays i
  ON a.hadm_id = i.hadm_id;
```

#### Patient Demographics
```sql
-- Example: Add patient demographics to any analysis
SELECT analysis.*, p.gender, p.anchor_age
FROM your_analysis_table analysis
LEFT JOIN mimiciv_hosp.patients p
  ON analysis.subject_id = p.subject_id;
```

### Module-Specific Linking

Patients can be linked across distinct MIMIC databases using their identifier. Databases which can currently be linked include MIMIC-IV, MIMIC-IV-ED, MIMIC-IV-ECG, MIMIC-IV-Note, and MIMIC-CXR.

- **Hospital (hosp)**: `subject_id`, `hadm_id`
- **ICU**: `subject_id`, `hadm_id`, `stay_id`
- **Emergency Department (ED)**: `subject_id`, `hadm_id`
    - the `hadm_id` in the MIMIC-IV-ED *edstays* table is the hospitalization immediately *after* the ED stay
- **Chest X-ray (CXR)**: `subject_id` in MIMIC-IV is equal to the `PatientID` metadata element in the DICOM headers of the chest x-rays in MIMIC-CXR
- **ECG**: `subject_id` links to MIMIC-IV; `note_id` links cardiologist notes in the MIMIC-IV-Note module
- **Note**: `subject_id`, `hadm_id`
