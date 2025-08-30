---
title: "Installing MIMIC-III in a local Postgres database on Windows"
layout: default
parent: "Local database setup"
grand_parent: "Getting Started"
nav_order: 2
description: "Step-by-step guide for installing MIMIC-III locally on Windows systems."
---

# Installing MIMIC-III in a local Postgres database on Windows

These are relatively brief instructions provided to ease installation of PostgreSQL with MIMIC on a Windows machine. If you feel there are key details missing, please [raise an issue](https://github.com/MIT-LCP/mimic-website/issues) with your suggested improvements - we would love to incorporate them!

## Prerequisites

Before proceeding with this guide you will need to:

1. Download the MIMIC-III Clinical Database (see [here]({{ "/docs/gettingstarted" | relative_url }}) for details on gaining access).
2. Extract the MIMIC-III Clinical Database as .csv files somewhere on your local computer.
3. Download the PostgreSQL scripts from [here](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres) - only the files which end in `.sql` are required.

## Quick Start

### 1. Install PostgreSQL

Install PostgreSQL using the installer linked to here:
http://www.postgresql.org/download/windows/

Any version above PostgreSQL v11 should work with instructions and the code written in the [mimic-code repository](https://github.com/MIT-LCP/mimic-code). Earlier versions may also work but with mixed success.

Run through the entire install process. Keeping the defaults will work, but make note of your postgres password, as we will need this later to login to the database system. For convenience, one option is to keep the default username "postgres" and use the password "postgres".

### 2. (Optional) Install compression utilities

It is convenient to install MIMIC directly from the compressed files, as they take up a large amount of space uncompressed. You can either:

- Install [7-zip](http://www.7-zip.org) for easy file extraction
- Install [GNU gzip](http://gnuwin32.sourceforge.net/packages/gzip.htm) for command-line compatibility
- Or decompress all files manually before proceeding

### 3. Load the data

For detailed step-by-step instructions including database setup, table creation, and data loading for Windows systems, please see the complete tutorial in the [MIMIC-III code repository](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres).

The repository includes Windows-specific batch files and PowerShell scripts to automate the process.

## Alternative: Use pgAdmin

pgAdmin is a graphical interface for PostgreSQL that many Windows users find easier to work with than command-line tools. It's typically installed alongside PostgreSQL and provides a user-friendly way to:

- Create databases and tables
- Import CSV data
- Run SQL queries
- Manage database users and permissions

## Need help?

If you encounter issues during installation:

- Check the [GitHub issues](https://github.com/MIT-LCP/mimic-code/issues) for similar problems
- Review the [complete Windows installation guide](https://github.com/MIT-LCP/mimic-code/tree/main/mimic-iii/buildmimic/postgres)
- Ask questions in the [MIMIC discussions](https://github.com/MIT-LCP/mimic-code/discussions)
