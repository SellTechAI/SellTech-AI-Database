<div align="center">

# SellTechAI-Database

**Hardware database for SellTech AI.**

</div>

---

## Overview

This repository contains the structured and versioned hardware database used by the **SellTech AI** Android application.

The database supports:

- component recommendations
- compatibility checks
- performance analysis
- filtering and scoring
- Supabase synchronization
- Room synchronization
- future database updates

---

## Structure

```text
SellTechAI-Database/
│
├── README.md
├── VERSION.json
│
├── database/
│   ├── graphics_cards/
│   │   ├── graphics_cards.json
│   │   └── version.json
│   ├── processors/
│   ├── motherboards/
│   ├── memory/
│   ├── storage/
│   ├── power_supplies/
│   ├── cases/
│   └── cooling/
│
├── schemas/
├── validation/
├── sources/
├── audit/
├── scripts/
└── archive/
```

---

## Data Workflow

Each component category follows the same process:

1. Define category scope
2. Build the product list
3. Remove duplicates and invalid entries
4. Define database schema
5. Separate base products and variants
6. Define source priority
7. Collect data field by field
8. Verify completed fields
9. Normalize units and values
10. Add compatibility and performance data
11. Store source and verification metadata
12. Run automatic validation
13. Review anomalies manually
14. Calculate derived data
15. Complete final category audit
16. Version and release the database

---

## Data Quality

The database is built around:

- reliable sources
- normalized values
- minimal unnecessary missing data
- traceable verification
- automatic validation
- manual review

Fields with unavailable or non-applicable data may be omitted instead of storing unnecessary `null` values.

---

## Versioning

Each category has its own version metadata.

Example:

```json
{
  "databaseVersion": "v1.0",
  "schemaVersion": "github-json-v1"
}
```

---

## Current Status

### Graphics Cards

The Graphics Cards category is the first completed database category.

Main files:

```text
database/graphics_cards/graphics_cards.json
database/graphics_cards/version.json
```

Additional component categories will be added using the same structure and validation workflow.

---

## Integration

The database is designed for integration with:

- Kotlin
- Jetpack Compose
- Room
- Supabase

The database repository is kept separate from the Android application repository so hardware data can be updated and versioned independently.
