# Synthetic Data Strategy

## Objective

Synthetic datasets were created to demonstrate and test the framework without exposing production data.

---

## Initial Approach

The first generation approach created datasets independently.

```text
CONSTRUCT
PRELOAD
POSTLOAD
SAP
```

This produced realistic structures but poor reconciliation results because records did not share common lineage.

---

## Improved Approach

A lineage-based generation model was introduced.

```text
MASTER
   ↓
CONSTRUCT
   ↓
PRELOAD
   ↓
POSTLOAD
   ↓
SAP
```

Each stage is derived from the previous stage.

---

## Benefits

- Improved reconciliation
- Reduced unmatched records
- Consistent business relationships
- More realistic migration scenarios

---

## Tested Objects

- STCC Assignment
- Business Share
- Distance & Duration
- TM Default Route
