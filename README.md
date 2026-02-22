# Aufbereitung von Daten aus Openstreetmap (OSM) für ArcGIS Pro Network Analyst (NA)
Nutzung Openstreetmap-Daten zur Erzeugung eines Routingnetzes für den ArcGIS Pro Network Analyst https://pro.arcgis.com/en/pro-app/latest/help/analysis/networks/network-analyst-solver-types.htm
- Fußwegrouting als Bestandteil des ÖPNV-Routing https://pro.arcgis.com/en/pro-app/latest/help/analysis/networks/transit-data-model.htm
- Straßenrouting insbesondere Busrouting Vehicle Routing Problem 

## Einlesen der Daten nach DuckDB
- [How to Read OSM Data with DuckDB](https://medium.com/data-science/how-to-read-osm-data-with-duckdb-ffeb15197390)

## Ausschluss von ways, 
- die für Straßen- oder Fußwegrouting irrelevant sind
    - highway:construction
    - highway:proposed
    - highway:bridleway
    - highway:raceway
    - highway:rest_area
    - highway:services

- Auchluss nur für Fußwegrouting
    - highway:trunk
    - highway:motorway
    - highway:motorway_link

## Berücksichtigung der Ebenen aus OSM
- level bei Indoor https://wiki.openstreetmap.org/wiki/Key:level
- layer bei Outdoor https://wiki.openstreetmap.org/wiki/Key:layer
- zusätzliche Zwischenpunkte (vertices) in NA-Network nur bei gleiche Ebene (level/layer)

## Verbesserung des Fußwegroutings bei Fußgängerzonen
- Abbildungen in OSM highway=pedestrian und area=yes
- [Routenplanung durch Flächen](./doc/Routenplanung_durch_Flaechen_MIKSCH_JAKOB.pdf)
- [Integrating open space](./doc/Integrating_Open_Spaces_into_OpenStreetMap_Routing.pdf)
- Aufteilen der Flächen in Hexgone https://uber.github.io/h3-py/api_quick.html

## Berücksichtung von Strecken für das ÖV-Routing, die nur für den ÖPNV befahrbar sind
- highway=service in Kombination mit access=no und bus=yes
- Darstellung von Busspuren bus:lanes lanes:bus lanes:psv 

## Steuerdatei für Sperrung Strecken für Fuß / Bus und Geschwindigkeiten Bus
- Struktur
  - Key:Highway
  - count (nur informativ)
  - Geschwindigkeit Bus (bus_speed)
  - Sperrung Bus (bus_allowed)
  - Sperrung Fuß (foot_allowed)

- [Parameter Routing](./highway_classify.csv)
