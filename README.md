<div align="center">

# 🧘 YogaDB Dataset

**A developer setup wizard + structured yoga pose dataset — scaffold your own yoga app backend over 48 poses with Sanskrit names, categories, difficulty levels, focus areas, target areas, benefits, instructions, and embedded pose artwork.**

[![Poses](https://img.shields.io/badge/Poses-48-7c3aed?style=flat-square)](data/yoga.json)
[![Categories](https://img.shields.io/badge/Categories-12-10b981?style=flat-square)](#dataset-fields)
[![Format](https://img.shields.io/badge/Format-JSON-orange?style=flat-square)](data/yoga.json)
[![UI](https://img.shields.io/badge/UI-index.html-blue?style=flat-square)](index.html)

</div>

---

## Overview

This repository has been refactored in-place from an exercise dataset into **YogaDB**.

This project was built with inspiration from https://github.com/hasaneyldrm/exercises-dataset.

It now contains:

- `index.html` — standalone searchable yoga pose library.
- `setup.html` — developer setup wizard for database schema, INSERT SQL, API request examples, and LLM scaffold prompts.
- `data/yoga.json` — canonical yoga pose dataset.
- `data/exercises.json` — compatibility copy containing the same yoga data, so older tooling that expects this filename does not break.

## Dataset Fields

Each pose contains:

```json
{
  "id": "0001",
  "name": "Boat",
  "sanskrit_name": "Navasana",
  "sanskrit_name_iast": "Nāvāsana",
  "translation": "Boat Pose",
  "category": "Core Yoga",
  "categories": ["Core Yoga"],
  "difficulty": "Intermediate",
  "focus": "Core",
  "target_areas": ["Abdominals", "Hip Flexors"],
  "description": "...",
  "benefits": "...",
  "instruction_steps": { "en": ["..."] },
  "image": "data:image/png;base64,...",
  "svg": "<svg ...>",
  "created_at": "2026-07-07T00:00:00Z"
}
```

## Current Coverage

- **48** yoga poses
- **12** categories: Backbend Yoga, Balancing Yoga, Chest Opening Yoga, Core Yoga, Forward Bend Yoga, General Yoga, Hip Opening Yoga, Inversion Yoga, Restorative Yoga, Seated Yoga, Standing Yoga, Strengthening Yoga
- **3** difficulty levels: Advanced, Beginner, Intermediate
- **11** focus areas: Balance, Chest, Core, Flexibility, Full Body, Hamstrings, Hips, Legs, Relaxation, Spine, Strength

## Quick Start

Open these files directly in a browser:

```text
index.html   # Browse/search/filter yoga poses
setup.html   # Generate SQL/API/LLM backend scaffolding
```

No build step is required; both pages are self-contained static HTML.

## Recommended API Shape

```text
GET /poses
GET /poses/:id
GET /poses?category=Core%20Yoga&difficulty=Beginner&focus=Core
GET /categories
GET /difficulties
GET /focuses
```

## SQL Table

The setup wizard generates schemas for PostgreSQL, MySQL, SQLite, and SQL Server. The canonical table is `poses`, with fields matching `data/yoga.json`.

## Migration Note

Original exercise files were backed up into:

```text
_backup_exercises_to_yoga_20260707_174745/
```
