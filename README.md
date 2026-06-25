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


## How It Works

Each object is defined through a configuration file containing:

- Dataset pairs to compare across stages
- Column-level validation rules
- Composite key definitions
- Filtering conditions
- Data quality scoring weights

During execution:

1. Configuration is loaded
2. Datasets are read from Excel
3. Comparisons are performed across defined pairs
4. Validation rules are applied
5. Results are summarized and logged
6. A structured HTML report is generated

---

## Running the Framework

### Run All Configurations

```python
from pathlib import Path
```
runner = ValidationRunner(export_html=True)
runner.run_all(Path("../configs"))


Run a Single Configuration
Pythonrunner = ValidationRunner(export_html=True)runner.run_config(Path("../configs/stcc.json"))Show more lines

Output
Console Output
The console provides step-by-step visibility of execution:

Object being processed
Table under validation
Summary results per dataset comparison
Key findings and rule violations


HTML Report
Each object generates a standalone HTML report with:

Clean section hierarchy
Styled headers and subsections
Highlighted validation status (PASS, FAIL, WARN)
Structured summaries and detailed breakdowns

Example sections:

Summary
Snapshot
Key Findings
Validation Summary
DQ Score Breakdown
Custom Checks


Exporting to PDF
HTML reports can be easily exported to PDF:

Open the generated report.html
Press Ctrl + P
Select "Save as PDF"

For smaller file sizes:

Set scale to 80–90%
Use minimal margins
Disable background graphics if needed


Technology Stack

Python (core logic)
Pandas (data processing)
JSON (configuration)
HTML/CSS (report rendering)
Jupyter Notebook (execution environment)


Design Highlights

Separation of concerns:

Validation logic handled by DataValidator
Rendering and orchestration handled by ValidationRunner


Extensible configuration model
Reusable across multiple supply chain objects
Environment-agnostic reporting (console + HTML)
Scalable to support additional objects and rules


Use Cases

Data migration validation
System integration testing
Data quality monitoring
Supply chain data reconciliation


Future Enhancements

Aggregate dashboard across all objects
PDF export automation
Collapsible sections in HTML reports
Rule engine extensions
Integration with data pipelines


Conclusion
This framework provides a robust, reusable solution for validating complex supply chain datasets across multiple transformation stages. Its configuration-driven design, combined with structured reporting, makes it suitable for enterprise-level data quality assurance and migration validation tasks.

