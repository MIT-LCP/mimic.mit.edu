---
title: "Local database setup"
layout: default
parent: "Getting Started"
has_children: true
nav_order: 2
description: "Set up MIMIC locally on your own database server."
---

# Local database setup

## PhysioNet  

Once your [application to access MIMIC]({{ "/docs/gettingstarted/" | relative_url }}) has been approved, you will be granted access to the 'MIMIC-III Clinical Database' project page on PhysioNet:  
https://physionet.org/content/mimiciii/

## Data and build scripts

MIMIC is provided as a collection of comma-separated (CSV) files, along with scripts to help users import the data into popular database systems. 

Instructions and build scripts for MIMIC are available in the [MIMIC code repository](https://github.com/MIT-LCP/mimic-code) for Postgres, MySQL, and Oracle:  

MIMIC-IV:
https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iv/buildmimic

MIMIC-IV-CXR: N/A. MIMIC-IV-CXR is a set of images and text reports. Code for working with MIMIC-IV-CXR is available online:
https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iv-cxr

MIMIC-IV-ED:
https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iv-ed/buildmimic

MIMIC-III:
https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic


## Tutorial  

In addition to the instructions on GitHub, tutorials for installing MIMIC-III in a local Postgres database are provided for Mac OSX, Unix, and MS Windows systems.
