OS OpenData GeoJSON
===================

## Intro ##

Repo for Ordnance Survey data in GeoJSON format. Currently testing ways to minimise file size so that it can be displayed in Github over Leaflet. Using ogr2ogr to convert 

`ogr2ogr -f "GeoJSON" -simplify 0.1 -t_srs crs:84 -Skipfailures SP_AdministrativeBoundary.geojson SP_AdministrativeBoundary.shp`

Then Notepad++ to remove spaces, properties, null features (ogr2ogr currently having various issues with some geometries I suspect because of topological errors in VectorMap District) - using remove space then, remove `"properties":{[a-z":,0-9 ]+},` , then remove `\.[0-9]+` for pushing the coords to 1m  precision (could do in ogr2ogr in future), then remove `{"type":"Feature","geometry":null}` then finally remove line breaks `\n`
,` 

- Changed CRS to WGS84
- Added Railway track as a smaller test dataset to try and visualise it