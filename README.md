# 🗺️ CO₂ Energy Map with Rotated House Numbers

This project is a **Leaflet-based interactive map** that visualizes:

- 🏘️ **Building footprints** styled by CO₂ class
- 📊 Dynamic **CO₂ emission charts** (Bar & Pie)
- 🔢 **House numbers** with correct **positioning and rotation**, extracted from attribute data

---

## 📦 Features

- 🗺️ **Leaflet.js** base map using Carto Light tiles
- 🏠 **GeoJSON buildings** (`energy.geojson`) styled by `co2_class`
- 📊 **Bar & Pie Charts** showing:
  - Total CO₂ emissions (`begin_co2`, `end_co2`)
  - Class distribution
- 🔢 **Rotated House Numbers**:
  - Extracted from `house_number.json`
  - Includes rotation angle and label
  - Positioned using `EPSG:25832 → WGS84` conversion
- 🔘 Small circle marker rendered under each house number for precision

---

## 📁 Project Structure

```text
📦 your-project-folder/
│
├── index.html              # Main interactive map
├── energy.geojson          # Building footprints with CO₂ data
├── house_number.json       # House number labels and rotations
└── README.md               # You're here
