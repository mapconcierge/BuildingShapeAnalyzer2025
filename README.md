# Building Shape Analysis Tool

A web-based GeoJSON analysis tool for computing geometric properties of building polygons, including orientation, shape metrics, and entrance accessibility analysis.

<img width="3024" height="1900" alt="Image" src="https://github.com/user-attachments/assets/9576848f-9b08-45fc-8edc-8481f1b30db9" />


## Features

### Core Analysis
- **Area Calculation**: Accurate geodesic area computation in square meters
- **Roundness Index**: Circularity measurement (4π × area / perimeter²)
- **Centroid Calculation**: Geographic center point (WGS84)
- **Major Axis Orientation**: Principal component analysis-based azimuth angle (0-360°, clockwise from North)
- **Entrance Analysis**: Distance and bearing to nearest building entrance

### Visualization
- **Interactive Map**: MapLibre GL JS with OpenFreeMap vector tiles
- **Building Overlays**: Semi-transparent polygons with orientation arrows
- **Entrance POIs**: Black circular markers for `entrance=main` and `entrance=yes`
- **Connection Lines**: Blue lines from building centroids to nearest entrances
- **Rose Diagrams**: Dual polar charts showing building orientation and entrance direction distributions

### Data Export
- **CSV Download**: Complete dataset with all computed metrics
- **Statistical Summary**: Count, sum, mean, standard deviation, min, max for all features

## Live Demo
https://mapconcierge.github.io/BuildingShapeAnalyzer2025/

<<<<<<< HEAD
## Usage

1. **Upload GeoJSON**: Click the file input and select a GeoJSON file containing building polygons (EPSG:4326)
2. **View Analysis**: 
   - Buildings appear as teal polygons with red orientation arrows
   - Arrow length = 2× building's major axis
   - Blue lines connect buildings to nearest entrances (within search radius)
3. **Explore Data**: Click any building to see detailed metrics in a popup
4. **Download Results**: Click "Download CSV" to export all computed data

## Computed Metrics

| Metric | Description | Unit |
|--------|-------------|------|
| `area_sqm` | Geodesic area | m² |
| `roundness` | Circularity index (1.0 = perfect circle) | - |
| `centroid_lon` | Centroid longitude | degrees |
| `centroid_lat` | Centroid latitude | degrees |
| `orientation_deg` | Major axis azimuth | degrees (0-360) |
| `axis_length_m` | Major axis length (2× max centroid distance) | meters |
| `entrance_distance_m` | Distance to nearest entrance | meters |
| `entrance_bearing_deg` | Bearing to nearest entrance | degrees (0-360) |
| `entrance_type` | Entrance classification | main/yes |

## Technical Details

### Dependencies
- **MapLibre GL JS** (v3.6.2): Map rendering
- **Turf.js** (v6.5.0): Geospatial calculations
- **Chart.js** (v4.4.0): Rose diagram visualization
- **Overpass API**: Real-time entrance data retrieval

### Architecture
- **Client-side only**: No server required
- **Single HTML file**: All code embedded for easy deployment
- **GitHub Pages ready**: Deploy directly to `/docs` folder

### Entrance Data
- **Source**: OpenStreetMap via Overpass API
- **Query**: `node["entrance"="main"]` and `node["entrance"="yes"]`
- **Search Radius**: 2× building major axis length
- **Priority**: `entrance=main` → `entrance=yes`
- **Update Trigger**: Map movement at zoom ≥16

### Algorithms
- **Orientation**: Principal Component Analysis (PCA) of polygon vertices
- **Area**: Turf.js geodesic area calculation (accounts for latitude distortion)
- **Roundness**: Polsby-Popper compactness measure
- **Bearing**: Turf.js bearing calculation (origin: centroid, destination: entrance)

## Rose Diagrams

### Building Orientation
- **Bins**: 16 directions (22.5° each)
- **Color**: Teal (#088888)
- **Interpretation**: Shows preferred building alignment (e.g., street grid patterns)

### Entrance Direction
- **Bins**: 16 directions (22.5° each)
- **Color**: Dark blue (#000099)
- **Interpretation**: Shows entrance accessibility patterns relative to building positions

## Map Controls
- **Zoom/Pan**: Standard map navigation
- **POI Layers**: All non-entrance POIs hidden for clarity
- **Base Map**: OpenFreeMap Liberty style (vector tiles)

## File Requirements

### Input GeoJSON
```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[lon, lat], ...]]
      },
      "properties": {
        "name": "Building Name",
        ...
      }
    }
  ]
}
```

- **CRS**: EPSG:4326 (WGS84)
- **Geometry**: Polygon or MultiPolygon
- **Properties**: Optional (preserved in output)

### Output CSV
All original properties plus computed metrics (see table above)

## Browser Support
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+

## Deployment

### GitHub Pages
1. Place `index.html` in `/docs` folder
2. Enable GitHub Pages in repository settings
3. Select `main` branch and `/docs` folder
4. Access via `https://username.github.io/repository-name/`

### Local Development
Simply open `index.html` in a browser. No build process required.

## Limitations
- **Entrance Data**: Requires internet connection for Overpass API
- **Performance**: Large datasets (>1000 buildings) may slow entrance processing
- **Search Radius**: Entrances beyond 2× major axis length are not connected
- **Rate Limiting**: Overpass API has usage limits (25s timeout per query)

## Use Cases
- Urban planning analysis
- Building orientation studies
- Accessibility assessment
- Architectural pattern recognition
- Street network alignment research

## License
This tool is provided as-is for educational and research purposes.

## Credits
- **Map Tiles**: [OpenFreeMap](https://openfreemap.org/)
- **Entrance Data**: [OpenStreetMap](https://www.openstreetmap.org/) contributors
- **Libraries**: MapLibre GL JS, Turf.js, Chart.js

## Version
v6.0 - November 2025

## Contributing
Contributions welcome! Please open an issue or submit a pull request.

## Support
For questions or issues, please open a GitHub issue with:
- Sample GeoJSON file (if applicable)
- Browser and version
- Description of the problem
=======
<img width="3024" height="1900" alt="Image" src="https://github.com/user-attachments/assets/9576848f-9b08-45fc-8edc-8481f1b30db9" />

>>>>>>> 617831e8ba2e200892b6327495c5b721e1d8ae79
