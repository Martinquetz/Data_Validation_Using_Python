# Config-Driven Data Migration Validation Framework

A Python-based validation framework for comparing, reconciling, and assessing enterprise data quality across migration stages.

Designed for data migration, system integration, and supply chain transformation programs, the framework uses configuration-driven rules to validate data quality, detect discrepancies, and measure reconciliation accuracy between source, staging, and target datasets.

---

## Table of Contents

- [Overview](#overview)
- [The Problem](#the-problem)
- [The Solution](#the-solution)
- [Core Capabilities](#core-capabilities)
  - [Data Reconciliation](#data-reconciliation)
  - [Data Quality (DQ) Validation](#data-quality-dq-validation)
  - [Rule-Based Validation](#rule-based-validation)
  - [Reporting](#reporting)
- [Framework Architecture](#framework-architecture)
- [Validation Workflow](#validation-workflow)
- [Example Objects-Validated](#example-objects-validated)
- [Example Validation Findings](#example-validation-findings)
- [Technology Stack](#technology-stack)
- [Design Principles](design-principles)
- [Typical Use Cases](#typical-use-cases)
- [Getting Started](#getting-started)
- [Future Enhancements](#future-enhancements)
- [Author Note](#author-note)

---

## Overview

Enterprise data migrations frequently involve multiple transformation layers where records are enriched, transformed, staged, loaded, and reconciled before reaching the target system.

This framework provides a scalable and reusable approach for validating data across those stages by performing:

- Record-level reconciliation
- Schema validation
- Business-rule validation
- Data-quality measurement
- Migration readiness assessment
- Automated reporting

The framework is configuration-driven, allowing validation logic to be defined externally without modifying the core codebase.

---

## The Problem

Enterprise migration programs often move data through several transformation stages:

```text
CONSTRUCT (Source)
    ↓
PRELOAD
    ↓
POSTLOAD
    ↓
SAP (Target ERP)
```

During this process, records can:

- Be lost during transformation
- Become duplicated
- Fail business-rule validation
- Drift from source values
- Be loaded with invalid attributes
- Become difficult to trace across stages

Manually validating thousands of records across multiple datasets is time-consuming, expensive, and error-prone.

---

## The Solution

This framework automates migration validation by:

- Comparing datasets across migration stages
- Reconciling records using configurable business keys
- Detecting schema differences and validation-rule violations
- Measuring data quality across multiple dimensions
- Producing structured reports for technical and business stakeholders

The result is a reusable validation layer that can support multiple migration objects with minimal configuration effort.

---

## Core Capabilities

### Data Reconciliation

- Fingerprint-based record matching
- Composite-key validation
- Cross-stage record comparison
- Missing-record detection
- Reconciliation scoring

### Data Quality (DQ) Validation

Evaluates the Following DQ Dimensions:

- Completeness
- Validity
- Accuracy
- Uniqueness
- Consistency

### Rule-Based Validation

Supports configurable checks including:

- Value ranges
- Mandatory fields
- Allowed values
- Pattern validation
- Column profiling
- Custom business rules

### Reporting

Produces:

- Console validation summaries
- HTML validation reports
- PASS / FAIL / WARN indicators
- Data Quality (DQ) scorecards
- Validation breakdowns and findings

---

## Framework Architecture

```text
+-------------+
| JSON Config |
+-------------+
       |
       v
+------------------+
| Dataset Loader   |
+------------------+
       |
       v
+------------------+
| Reconciliation   |
| Engine           |
+------------------+
       |
       v
+------------------+
| Validation Rules |
+------------------+
       |
       v
+------------------+
| DQ Scoring       |
+------------------+
       |
       v
+------------------+
| Report Generator |
+------------------+
```

The framework separates validation logic from reporting logic, enabling scalability and maintainability across data objects.

---

## Validation Workflow

```text
CONFIG
   ↓
LOAD DATASETS
   ↓
GENERATE FINGERPRINTS
   ↓
RECONCILE RECORDS
   ↓
APPLY VALIDATION RULES
   ↓
CALCULATE DQ SCORES
   ↓
GENERATE REPORTS
```

---

## Example Objects Validated

The framework has been validated using synthetic enterprise-scale migration datasets representing real-world supply chain master data scenarios.

| Object | Validation Focus |
|----------|----------|
| STCC Assignment | Reference & mapping validation |
| Business Share | Hierarchical allocation validation |
| Distance & Duration | Geospatial and numeric validation |
| TM Default Route | Route hierarchy and sequence validation |

### Synthetic Data Strategy

To improve reconciliation fidelity, synthetic datasets were generated using a lineage-based approach:

```text
MASTER
   ↓
CONSTRUCT (Source)
   ↓
PRELOAD
   ↓
POSTLOAD
   ↓
SAP (Target ERP)
```

Each downstream dataset is derived from the preceding stage, preserving business relationships and enabling meaningful reconciliation analysis.

---

## Example Validation Findings

The framework is capable of detecting:

- Schema differences
- Missing records
- Invalid values
- Profile violations
- Composite-key duplicates
- Cross-stage reconciliation failures
- Data-quality degradation

### Example Results

```text
Status: PASS | Score: 99.60%

Records: 5000
Alignment: fingerprint

Rule Violations:
- DB_KEY_not_unique
```

```text
Status: FAIL | Score: 97.40%

Rule Violations:
- DURATION_format_violation
- composite_key_duplicates
- LONGITUDE_A_min_violation
```

---

## Technology Stack

- Python
- Pandas
- JSON Configuration
- HTML/CSS Reporting
- Jupyter Notebook
- OpenPyXL (Synthetic Data Generation)

---

## Repository Structure

```text
migration-data-validation-framework/
│
├── README.md
├── requirements.txt
│
├── framework/
│   ├── validation_runner.py
│   ├── comparison_engine.py
│   ├── profiling_engine.py
│   ├── scoring_engine.py
│   └── utils/
│
├── configs/
│
├── sample_data/
│   ├── STCC/
│   ├── BusinessShare/
│   ├── DistanceDuration/
│   └── TMDefaultRoute/
│
├── sample_reports/
│
├── screenshots/
│
├── docs/
│   ├── architecture.md
│   ├── validation_rules.md
│   ├── scoring_methodology.md
│   └── synthetic_data_strategy.md
│
└── synthetic_generators/
```

---

## Design Principles

- Configuration-driven architecture
- Object-agnostic validation logic
- Separation of validation and reporting concerns
- Reusable across migration programs
- Extensible rule framework
- Scalable to large datasets
- Technology-independent reporting

---

## Typical Use Cases

- Data Migration Validation
- ERP Transformation Programs
- Supply Chain Data Reconciliation
- Data Quality Assurance
- System Integration Testing
- Data Governance Initiatives
- Migration Readiness Assessments

---

## Getting Started

### Run All Configurations

```python
from pathlib import Path
from validation_runner import ValidationRunner

runner = ValidationRunner(export_html=True)
runner.run_all(Path("./configs"))
```

### Run a Single Configuration

```python
from pathlib import Path
from validation_runner import ValidationRunner

runner = ValidationRunner(export_html=True)
runner.run_config(Path("./configs/stcc.json"))
```

### Outputs

The framework generates:

- Console execution summaries
- Validation status indicators
- Data Quality scorecards
- HTML reports suitable for stakeholder review

---

## Future Enhancements

- Portfolio-wide validation dashboard
- Automated PDF report generation
- CI/CD integration
- Rule management interface
- Historical trend analysis
- Pipeline orchestration support
- Cloud deployment options

---

## Author Note

This project was developed as a practical solution for validating enterprise migration datasets through configurable reconciliation, data-quality scoring, and rule-based validation.

Synthetic supply-chain migration objects were created to simulate enterprise-scale data migration scenarios and demonstrate validation behavior across multiple transformation stages while preserving realistic business relationships.

The result is a reusable validation framework that combines technical rigor with business-oriented reporting for migration assurance initiatives.
