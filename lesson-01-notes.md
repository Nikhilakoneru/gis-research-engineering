# Lesson 01 - GIS & REST API Basics

## What is GIS?
It's basically putting data on a map so it 
makes more sense than just looking at a 
CSV file with rows and columns.

## ArcGIS Online
Cloud platform where everything lives - data, 
maps, services. Think of it like Google Drive 
but for maps.

## REST API
A URL based system to access everything in 
ArcGIS. Every map, layer, item has its own URL.
The API is stateless which means every request 
is treated as a new request - it has no memory 
of previous requests.

## URL Structure
server/path?parameters
- ? starts the parameters
- & adds more parameters
- = signs get encoded as %3D in the browser
- commas get encoded as %2C

## MapServer vs FeatureServer
MapServer - read only, like a photo of a map,
can't query it directly.
FeatureServer - full access, can query, filter,
edit and download data.

## Geometry Types
- Point - a single spot like a news outlet
- Polyline - a path like a highway
- Polygon - a shape with area like a state or town

## Renderers
How features look on the map:
- Simple - everything same color
- Unique Value - different category different color
- Class Breaks - color by number ranges
  e.g. 0 news outlets = red, 1-2 = yellow, 3+ = green

## Query Parameters
- where= filter data e.g. POP2000 > 5000000
- outFields= which columns you want back
- resultRecordCount= how many results
- f= format json or pjson
- where=1=1 means give me everything

## What I Actually Did Today
- Made my first REST API call in the browser
- Read real JSON responses from Esri servers
- Queried US Census data and filtered by population
- Learned to use the Services Directory
- Understood how URL parameters work
