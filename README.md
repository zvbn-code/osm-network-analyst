# Aufbereitung von Daten aus Openstreetmap (OSM) für ArcGIS Pro Network Analyst
Nutzung Openstreetmap-Daten zur Erzeugung eines Routing Netzes für den ArcGIS Pro Network Analyst https://pro.arcgis.com/en/pro-app/latest/help/analysis/networks/network-analyst-solver-types.htm
- fußwegrouting als Bestandteil des ÖPNV-Routing https://pro.arcgis.com/en/pro-app/latest/help/analysis/networks/transit-data-model.htm
- Straßenrouting insbesondere Busrouting Vehicle Routing Problem 

## Ausschluss von ways, 
- die für Straßen- oder Fußwegrouting irrelevant sind
    - track
    - tram
    - standard gauge

- nur für Fußwegrouting
    - trunk
    - motorway

## Berücksichtigung der Ebenen
- level bei Indoor https://wiki.openstreetmap.org/wiki/Key:level
- layer bei Outdoor https://wiki.openstreetmap.org/wiki/Key:layer
- zusätzliche Zwischenpunkte (vertices) nur bei gleiche Ebene (level/layer)

## Verbesserung des Fußwegroutings bei Fußgängerzonen
- Abbildungen in OSM highway=pedestrian und area=yes
- https://uber.github.io/h3-py/api_quick.html

## Berücksichtung von Strecken, die nur für den ÖPNV befahrbar sind
- highway=service in Kombination mit access=no und bus=yes
- Darstellung von Busspuren bus:lanes lanes:bus lanes:psv 
