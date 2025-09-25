---
title: "Your First MIMIC Query"
layout: default
parent: "Tutorials"
nav_order: 1
permalink: /tutorials/first-query/
---

# Your First MIMIC Query
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Learn how to write your first query against the MIMIC database. This tutorial assumes you have already gained access to MIMIC data.

## Prerequisites

- Access to MIMIC data (see [Getting Started](/docs/gettingstarted/))
- Basic SQL knowledge
- Access to a query environment (BigQuery, PostgreSQL, etc.)

## Understanding the Basic Structure

MIMIC-IV is organized into modules. Let's start with the most fundamental table: `patients` in the core module.

### The patients table

The `patients` table contains basic demographic information:

{% include database/subject_id.md %}

## Your First Query

Let's count how many patients are in the database:

```sql
SELECT COUNT(*) as total_patients
FROM `physionet-data.mimiciv_hosp.patients`;
```

{: .note }
> This example uses BigQuery syntax. Adjust the table name format for your platform.

### Expected Result

You should see approximately 380,000+ patients in MIMIC-IV.

## Exploring Patient Demographics

Let's look at the gender distribution:

```sql
SELECT 
    gender,
    COUNT(*) as count,
    ROUND(COUNT(*) * 100.0 / SUM(COUNT(*)) OVER(), 2) as percentage
FROM `physionet-data.mimiciv_hosp.patients`
GROUP BY gender
ORDER BY count DESC;
```

## Adding Hospital Admissions

Now let's join with the `admissions` table to see admission patterns:

```sql
SELECT 
    p.gender,
    COUNT(DISTINCT a.hadm_id) as total_admissions,
    COUNT(DISTINCT p.subject_id) as unique_patients,
    ROUND(COUNT(DISTINCT a.hadm_id) / COUNT(DISTINCT p.subject_id), 2) as avg_admissions_per_patient
FROM `physionet-data.mimiciv_hosp.patients` p
JOIN `physionet-data.mimiciv_hosp.admissions` a 
    ON p.subject_id = a.subject_id
GROUP BY p.gender;
```

### Key Concepts

- {% include database/subject_id.md %}
- {% include database/hadm_id.md %}

## Next Steps

Now that you've run your first queries:

1. **Explore other tables** - Try querying [ICU stays](/docs/iv/modules/icu/icustays/)
2. **Learn about data linking** - Understand [cross-module joins](/concepts/cross-module-linking/)
3. **Try more complex analysis** - Move on to [cohort selection](/tutorials/cohort-selection/)

## Common Issues

### Query Timeout
If your query times out, try adding `LIMIT 1000` to test on a smaller dataset first.

### Permission Errors
Ensure you've properly signed the data use agreement for the modules you're querying.

### Different Platforms
- **PostgreSQL**: Remove backticks and use schema.table format
- **AWS**: Use appropriate S3 bucket references
- **Local**: Adjust paths to your local database

---

{: .highlight }
> **Well done!** You've successfully run your first MIMIC queries. Understanding these basic patterns will help you tackle more complex analyses.
