# E2: Symbolization in a GIS

## Warm Up
Firstly, let’s talk about what **symbolization** actually means.  
At its core, symbolization is about **how we visually represent spatial data** — turning raw points, lines, polygons, or rasters into something meaningful and readable on a map.

### What is Symbolization?
Symbolization is the process of assigning **visual variables** (color, size, shape, pattern, transparency, etc.) to spatial features so they communicate information effectively.

For example:
- 🟢 **Points**: Size or color might indicate population of a city.
- 📏 **Lines**: Thickness might show traffic capacity; dashed lines could represent underground routes.
- 🗺️ **Polygons**: Fill color could show land use types; transparency could reveal imagery underneath.
- 🖼 **Rasters**: Color ramps might represent elevation or temperature.

**Goal**: Ensure that the **symbol** (what you draw) matches the **referent** (what it means in the real world) — clearly, consistently, and intuitively.

> Cartographers have developed a set of **visual variables** (shape, size, orientation, color, pattern, transparency, etc.) to express these symbol–referent relationships. The choice of variable depends on whether your data is qualitative (categories) or quantitative (numbers).

---

### Types of Symbolization in GIS
We’ll work with multiple styles today:

1. **Uniform Symbolization** – Same style for all features (e.g., all bus stops shown with the same icon).
2. **Qualitative Symbolization** – Different styles for different categories (e.g., different colors for museums vs. schools).
3. **Quantitative Symbolization** – Styles vary based on numeric values (e.g., darker shades for taller buildings).
4. **Proportional & Graduated Symbols** – Symbol sizes vary with data values.
5. **Cased Line Features** – Multi-layered lines to improve visual clarity.
6. **Scale-based Symbolization** – Symbols change visibility or size depending on zoom level.
7. **Transparency** – See layers underneath while still keeping context.

---

## Task

### Descriptions
Detailed instructions in {download}`Lesson 2 <../doc/Lesson 2.docx>`

& You can [Click here to look](./lessons/lesson2.md)

#### Data
- `Students.gdb`
- Project created in **E1**.

### Overview
#### 1. Uniform Symbolization – Bus Stops
- Add **bus_stops** layer from `Data Students.gdb`.
- Use **Single Symbol** style → choose an appropriate point symbol from the gallery.
- Adjust fill color and size under **Properties → Appearance**.

#### 2. Tram Stops & Underground Stations with External Symbols
- Open **Format Point Symbol → Properties → Layers**.
- Import `Tram_logo.svg` or `UBahn_logo.svg` from the Symbols folder.
- Adjust symbol size if needed.

#### 3. Qualitative Symbolization – Museums & TUM
- **Buildings layer** → Symbolize by `tourism` field (Unique Values).
- Make museums stand out with a unique color.
- Add second field (`amenity`) to also show TUM buildings distinctly while keeping museums highlighted.

#### 4. Quantitative Symbolization – Building Heights
- Use **Graduated Colors** on building height (calculated via Arcade: `$feature.level_num * 3.5`).
- Test different classification methods; create a separate class for "no data" (color it light grey).

#### 5. Proportional Symbols – Roads by Speed
- **Proportional Symbols** style → Field: `speed_num`.
- Set minimum size = 0 to hide no data; choose an appropriate max size.

#### 6. Cased Line Features
- Unique Values → Field: `type_of_road`.
- Select main road classes → apply cased road style.
- Move symbol layers to join and merge intersections properly.

#### 7. Scale-Based Symbolization
- Roads:  
  - Main roads visible at 1:10,000 and larger.  
  - Minor roads visible at 1:5,000 and larger.
- Public transport:  
  - Adjust size stops for different zoom levels (e.g., 50pt at 1:1,000 → 1pt at 1:100,000,000).

#### 8. Transparency
- Adjust building transparency so orthophoto shows through.
- Try the swipe tool to compare layers interactively.

#### 9. Combining Skills – Underground Lines
- Create `line_number` field and populate values for U-Bahn lines.
- Symbolize by category:
  - Solid strokes for U1/U2.
  - Bicolored dashed+solid for shared lines U3/U6 and U4/U5.
- Sort underground lines under buildings to indicate they’re below ground.

---

## Advance Task
- Use **Arcade expressions** to create new fields dynamically.
- Use online tools such as [Maputnik](https://maputnik.github.io/) to explore and experiment with additional map styles you like.

---

## Materials
- [Visual Variables in Cartography](https://www.axismaps.com/guide/data/visual-variables)
- [ArcGIS Pro: Apply Symbology](https://pro.arcgis.com/en/pro-app/latest/help/mapping/layer-properties/change-symbology.htm)
- [Arcade Expression Language](https://developers.arcgis.com/arcade/)
- [Scale-Based Symbology in ArcGIS Pro](https://pro.arcgis.com/en/pro-app/latest/help/mapping/layer-properties/scale-based-symbol-classes.htm)
