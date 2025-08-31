---
title: "MIMIC-III Tables"
layout: default
parent: "MIMIC-III documentation"
nav_order: 20
has_children: true
permalink: /docs/iii/tables/
---

# MIMIC-III Tables

MIMIC-III contains 26 tables covering different aspects of patient care in the ICU and hospital setting.

## Table Categories

### Patient Demographics and Admissions
- **patients** - Patient demographics
- **admissions** - Hospital admissions
- **icustays** - ICU stays
- **transfers** - Patient transfers between units

### Clinical Events  
- **chartevents** - Charted observations and vital signs
- **labevents** - Laboratory test results
- **microbiologyevents** - Microbiology culture results
- **noteevents** - Clinical notes
- **datetimeevents** - Date/time events
- **inputevents_mv** - Fluid inputs (MetaVision)
- **inputevents_cv** - Fluid inputs (CareVue)
- **outputevents** - Patient outputs

### Medications and Procedures
- **prescriptions** - Medication prescriptions  
- **procedureevents_mv** - Procedures (MetaVision)
- **services** - Clinical services
- **cptevents** - CPT codes for procedures

### Reference Tables
- **caregivers** - ICU caregiver information
- **d_cpt** - CPT code dictionary
- **d_icd_diagnoses** - ICD diagnosis code dictionary
- **d_icd_procedures** - ICD procedure code dictionary
- **d_items** - Item dictionary for charted events
- **d_labitems** - Laboratory item dictionary

Each table includes detailed documentation about structure, relationships, and usage patterns.
