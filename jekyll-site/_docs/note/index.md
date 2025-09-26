---
title: "MIMIC-IV-Note"
layout: default
nav_order: 26
has_children: true
permalink: /docs/note/
---

# Note Module

The Note module contains deidentified free-text clinical notes for hospitalized patients. As of MIMIC-IV-Note v2.2, only notes from the hospital wide EHR are available. This includes:

- **discharge** - Discharge summaries
- **radiology** - Radiology reports

## Tables in this Module

The Note module contains:

- **discharge** - Discharge summaries
- **discharge_detail** - Information related to discharge summaries
- **radiology** - Radiology reports
- **radiology_detail** - Information related to radiology reports

All notes have been deidentified to protect patient privacy while preserving clinical content for research.
Deidentified entities are replaced with three underscores (`___`).