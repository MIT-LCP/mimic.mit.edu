---
title: "caregiver table"
layout: default
parent: "ICU Module"
grand_parent: "MIMIC-IV"
nav_order: 1
permalink: /docs/iv/modules/icu/caregiver/
---

# caregiver table

A description table for the ICU caregivers in the ICU module referenced by *caregiver_id*.

{: .note }
As of MIMIC-IV v2.2, this table simply lists all unique `caregiver_id` in the database.

## Terminology Note

In order to distinguish identifiers used in the hospital wide EHR from those used in the ICU information system, we have adopted the nomenclature of "caregivers" for the ICU (`caregiver_id` and *caregivers*). For the hospital data in the hosp module, we use the terminology of "providers" (`provider_id` and *providers*). However, conceptually, both these sets of identifiers and tables refer to practicing providers at the hospital.

## Table Structure

| Name | Postgres data type |
|------|-------------------|
| caregiver_id | VARCHAR(10) NOT NULL |

### `caregiver_id`

`caregiver_id` lists all possible identifiers for caregivers used in the ICU module.

{% include database/caregiver_id.md %}

## Related Tables

This identifier is used in the following ICU module tables:

- [chartevents](/docs/iv/modules/icu/chartevents/)
- [datetimeevents](/docs/iv/modules/icu/datetimeevents/)
- [inputevents](/docs/iv/modules/icu/inputevents/)
- [outputevents](/docs/iv/modules/icu/outputevents/)
- [procedureevents](/docs/iv/modules/icu/procedureevents/)

## Usage Examples

```sql
-- Count number of unique caregivers
SELECT COUNT(*) FROM caregiver;

-- Find caregiver activity in chartevents
SELECT c.caregiver_id, COUNT(*) as num_entries
FROM caregiver c
LEFT JOIN chartevents ce ON c.caregiver_id = ce.caregiver_id
GROUP BY c.caregiver_id
ORDER BY num_entries DESC;
```

## See Also

- [provider table](/docs/iv/modules/hosp/provider/) - Hospital provider identifiers
- [ICU Module Overview](/docs/iv/modules/icu/) - Overview of all ICU tables
