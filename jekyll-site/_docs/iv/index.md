---
title: "MIMIC-IV"
layout: default
nav_order: 21
has_children: true
permalink: /docs/iv/
---

# MIMIC-IV Documentation

MIMIC-IV is the latest version of the MIMIC Critical Care Database. It contains de-identified health data associated with patients admitted to the Beth Israel Deaconess Medical Center between 2008 and 2019.

## What's New in MIMIC-IV

- **Larger patient population** - Over 380,000 hospital admissions
- **Extended time range** - Data from 2008-2019
- **Modular structure** - Organized by data provenance
- **Enhanced data quality** - Improved cleaning and validation
- **Cloud-native** - Optimized for cloud platforms

## MIMIC-IV Modules

MIMIC-IV is organized into modules based on the source of the data:

### Core Module
Patient demographics, admission tracking, and stay information.

[Explore Modules →]({{ "/docs/iv/modules/" | relative_url }}){: .btn .btn-outline }

### Hospital (Hosp) Module  
Data from the hospital-wide electronic health record including lab results, medications, diagnoses, and procedures.

[Explore Hosp Module →]({{ "/docs/iv/modules/hosp/" | relative_url }}){: .btn .btn-outline }

### ICU Module
Highly granular data from the ICU including vital signs, fluid balance, and charted observations.

[Explore ICU Module →]({{ "/docs/iv/modules/icu/" | relative_url }}){: .btn .btn-outline }

### Emergency Department (ED) Module
Emergency department data including triage, vital signs, and treatment information.

[Explore ED Module →]({{ "/docs/iv/modules/ed/" | relative_url }}){: .btn .btn-outline }

### Chest X-Ray (CXR) Module
Chest X-ray images and associated radiology reports.

[Explore CXR Module →]({{ "/docs/iv/modules/cxr/" | relative_url }}){: .btn .btn-outline }

### Note Module
De-identified clinical notes and reports.

[Explore Note Module →]({{ "/docs/iv/modules/note/" | relative_url }}){: .btn .btn-outline }

## Getting Started with MIMIC-IV

1. **Understand the structure** - Review the [modular organization]({{ "/docs/iv/modules/" | relative_url }})
2. **Learn about identifiers** - Understand how patients are [linked across modules]({{ "/docs/iv/about/" | relative_url }})
3. **Try the tutorials** - Start with [MIMIC-IV tutorials]({{ "/docs/iv/tutorials/" | relative_url }})
4. **Explore concepts** - See [core concepts]({{ "/docs/iv/about/concepts/" | relative_url }})
