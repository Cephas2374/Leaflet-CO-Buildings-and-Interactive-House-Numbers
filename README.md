# Leaflet CO₂ Buildings and Interactive House Numbers

This repository contains a **Leaflet-based web application** for visualizing building CO₂ data and managing house numbers interactively.

---

## Features

1. **Energy Buildings**

   * Loads `energy.geojson` containing building polygons.
   * Colors polygons based on `co2_class` (A–D).
   * Filter buildings by `energy_projekt_id` using a dropdown.
   * Display popup with building properties.

2. **CO₂ Chart**

   * Shows **Begin CO₂** and **End CO₂** for all or selected project(s).
   * Interactive bar chart using Chart.js.

3. **House Numbers**

   * Loads `house_number.geojson` with `art` property:

     ```
     "art": "longitude;latitude;rotation;HNR;house_number"
     ```
   * Displays numbers as rotated labels on the map.
   * Rotate existing house numbers by clicking (+15° per click).
   * Add new house numbers interactively:

     * Click the “🏠+” button to activate add mode.
     * Select a building.
     * Click inside the building → prompt for number → label added.
   * Newly added numbers are associated with the building via `building_id`.

4. **Export Updated House Numbers**

   * Download all house numbers (existing + newly added + rotations) as `house_number_updated.geojson`.

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/username/leaflet-co2-house-numbers.git
cd leaflet-co2-house-numbers
```

2. Ensure your project folder contains:

   * `index.html` (main web application)
   * `energy.geojson` (building polygons with CO₂ data)
   * `house_number.geojson` (existing house numbers)

3. Open `index.html` in a modern browser.

> Note: To avoid CORS issues, you may need to run a local HTTP server:
>
> ```bash
> python -m http.server 8000
> ```
>
> Then navigate to `http://localhost:8000` in your browser.

---

## Usage

1. **Filter Buildings**

   * Use the dropdown on the top-left to select a project.
   * Map will update polygons and chart accordingly.

2. **View CO₂**

   * The top-right chart shows Begin/End CO₂ for selected project or all projects.

3. **Rotate House Numbers**

   * Click on any house number label → it rotates by 15°.
   * Rotation is stored in the `art` property.

4. **Add New House Numbers**

   * Click the “🏠+” button to activate add mode (button background turns blue).
   * Click on a building → prompt asks for house number.
   * Number is added at click location with rotation 0°.
   * You can rotate the new number by clicking it.
   * To exit add mode, click the “🏠+” button again.

5. **Export House Numbers**

   * Click the “💾” button (top-right) to download the updated `house_number_updated.geojson`.
   * This file includes all new numbers, associated building IDs, and rotation values.

---

## Data Format

### Energy Buildings (`energy.geojson`)

* Polygon geometries.
* Properties include:

  * `energy_projekt_id`
  * `co2_class` (a, b, c, d)
  * `energy_begin_co2_from_energy_demand`
  * `energy_end_co2_from_energy_demand`

### House Numbers (`house_number.geojson`)

* Point geometries.
* Property `art` format:

  ```
  longitude;latitude;rotation (radians);HNR;house_number
  ```
* Optional `building_id` links the number to a building.

---

## Technology Stack

* [Leaflet](https://leafletjs.com/) — map rendering.
* [Chart.js](https://www.chartjs.org/) — CO₂ bar chart.
* Vanilla JavaScript for interactive features.

---

## Planned Enhancements

* Free rotation via mouse drag (currently rotation is by +15° clicks).
* Auto-snap new house numbers inside building polygons.
* Backend integration for saving updates directly to GeoJSON or database.

---

## License

This project is released under the MIT License.

