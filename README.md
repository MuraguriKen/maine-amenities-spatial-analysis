# Maine Amenities Spatial Analysis (PostGIS + QGIS)

Spatial analysis of Maine **schools** versus public amenities (**fire stations, police stations, hospitals**) using **PostgreSQL/PostGIS** and **QGIS**.

## Questions explored
- Total counts of each amenity type
- Counts per county (spatial join using county boundaries)
- Average number of schools per county
- Counties with max/min counts per amenity type
- Ratios of schools to each amenity type
- Example spatial filters (Bangor area bounding box)
- Proximity checks (closest/furthest examples)

## Files
- `sql/postgres_postgis.sql` – Primary PostGIS queries (counts, spatial joins, ratios, Bangor subset, proximity)
- `sql/qgis_queries.sql` – Queries used inside QGIS (feature inspection, bounding box filters, closest/furthest selections)

## Tools
- PostgreSQL + PostGIS
- QGIS

## Notes / Assumptions
- Distance calculations depend on CRS. For meters, use a projected CRS (e.g., EPSG:26919) or `geography` casting.
- Ratio queries should cast counts to numeric and use `NULLIF` to avoid divide-by-zero.
- Closest-distance queries can be optimized using KNN (`<->`) + `LATERAL` joins.
