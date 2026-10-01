<div align="center">

# SellTech AI Database

**Structured, validated and versioned hardware data for SellTech AI.**

</div>

---

## Overview

This repository contains the hardware database used by the **SellTech AI** Android application.

It provides structured data for:

- component recommendations
- compatibility analysis
- performance evaluation
- filtering and scoring
- offline database access
- independent database updates

Database releases are maintained separately from the Android application, allowing hardware data to evolve without requiring an app release.

---

## Architecture

```text
Excel Master
     ↓
Validation & Audit
     ↓
JSON Database
     ↓
GitHub
     ↓
SellTech AI
     ↓
Local Cache / Offline Fallback
```

The application checks the repository manifest for newer database versions.

A downloaded database is validated before activation. If an update fails validation, the existing local database remains active.

---

## Repository Structure

```text
SellTech-AI-Database/
│
├── README.md
│
├── database/
│   ├── manifest.json
│   │
│   ├── graphics_cards/
│   │   └── graphics_cards.json
│   │
│   ├── processors/
│   │   └── processors.json
│   │
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

## Database Workflow

Every hardware category follows the same controlled workflow:

1. Define category scope
2. Build and verify the product list
3. Remove duplicates and invalid entries
4. Define the database schema
5. Separate base products and variants
6. Define source priority
7. Collect and verify data field by field
8. Normalize units and values
9. Add compatibility and performance data
10. Preserve source and verification metadata
11. Run automatic validation
12. Manually review anomalies
13. Calculate derived data
14. Complete the final category audit
15. Version and release the database

---

## Data Integrity

SellTech AI databases are designed around:

- authoritative source priority
- normalized values and units
- deterministic data processing
- traceable verification
- automatic validation
- manual anomaly review
- explicit handling of unavailable data

Unknown values are never treated as confirmed compatibility.

Fields without a verified value may be omitted rather than populated with artificial data or unnecessary `null` values.

---

## Versioning & Updates

Database categories are independently versioned while a central manifest controls available releases.

```json
{
  "databaseVersion": "v1.0",
  "schemaVersion": "github-json-v1"
}
```

Before activation, downloaded databases are checked for:

- version consistency
- schema consistency
- category integrity
- product count integrity
- structural validity
- SHA-256 integrity

Invalid updates are rejected without replacing the active database.

---

## Current Status

### Graphics Cards

**Status: Completed — v1.0**

```text
database/graphics_cards/graphics_cards.json
```

**617 validated products**

Additional hardware categories are being built using the same database architecture and validation workflow.

---

## Android Integration

The database is consumed by **SellTech AI**, built with Kotlin and Jetpack Compose.

Runtime database priority:

```text
Validated Local Update
        ↓
Bundled Asset Fallback
```

This allows SellTech AI to receive database updates independently while remaining fully functional offline.

---

<div align="center">

**SellTech AI Database**

*Reliable hardware data. Deterministic recommendations.*

</div>
