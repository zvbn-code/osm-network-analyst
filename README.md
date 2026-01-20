# osm-network-analyst
Nutzung Openstreetmap-Daten zur Erzeugung eines Routing Netzes für den ArcGIS Pro Network Analyst

Ausschluss von ways, die für Straßen- oder Fußwegrouting irrelevant sind
- track
- tram
- standard gauge

Berücksichtigung der Ebenen
- level bei Indoor https://wiki.openstreetmap.org/wiki/Key:level
- layer bei Outdoor https://wiki.openstreetmap.org/wiki/Key:layer

Verbesserung des Fußwegroutings bei Fußgängerzonen
- Abbildungen in OSM highway=pedestrian und area=yes
- https://uber.github.io/h3-py/api_quick.html
