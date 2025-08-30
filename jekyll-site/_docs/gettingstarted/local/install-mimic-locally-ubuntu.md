---
title: "Installing MIMIC-III in a local Postgres database"
layout: default
parent: "Local database setup"
grand_parent: "Getting Started"
nav_order: 1
description: "Step-by-step guide for installing MIMIC-III locally on Unix/Mac systems."
---

# Installing MIMIC-III in a local Postgres database

Prerequisites: *This tutorial assumes that you have already completed the [steps required to gain access](/docs/gettingstarted) to the MIMIC dataset on PhysioNet.*

Note that this install was written and tested using Mac OS X and Ubuntu 15.04. If you feel there are key details missing, please [raise an issue](https://github.com/MIT-LCP/mimic-website/issues) with your suggested improvements - we would love to incorporate them!

There are two options for installing MIMIC-III locally in a PostgreSQL database:

1. Manually, by following the tutorial below
2. Automatically, using the make files available in the [mimic-code repository](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres)

These steps are roughly equivalent, though you may learn more about the database configuration by installing the data manually.

## Prerequisites

Before proceeding with this tutorial you will need to:

1. Download the MIMIC-III Clinical Database (see [here](/docs/gettingstarted/) for details on gaining access).
2. Place the MIMIC-III Clinical Database as either .csv or .csv.gz files somewhere on your local computer.
3. Download the PostgreSQL scripts from [here](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres) - only the files which end in `.sql` are required.

It's easiest to move all the MIMIC data files and the scripts to load the data into a single folder (usually called the working directory). Most of the commands below will assume that files are located in the current folder.

## Quick Start

### 1. Install Postgres

Postgres (also known as PostgreSQL) is a database management system. To create an instance of MIMIC-III on your local machine, you'll first need to make sure that Postgres is installed. For installation, please refer to: http://www.postgresql.org/download/

On Mac OSX with the [Homebrew package manager](http://brew.sh/), simply type ```brew install postgres```. On Ubuntu Linux, try ```sudo apt-get install postgresql```.

### 2. Download the CSV data files

Assuming that you have completed the [steps required to gain access](/docs/gettingstarted) to the MIMIC dataset, you should be able to access the CSV data files on PhysioNet at: https://physionet.org/content/mimiciii/.

Download these files to a local folder and decompress them if desired (it is possible to load the data directly into a database from compressed data files). The program `gzip` can be used to decompress the data (e.g. ```gzip -d *.gz```).

### 3. Create database and load data

For detailed step-by-step instructions including database user creation, table creation, and data loading, please see the complete tutorial in the [MIMIC-III code repository](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres).

The automated approach using the provided Makefile is recommended for most users:

```bash
# Clone the repository
git clone https://github.com/MIT-LCP/mimic-code.git
cd mimic-code/mimic-iii/buildmimic/postgres

# Edit the configuration
cp config.ini.example config.ini
# Edit config.ini with your database settings and data file paths

# Build the database
make mimic-gz  # if using compressed files
# or
make mimic     # if using uncompressed files
```

## Need help?

If you encounter issues during installation:

- Check the [GitHub issues](https://github.com/MIT-LCP/mimic-code/issues) for similar problems
- Review the [complete installation guide](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres)
- Ask questions in the [MIMIC discussions](https://github.com/MIT-LCP/mimic-code/discussions)
