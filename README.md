# Config-Driven Data Validation Framework for Supply Chain Systems
Carrying out a data validation & quality check in a data migration exercise using python.

## Overview

This project is a configurable data validation framework designed to validate and compare supply chain datasets across multiple transformation stages. It provides a structured, reusable, and scalable approach to ensuring data quality during system integrations and migrations.

The framework compares datasets across stages such as SAP Load, Postload, Preload, and Construct, applying validation rules, measuring data quality, and generating both console and HTML reports for analysis and presentation.

---

## Key Features

- Config-driven validation logic using JSON configuration files
- Support for multi-stage dataset comparisons (e.g., sapload → postload → preload → construct)
- Data quality evaluation across key dimensions (completeness, validity, accuracy, uniqueness, consistency)
- Automatic detection of mismatches, schema issues, and rule violations
- Dynamic composite key generation for record-level consistency checks
- Structured reporting with hierarchical sections (Summary, Snapshot, Key Findings, etc.)
- Dual rendering:
  - Console output (for debugging and traceability)
  - Styled HTML reports (for presentation and sharing)
- Batch execution across multiple data objects
- Clean separation of validation logic and reporting logic

---
