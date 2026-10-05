# Coordinate & Bearing Calculator

Static bilingual UA/EN web app for GitHub Pages.

## Input Excel
First sheet must contain columns:
- `name`
- `tp_utm_easting`
- `tp_utm_northing`

Required point names: `LM`, `BM`, `SP`, `TP1...TPn`.

## Calculations
- True bearing: grid bearing from UTM X/Y (clockwise from grid north)
- Magnetic bearing: true/grid bearing minus selected declination (8° or 9°)
- Distance: planar UTM distance in metres
- Area: shoelace area for SP → TP1 → ... → TPn → SP

## GitHub Pages
Upload `index.html` to a repository and enable Pages from the repository settings.
