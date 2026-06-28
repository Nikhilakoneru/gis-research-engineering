# ArcGIS Experience Builder

## What is Experience Builder
A no-code/low-code tool to build web apps on top of your maps. You drag widgets onto a canvas and connect them to your data. The end result is a shareable URL anyone can open.

## Why it needs a FeatureServer
Experience Builder widgets like Filter and List need to query data in real time. If your layer is just a CSV it has no endpoint to query. You need a hosted feature layer with a FeatureServer URL for the widgets to work.

## Widgets I used

**Map widget** - shows the actual map with your styled layer on it.

**Filter widget** - lets users filter what shows on the map using SQL expressions. Set up `news_outlets <= 0` so users can isolate news deserts with one click.

**List widget** - shows a scrollable list of features alongside the map. Connected it to town_name using an Arcade expression.

## Arcade expression I wrote
```
return $feature.town_name
```
`$feature` means the current row of data. So for each town in the layer it grabs the town_name field and shows it in the list. Basically the GIS version of accessing a property on an object.

## How the Filter widget works
The SQL expression `news_outlets <= 0` gets sent to the FeatureServer as a WHERE clause when the user applies the filter. The map updates to only show features that match. Same SQL as manual REST API queries, just triggered by a button click instead.

## Publishing
Draft = only you can see it. Published = anyone with the link can open it. You have to explicitly publish for it to go live.

## What I Actually Did
- Built a full Experience Builder app called Maine News Coverage App
- Connected it to the Maine News Coverage Map
- Added a Filter widget with `news_outlets <= 0` to show news deserts
- Added a List widget showing town names using `return $feature.town_name`
- Published the app so it has a live public URL
- Learned Arcade while trying to bind list fields to real data
