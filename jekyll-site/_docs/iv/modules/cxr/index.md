---
title: "Chest X-Ray Module"
layout: default
parent: "MIMIC-IV Modules"
grand_parent: "MIMIC-IV"
nav_order: 4
has_children: true
permalink: /docs/iv/modules/cxr/
---

# Chest X-Ray Module

MIMIC-CXR provides chest X-ray images and radiology reports for a subset of patients admitted to the emergency department. This module contains:

- High-resolution chest X-ray images
- Associated radiology reports
- Study metadata and timing
- Image processing information

## Tables in this Module

The CXR module contains tables for:

- **mimic_cxr_studies** - Study-level metadata
- **mimic_cxr_metadata** - Image metadata  
- **mimic_cxr_reports** - Radiology reports
- **mimic_cxr_sectioned** - Sectioned radiology reports
- **mimic_cxr_chexpert** - CheXpert labels
- **mimic_cxr_negbio** - NegBio labels

This module enables research combining medical imaging with clinical data from the same patients.
