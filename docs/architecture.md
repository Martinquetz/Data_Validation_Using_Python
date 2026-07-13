# Framework Architecture

## Purpose

The Config-Driven Data Migration Validation Framework provides a reusable and scalable approach for validating enterprise datasets across migration stages.

The framework separates validation logic, scoring, reconciliation, and reporting into independent components.

---

## Core Components

### Validation Runner

Responsible for:

- Loading configurations
- Coordinating execution
- Generating reports

### Validation Engine

Responsible for:

- Schema validation
- Record reconciliation
- Rule execution

### DQ Scoring Engine

Responsible for calculating:

- Completeness
- Validity
- Accuracy
- Uniqueness
- Consistency

### Reporting Layer

Responsible for:

- Console output
- HTML report generation

---

## Processing Flow

```text
CONFIG
   ↓
LOAD DATASETS
   ↓
RECONCILE RECORDS
   ↓
APPLY RULES
   ↓
CALCULATE SCORES
   ↓
GENERATE REPORTS
```

---

## Design Principles

- Configuration-driven
- Reusable
- Scalable
- Technology-independent
- Object-agnostic
