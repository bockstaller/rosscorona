# Rosscorona

This set of notebooks is used to create maps for a Rosskur-like event.

- Rosscorona.ipynb implements the algorithm creating the route and waypoints
- Master.ipynb is the "UI" for Rosskorona.ipynb
- CreateMaps.ipynb uses the output of Master.ipynb to create maps using maposmatic.osm-baustelle.de

You need an openrouteservice api key to use the Master and Rosscorona notebooks.


## Algorithm

1. Get a roundtrip from the openrouteservice respecting the length, green, quiet parameters to get a baseline route and extract the waypoints
2. Blow up the line route to a corridor of the 200m and get all POIs contained in this corridor
3. Sort the POIs along the waypoints of the original route
4. Try to select POIs as evenly along the route as possible
5. Get a route between the selected POIs to check if the final route is doable


## Known limitations

- using the current code near a border might lead to border crossings. This can be avoided most of the times by running a custom openrouteservice instance via docker, then it is possible to define large enough "avoid polygons" along the borders. But they might be ignored by the openrouteservice anyways
- the route parameters are more suggestions than real limits
