---
title: Core concepts
parent: About MIMIC-IV
grand_parent: MIMIC-IV documentation
nav_order: 1
---

# Core concepts

A few key concepts when working with MIMIC-IV.

# Patient identifiers

Patients are identified in the database using three possible identifiers: `subject_id`, `hadm_id`, and `stay_id`.
Every unique patient is assigned a unique `subject_id`, all unique hospitalizations are assigned a unique `hadm_id`, and finally all unique ward stays are assigned a unique `transfer_id`. In this context, a ward is a distinct area of the hospital, and a new `transfer_id` is assigned to a patient if the hospital patient tracking system records that they have been moved from one room to another.

However, many patients will move from one specific location to another, but practically their type of care has not changed. A good example is a patient moving bed locations within an ICU: these changes result in the patient having a new `transfer_id`, but the patient never left the ICU and we would consider this as a continuous episode of care. In order to alleviate this issue, we have created a `stay_id`, which is retained across all ward stays of the same type occurring within 24 hours of each other. That is, if a patient leaves and returns to the ICU within 24 hours, they will have the same `stay_id` for the second ICU stay.

## `subject_id`

{% include database/subject_id.md %}

## `hadm_id`

{% include database/hadm_id.md %}

## `transfer_id`

The *transfers* table contains information for each unique `transfer_id`. `transfer_id` is an artificially generated identifier which is uniquely assigned to a ward stay for an individual patient.

## `stay_id`

{% include database/stay_id.md %}

# date and times

Columns which store a date and time in the database are stored with one of two suffixes: `time` or `date`.
If a column has `time` as the suffix, e.g. `charttime`, then the data resolution is down to the minute. If the column has `date` as the suffix, e.g. `chartdate`, then the data resolution is down to the day. That means that measurements in a `chartdate` column will always have 00:00:00 has the hour, minute, and second values. This does *not* mean it was recorded at midnight: it indicates that we do not have the exact time, only the date.

## Date shifting

All dates in the database have been shifted to protect patient confidentiality. Dates will be internally consistent for the same patient, but randomly distributed in the future. Dates of birth which occur in the present time are *not* true dates of birth. Furthermore, dates of birth which occur before the year 1900 occur if the patient is older than 89. In these cases, the patient's age at their first admission has been fixed to 300.

## `charttime` vs `storetime`

Most data, with the exception of patient related demographics, are recorded with a time indicating when the observation was made: `charttime`. `charttime` dates back to the use of paper charts: in order to facilitate efficient observations by nursing staff, the day was separated into hourly blocks, and observations were recorded within these hourly blocks. Thus, any time one performed a measurement between the hours of 04:00 and 05:00, the data would be charted in the 04:00 block, and so on. This concept has carried forward into the electronic recording of data: even if data is recorded at 04:23, in many cases it is still charted as occurring at 04:00.

`storetime` provides information on the recording of the data element itself. All observations in the database must be validated before they are archived into the patient medical record. The `storetime` provides the exact time that this validation occurred. For example, a heart rate may be charted at 04:00, but only validated at 04:40. This indicates that the care provider validated the measurement at 4:40 and indicated that it was a valid observation of the patient at 04:00.
Conversely, it's also possible that the `storetime` occurs *before* the `charttime`. While a Glasgow Coma Scale may be charted at a `charttime` of 04:00, the observation may have been made and validated slightly before (e.g. 3:50). Again, the validation implies that the care staff believed the measurement to be an accurate reflection of the patient status at the given `charttime`.

To recap:

* `charttime` is the time at which a measurement is *charted*. In almost all cases, this is the time which best matches the time of actual measurement. In the case of continuous vital signs (heart rate, respiratory rate, invasive blood pressure, non-invasive blood pressure, oxygen saturation), the `charttime` is usually exactly the time of measurement.
* `storetime` is the time at which the data is recorded in the database: logically it occurs after `charttime`, often by hours, but usually not more than that.

## Other date and time columns present in the database

### `chartdate`

`chartdate` is equivalent to `charttime`, except it does not contain any information on the time (all hour, minute, and seconds are 0 for these measurements).

### `admittime`, `dischtime`, `deathtime`

`admittime` and `dischtime` are the hospital admission and discharge times, respectively. `deathtime` is the time of death of a patient if they died *in* hospital. If the patient did not die within the hospital for the given hospital admission, `deathtime` will be null.

### `intime`, `outtime`

`intime` and `outtime` provide the time at which a patient entered and exited the given unit. In the *icustays* table, the unit is always an ICU. In the *transfers* table, the unit can be any ward in the hospital.

### `starttime`, `endtime`

For events which occur over a period of time, `starttime` and `endtime` provide the beginning and end time of the event. For medical infusions, these columns indicate the period over which the substance was administered.

### `dod`

`dod` is the patient's date of death sourced from one of two sources: the hospital database or a state death database. See the [*patients*](/docs/iv/modules/hosp/patients) documentation for more detail.

### `transfertime`

`transfertime` is the time at which the patient's service changes.
