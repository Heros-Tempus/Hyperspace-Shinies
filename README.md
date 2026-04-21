# Legends ZA - Shiny Hyperspace Guide

A static website (hosted via GitHub Pages) that identifies which Pokémon in the *Mega Dimension DLC* can be **force-spawned shiny** using donut mechanics.

## Overview

This project visualizes hyperspace encounter data and highlights cases where a specific **Sparkling Power (donut type)** guarantees a shiny encounter.

The core idea:

> If only one Pokémon in a zone can spawn with a given type, then using a matching Sparkling Power 3 donut will force that Pokémon to appear shiny.

### Example

- **Bug Type — Zone 10 — Star Level 4**
- Available Pokémon:
  - Kleavor
  - Scyther
  - Beedrill
  - Kakuna
  - Scolipede
  - Whirlipede

- Results:
  - **Rock donut → Kleavor (guaranteed shiny)**
  - **Flying donut → Scyther (guaranteed shiny)**
  - Other types fail due to overlaps

## Evolution Overlap Rule

This project intentionally **ignores type overlaps within evolutionary families**.

### Why?

Because from a shiny hunting perspective:

- Catching a pre-evolution is equivalent to catching the evolution
- Example:
  - Kakuna → Beedrill

### Example

- **Bug Type — Zone 3 — Star Level 4**
- Available:
  - Pinsir
  - Beedrill
  - Kakuna
  - Scyther

- Results:
  - **Flying donut → Scyther**
  - **Poison donut → Beedrill OR Kakuna**

Both are considered valid outcomes for shiny Beedrill hunting.

## Features

- Browse zones grouped by Pokémon type
- View:
  - Displayed Pokémon (preview)
  - Full encounter pool
  - Forceable shiny targets
- Expandable UI tiles per zone
- Type-colored interface
- Search with autocomplete
- Filter results to specific Pokémon

## Project Structure

```text
.
├── index.html                     # Main static site
├── data_modified_cleaned.json     # Zone + spawn + forceability data
├── Pokemon_Hyperspace_Map.json    # Pokémon metadata (types, images)
└── images/                        # Local sprite assets
```

### index.html

- Fully self-contained UI
- Loads both JSON files dynamically
- Handles:
  - Rendering tiles
  - Search + filtering
  - Expand/collapse behavior

### data_modified_cleaned.json

Defines encounter data per zone:

```json
{
  "Zone": 10,
  "Star Level": 4,
  "Type": "Bug",
  "AvailableData": [...],
  "Forceable": [
    { "Pokemon": "kleavor", "Donut": "Rock" },
    { "Pokemon": "scyther", "Donut": "Flying" }
  ]
}
```

### Pokemon_Hyperspace_Map.json

Maps Pokémon to:

- Display name
- Types
- Image paths / URLs

## How It Works

1. Each zone defines all possible spawns
2. Each Pokémon has one or more types
3. For each donut type:
   - If exactly one valid target exists → it is **forceable**
   - If multiple share that type → **not forceable**
4. Evolution families are treated as interchangeable

## Image Credits & Usage

All Pokémon images used in this project are **official artwork** owned by The Pokémon Company.

- Image files were originally sourced from Pokémon Database [PokémonDB](https://pokemondb.net/)
- Images are stored locally in this repository to:
  - Reduce external requests
  - Improve performance and load times
  - Avoid placing unnecessary load on Pokémon Database’s servers

This project is **non-commercial** and intended for informational and educational use only.

No ownership is claimed over any Pokémon assets.  
All rights belong to The Pokémon Company, Nintendo, Game Freak, and Creatures Inc.

If requested by a rights holder, the repository can be updated to remove locally hosted images and instead reference the original external image URLs.

If you are a rights holder and would like any content removed or modified, please open an issue or contact the repository owner.

## License

This project’s **code and original data** are licensed under the MIT License.

### Third-Party Content

This repository includes Pokémon names, images, and related assets which are **not covered by the MIT License**.

- Pokémon and all related properties are owned by The Pokémon Company, Nintendo, Game Freak, and Creatures Inc.
- These assets are used for non-commercial, informational purposes only

No rights are granted for redistribution or commercial use of these assets.
