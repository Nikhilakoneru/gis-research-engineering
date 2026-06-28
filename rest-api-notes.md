# REST API & FeatureServer

## What is a FeatureServer
A live endpoint that lets you query, filter, and get real data back as JSON. Different from MapServer which is read-only and just serves map images.

## The URL pattern
`https://services.arcgis.com/{org}/arcgis/rest/services/{layerName}/FeatureServer/0/query`

The /0 at the end means layer index 0, the first layer in the service.

## Query Parameters I used
- where= the SQL filter e.g. `news_outlets = 0`
- outFields= which columns to return e.g. `town_name,county`
- f= format, always use json
- returnGeometry= true gives coordinates, false just gives attributes
- resultRecordCount= limits how many rows come back

## What the JSON response looks like
```
{
  "features": [
    {
      "attributes": { "town_name": "Caribou", "news_outlets": 0 },
      "geometry": { "x": -68.01, "y": 46.86 }
    }
  ]
}
```
attributes = the data, geometry = the coordinates on the map.

## SQL WHERE clauses
Same as regular SQL. Examples:
- `news_outlets = 0` exact match
- `news_outlets <= 2` less than or equal
- `county = 'Aroostook'` strings need single quotes
- `1=1` means give me everything, no filter

## How fetch() connects to this
```javascript
fetch(url + "/query?where=1%3D1&outFields=*&f=json")
  .then(res => res.json())
  .then(data => console.log(data.features))
```
The = sign gets URL encoded as %3D. That's why URLs look weird sometimes.

## What I Actually Did
- Queried a real public COVID-19 FeatureServer
- Filtered records using SQL WHERE clauses
- Read actual JSON responses from Esri servers
- Understood how fetch() calls REST endpoints
- Learned why = becomes %3D in URLs
