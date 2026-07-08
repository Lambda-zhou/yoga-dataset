<div align="center">

# 🧘 YogaDB Dataset

**A developer setup wizard + structured yoga pose dataset — scaffold your own yoga app backend (DB schema, API code, LLM prompt) over 48 poses with Sanskrit names, IAST transliteration, categories, difficulty levels, focus areas, target areas, benefits, English instruction steps, and embedded pose artwork.**

[![Poses](https://img.shields.io/badge/Poses-48-7c3aed?style=flat-square)](data/yoga.json)
[![Categories](https://img.shields.io/badge/Categories-12-10b981?style=flat-square)](#-statistics)
[![Format](https://img.shields.io/badge/Format-JSON-orange?style=flat-square)](data/yoga.json)
[![UI](https://img.shields.io/badge/UI-index.html-blue?style=flat-square)](index.html)

</div>

---

## ⚠️ Notice — embedded pose artwork is included as data

> **This repository is a developer setup wizard and structured yoga pose dataset.** Each pose record includes metadata, practice guidance, and embedded artwork fields (`image` as a Base64 data URI and `svg` markup) so the browser demo can run without downloading extra assets.
>
> The dataset is intended for educational, prototyping, and app-development use. Review the repository license and verify rights/requirements before using the data or artwork in a commercial product.
>
> **If you are a rights holder and want anything removed or clarified, please [open an issue](../../issues) or contact the maintainer.**

---

## 📦 Data Source & Attribution

This repository has been refactored in-place from an exercise dataset into **YogaDB**.

This project was built with inspiration from https://github.com/hasaneyldrm/exercises-dataset.

**Added in this repository** on top of the original scaffold:

- a canonical yoga pose dataset in `data/yoga.json`
- a compatibility copy in `data/exercises.json` for older tooling that expects that filename
- an interactive browser (`index.html`) for searching and filtering poses
- a developer setup wizard (`setup.html`) for SQL schemas, API examples, and LLM backend scaffolding
- embedded pose artwork fields for a self-contained static demo

---

## 📋 Table of Contents

- [Data Source & Attribution](#-data-source--attribution)
- [Overview](#-overview)
- [Interactive Browser & Developer Setup](#-interactive-browser--developer-setup)
- [File Structure](#-file-structure)
- [Statistics](#-statistics)
- [Data Schema](#-data-schema)
- [Sample Poses](#-sample-poses)
- [Usage Examples](#-usage-examples)
- [License & Use](#-license--use)

---

## 🔍 Overview

This dataset is a curated collection of **48 yoga poses** for educational, wellness, research, and rapid application prototyping. It captures common pose names alongside Sanskrit naming, difficulty, practice focus, target areas, benefits, descriptions, and English instruction steps — making it useful for:

- Building yoga, mindfulness, mobility, or home-practice applications
- Creating searchable pose libraries and practice planners
- Prototyping wellness APIs and database-backed apps
- Teaching pose vocabulary with Sanskrit names and IAST transliteration
- Experimenting with recommendation, filtering, or categorization workflows

Each pose record contains structured fields ready for import into PostgreSQL, MySQL, SQLite, SQL Server, a document database, or a static frontend.

---

## 🛠️ Interactive Browser & Developer Setup

Open these files directly in a modern browser — no build step or local server is required:

- **`index.html`** — a standalone searchable yoga pose library with client-side filtering.
- **`setup.html`** — a developer setup wizard that helps turn the JSON dataset into an app backend.

The setup wizard includes three practical sections:

1. **Database Setup** — generate schemas and seed/insert SQL for PostgreSQL, MySQL, SQLite, and SQL Server.
2. **API Integration** — copy-paste client request examples for common languages/tools after entering your API base URL.
3. **Ask Your LLM** — a structured prompt you can paste into ChatGPT, Claude, or Gemini to generate a REST API scaffold using your preferred framework and database.

---

## 📂 File Structure

```text
yoga-dataset-main/
├── data/
│   ├── yoga.json            # Canonical dataset — 48 yoga pose records (JSON array)
│   └── exercises.json       # Compatibility copy containing the same yoga data
├── index.html               # Interactive yoga pose browser (client-side, no server needed)
├── setup.html               # Developer setup guide (DB import + API integration + LLM prompt)
├── sample-README.md         # Original/example README style reference
└── README.md
```

### Key Files

- **`data/yoga.json`** — the primary data file. A JSON array of 48 yoga pose objects with metadata, instructions, and embedded artwork.
- **`data/exercises.json`** — a compatibility copy with the same records, useful when legacy code expects an `exercises.json` path.
- **`index.html`** — standalone pose browser. Open directly in any modern browser.
- **`setup.html`** — developer guide for DB setup, API integration, and LLM-assisted backend generation.

---

## 📊 Statistics

| Metric | Count |
|---|---|
| Total Poses | **48** |
| Categories | **12** |
| Difficulty Levels | **3** |
| Focus Areas | **11** |
| Target Area Labels | **12** |

### Poses by Category

| Category | Pose Count |
|---|---|
| Strengthening Yoga | 10 |
| Core Yoga | 8 |
| Standing Yoga | 7 |
| Chest Opening Yoga | 6 |
| Seated Yoga | 6 |
| Forward Bend Yoga | 3 |
| Backbend Yoga | 2 |
| Hip Opening Yoga | 2 |
| Balancing Yoga | 1 |
| General Yoga | 1 |
| Inversion Yoga | 1 |
| Restorative Yoga | 1 |

### Poses by Difficulty

| Difficulty | Pose Count |
|---|---|
| Intermediate | 28 |
| Advanced | 14 |
| Beginner | 6 |

### Poses by Focus Area

| Focus | Pose Count |
|---|---|
| Strength | 10 |
| Core | 8 |
| Legs | 7 |
| Chest | 6 |
| Flexibility | 6 |
| Hamstrings | 3 |
| Full Body | 2 |
| Hips | 2 |
| Spine | 2 |
| Balance | 1 |
| Relaxation | 1 |

### Target Area Labels

| Target Area | Record Count |
|---|---|
| Legs | 19 |
| Strength | 15 |
| Balance | 9 |
| Core | 8 |
| Flexibility | 8 |
| Hamstrings | 8 |
| Spine | 8 |
| Chest | 7 |
| Hips | 7 |
| Arms | 4 |
| Full Body | 3 |
| Relaxation | 2 |

---

## 🗂️ Data Schema

Each record in `data/yoga.json` follows this structure:

| Field | Type | Description |
|---|---|---|
| `id` | `string` | Unique numeric identifier (e.g. `"0001"`) |
| `name` | `string` | Common English pose name (e.g. `"Boat"`) |
| `sanskrit_name` | `string` | Sanskrit pose name without diacritics (e.g. `"Navasana"`) |
| `sanskrit_name_iast` | `string` | IAST transliteration with diacritics (e.g. `"Nāvāsana"`) |
| `translation` | `string` | Word-by-word meaning or translated pose phrase |
| `category` | `string` | Primary category (e.g. `"Core Yoga"`, `"Standing Yoga"`) |
| `categories` | `array[string]` | Category list, useful for future multi-category records |
| `difficulty` | `string` | Pose difficulty (`Beginner`, `Intermediate`, `Advanced`) |
| `focus` | `string` | Main practice focus (e.g. `Core`, `Flexibility`, `Strength`) |
| `target_areas` | `array[string]` | Body/practice areas associated with the pose |
| `description` | `string` | Human-readable pose description |
| `benefits` | `string` | Benefits and practice effects |
| `instruction_steps.en` | `array[string]` | English step-by-step instructions |
| `image` | `string` | Embedded Base64 image data URI |
| `svg` | `string` | Embedded SVG artwork markup |
| `created_at` | `string` | ISO 8601 timestamp of record creation |

### Sample Record

```json
{
  "id": "0001",
  "name": "Boat",
  "sanskrit_name": "Navasana",
  "sanskrit_name_iast": "Nāvāsana",
  "translation": "nāva = boat, āsana = posture",
  "category": "Core Yoga",
  "categories": [
    "Core Yoga",
    "Seated Yoga",
    "Strengthening Yoga"
  ],
  "difficulty": "Intermediate",
  "focus": "Core",
  "target_areas": [
    "Core",
    "Flexibility",
    "Strength"
  ],
  "description": "From a seated position the feet are lifted up so that the thighs are angled about 45-50 degrees relative to the earth. The tailbone is lengthened into the earth and the pubis pulls...",
  "benefits": "Strengthens the abdomen, hip flexors, and spine. Stimulates the kidneys, thyroid and prostate glands, and intestines. Helps relieve stress. Improves digestion....",
  "instruction_steps": {
    "en": [
      "From a seated position the feet are lifted up so that the thighs are angled about 45-50 degrees relative to the earth.",
      "The tailbone is lengthened into the earth and the pubis pulls toward the navel.",
      "The shoulder blades are spread across the back and the hands reach around the back of the calves, with legs pulled towards the body.",
      "..."
    ]
  },
  "image": "data:image/png;base64,...",
  "svg": "<svg ...></svg>",
  "created_at": "2024-01-01T00:00:00Z"
}
```

---

## 🎬 Sample Poses

> Artwork is bundled inside each record via `image` and `svg`; examples below highlight the metadata and practice guidance.


### 1 — Boat (Navasana) · Core Yoga

> **Difficulty:** Intermediate · **Focus:** Core · **Target areas:** Core, Flexibility, Strength

From a seated position the feet are lifted up so that the thighs are angled about 45-50 degrees relative to the earth. The tailbone is lengthened into the earth and the pubis pulls toward the navel. The shoulder blades are spread across the back and the hands reach around the back of the calves, with legs pulled towards the body. The chin is tipped slightly toward the sternum so that the base of the skull lifts li...

**Benefits:** Strengthens the abdomen, hip flexors, and spine. Stimulates the kidneys, thyroid and prostate glands, and intestines. Helps relieve stress. Improves digestion.

**Practice cues:** From a seated position the feet are lifted up so that the thighs are angled about 45-50 degrees relative to the earth. The tailbone is lengthened into the earth and the pubis pulls toward the navel.
### 2 — Half Boat (Ardha Navasana) · Core Yoga

> **Difficulty:** Intermediate · **Focus:** Core · **Target areas:** Core, Flexibility, Strength

From a seated position the hands are gripped around the back of the legs and the knees are bent in a 90 degree angle. Both legs are pulled in towards the abdomen. The core is engaged to maintain balance on the sits bones (be sure that the back does not round). The front of the torso lengthens between the pubis and top of the sternum as the spine extends in both directions reaching up to the sky and rooting down to...

**Benefits:** Strengthens the abdomen, hip flexors and spine. Stimulates the kidneys, thyroid, prostate glands and intestines. Helps relieve stress. Improves digestion.

**Practice cues:** From a seated position the hands are gripped around the back of the legs and the knees are bent in a 90 degree angle. Both legs are pulled in towards the abdomen.
### 3 — Bow (Dhanurasana) · Chest Opening Yoga

> **Difficulty:** Intermediate · **Focus:** Chest · **Target areas:** Chest, Spine

From a prone position with the abdomen on the earth, the hands grip the ankles (but not the tops of the feet) with knees no wider than the width of your hips. The heels are lifted away from the buttocks and at the same time the thighs are lifted away from the earth working opposing forces as the heart center, hips and back open. The gaze is forward.

**Benefits:** Stretches the entire front of the body, ankles, thighs and groins, abdomen and chest, and throat, and deep hip flexors (psoas). Strengthens the back muscles. Improves posture. Stimulates the organs of the abdomen and neck.

**Practice cues:** From a prone position with the abdomen on the earth, the hands grip the ankles (but not the tops of the feet) with knees no wider than the width of your hips. The heels are lifted away from the buttocks and at the same time the thighs are lifted away from t...
### 4 — Bridge (Setu Bandha Sarvangasana) · General Yoga

> **Difficulty:** Intermediate · **Focus:** Full Body · **Target areas:** Full Body

From a supine position, on your back, the hips are pressed up with the heels of the feet rooted into the earth close to the sits bones. The toes are actively lifted and the pelvis tucked. The thighs are parallel to the earth and the fingers are interlaced under the body with the ribcage lifted and the heart open. The back of the neck rests on the earth. The gaze is to the sky.

**Benefits:** Stretches the chest, neck, and spine. Stimulates abdominal organs, lungs, and thyroids. Rejuvenates tired legs. Improves digestion. Helps relieve the symptoms of menopause. Relieves menstrual discomfort when done supported. Reduces anxiety, fatigue, backach...

**Practice cues:** From a supine position, on your back, the hips are pressed up with the heels of the feet rooted into the earth close to the sits bones. The toes are actively lifted and the pelvis tucked.
### 5 — Butterfly (Baddha Konasana) · Seated Yoga

> **Difficulty:** Intermediate · **Focus:** Flexibility · **Target areas:** Flexibility, Hamstrings, Hips

In sitting position, bend both knees and drop the knees to each side, opening the hips. Bring the soles of the feet together and bring the heels as close to the groin as possible, keeping the knees close to the ground. The hands may reach down and grasp and maneuver the feet so that the soles are facing upwards and the heels and little toes are connected. The shoulders should be pulled back and no rounding of the...

**Benefits:** Opens the hips and groins. Stretches the shoulders, rib cage and back. Stimulates the abdominal organs, lungs and heart.

**Practice cues:** In sitting position, bend both knees and drop the knees to each side, opening the hips. Bring the soles of the feet together and bring the heels as close to the groin as possible, keeping the knees close to the ground.
### 6 — Camel (Ustrasana) · Chest Opening Yoga

> **Difficulty:** Intermediate · **Focus:** Chest · **Target areas:** Chest, Spine

From a kneeling position the knees are hip width apart and the thighs are perpendicular to the earth. The inner thighs are narrowed and rotated slightly inward with the buttocks engaged but not hardened. The tailbone is tucked under but the hips do not puff forward. The shins and tops of the feet are pressed firmly into the earth. The ribcage is open, along with the heart center, but the lower front ribs do not pr...

**Benefits:** Stretches the entire front of the body, the ankles, thighs and groins, abdomen and chest, and throat. Stretches the deep hip flexors (psoas). Strengthens back muscles. Improves posture. Stimulates the organs of the abdomen and neck.

**Practice cues:** From a kneeling position the knees are hip width apart and the thighs are perpendicular to the earth. The inner thighs are narrowed and rotated slightly inward with the buttocks engaged but not hardened.

---

## 🚀 Usage Examples

### Python — Load and Filter

```python
import json

with open("data/yoga.json", "r", encoding="utf-8") as f:
    poses = json.load(f)

print(f"Total poses loaded: {len(poses)}")
# -> Total poses loaded: 48

# Filter by category
core_poses = [pose for pose in poses if pose["category"] == "Core Yoga"]
print(f"Core Yoga poses: {len(core_poses)}")
# -> Core Yoga poses: 8

# Filter by difficulty
beginner = [pose for pose in poses if pose["difficulty"] == "Beginner"]
print(f"Beginner poses: {len(beginner)}")
# -> Beginner poses: 6

# Get all unique categories
categories = sorted({pose["category"] for pose in poses})
print("Categories:", categories)

# Access English instruction steps
pose = poses[0]
for step in pose["instruction_steps"]["en"]:
    print("-", step)
```

### Python — Load with Pandas

```python
import json
import pandas as pd

with open("data/yoga.json", "r", encoding="utf-8") as f:
    data = json.load(f)

df = pd.DataFrame(data)

# Top categories by pose count
print(df["category"].value_counts())

# Intermediate poses focused on core work
core_intermediate = df[(df["focus"] == "Core") & (df["difficulty"] == "Intermediate")]
print(core_intermediate[["name", "sanskrit_name", "category", "difficulty"]])
```

### JavaScript / Node.js

```js
const poses = require("./data/yoga.json");

console.log(`Total poses: ${poses.length}`);

// Beginner poses only
const beginner = poses.filter(pose => pose.difficulty === "Beginner");
console.log(`Beginner poses: ${beginner.length}`);
// -> Beginner poses: 6

// Group poses by category
const byCategory = poses.reduce((acc, pose) => {
  acc[pose.category] = acc[pose.category] || [];
  acc[pose.category].push(pose);
  return acc;
}, {});

// Access names and instructions
const pose = poses[0];
console.log(pose.name, pose.sanskrit_name_iast);
console.log(pose.instruction_steps.en);
```

### TypeScript — Type-safe Usage

```typescript
interface YogaPose {
  id: string;
  name: string;
  sanskrit_name: string;
  sanskrit_name_iast: string;
  translation: string;
  category: string;
  categories: string[];
  difficulty: "Beginner" | "Intermediate" | "Advanced" | string;
  focus: string;
  target_areas: string[];
  description: string;
  benefits: string;
  instruction_steps: {
    en: string[];
  };
  image: string;
  svg: string;
  created_at: string;
}

import poses from "./data/yoga.json";
const data = poses as YogaPose[];

const practicePlan: YogaPose[] = data
  .filter(pose => pose.difficulty !== "Advanced")
  .slice(0, 6);

console.log("Practice plan:", practicePlan.map(p => `${p.name} (${p.sanskrit_name})`));
```

---

## 📄 License & Use

This repository is a **developer setup wizard and structured yoga pose dataset** with pose metadata, English instruction steps, benefits, and embedded artwork.

- Review the repository license before redistribution or commercial use.
- Verify rights and compliance requirements for any production use of pose descriptions, instructions, or artwork.
- This repository does **not** provide medical advice. Yoga practice can involve physical risk; apps built from this dataset should include appropriate safety guidance and encourage users to consult qualified professionals when needed.
- If you are a rights holder and wish to have anything removed or clarified, please [open an issue](../../issues) or contact the maintainer.

- 学 AI，上 L 站：https://linux.do/
