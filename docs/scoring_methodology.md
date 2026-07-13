# Data Quality Scoring Methodology

The framework evaluates data quality using five primary dimensions.

---

## Completeness

Measures the percentage of populated required fields.

Example:

```text
100 rows
95 complete

Completeness = 95%
```

---

## Validity

Measures conformity with business rules.

Examples:

- Allowed values
- Format checks
- Range checks

---

## Accuracy

Measures agreement between compared datasets.

Examples:

- Source vs Target
- Preload vs Postload

---

## Uniqueness

Measures duplicate detection against configured keys.

Examples:

- DB_KEY
- Composite Keys

---

## Consistency

Measures agreement between related datasets across migration stages.

---

## Overall Score

The framework combines the individual dimensions to produce an overall validation score.

Example:

```text
Completeness: 100%
Validity: 96%
Accuracy: 100%
Uniqueness: 100%
Consistency: 100%

Overall: 99.2%
```
