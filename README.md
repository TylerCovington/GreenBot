# GreenBot

[data.georgia.org/parks](https://data.georgia.org/parks)

The Iframe in the page above uses: https://github.com/MishUshakov/dialogflow-web<br>
Note: Avoid "npm init", use "npm install" instead.<br>
We are waiting for DialogFlow 2.0 version from MishUshakov

<b>Projects:</b>

1. Automate pulling available bike-share locations from [Coord.co](https://Coord.co) API. Discuss ways to use docks and existing bike racks with dockless bikes and scooters.

2. Convert 2012-2016 Detailed Table > Block Groups (sets of census blocks) from Tiger.<br>
https://www.census.gov/geo/maps-data/data/tiger-data.html<br>
(Blocks are only available every 10 years.)

3. Pull greenspace from OpenStreetMaps, use shapes instead of boundaries.<br>
https://forum.openstreetmap.org/viewtopic.php?id=61119<br>
Resulting Atlanta park outline dataset in Carto:<br>
https://mycommunity.carto.com/builder/f6c3b59c-449d-4f46-9081-44e3cb1c69ac/embed

4. Work toward showing the amount of green space relative to each census block group. (Needs to add up greenspace from GROUP  BY clause, and also include sum of greenspace area with 1/4 mile of block group.)<br>

SELECT geoid areaID, the_geom, sum(ST_Area(the_geom)/100) AS area, sum(ST_Area(green_geom)/100) AS green_area
FROM (
  SELECT a.geoid, a.the_geom, b.the_geom green_geom
  FROM cb_2016_13_bg_500k a
  JOIN atlanta_greenspace b ON ST_Intersects(a.the_geom, b.the_geom)
) sub
GROUP BY areaID, the_geom
ORDER BY areaID<br>
[Percentage of Polygon Sample](https://gis.stackexchange.com/questions/65956/percentage-of-polygon-in-one-shapefile-within-polygon-of-another)

5. Add sample maps using Google, Carto and MapBox<br>
Parks and green space layers in a combined Carto map.<br>
https://mycommunity.carto.com/builder/2dc11226-86c7-458a-838b-56de1ffd7027/embed<br>
Incomplete park dataset provided to James by city for Park Finder site.

6. Find Firebase Function samples using DialogFlow v2 with Firestore.<br>
Firestore setup (DialogFlow v1):<br>
https://miningbusinessdata.com/firebase-guide-part-1-create-new-dialogflow-agent/

<b>Carto Maps</b>

Census Tracts: https://georgia-map.carto.com/tables/total_population_2016/public/map

Atlanta Greenspace: https://mycommunity.carto.com/dashboard

<b>Related Sites</b>

[Parks Trust Public Land Deserts (Curbed)](https://atlanta.curbed.com/2018/5/1/17307034/atlanta-parks-trust-public-land-deserts) - [View Map](https://parkserve.tpl.org/mapping/index.html?CityID=1304000)


## Firebase Function Install Steps

Our DialogFlow project loads the Firebase Function in this GreenBot repo.

cd firebase/functions

npm install

firebase login

firebase init

These can differ:<br>
What language would you like to use to write Cloud Functions? JavaScript<br>
Do you want to use ESLint to catch probable bugs and enforce style? No<br>
File functions/package.json already exists. Overwrite? No<br>
&nbsp; Skipping write of functions/package.json<br>
File functions/index.js already exists. Overwrite? No<br>
&nbsp; Skipping write of functions/index.js<br>
Do you want to install dependencies with npm now? No<br>
Allow Firebase to collect anonymous info - n

Deploy your Cloud Function for Firebase with:<br>
 firebase deploy --only functions:dialogflowFirebaseFulfillment

Source: [https://dialogflow.com/docs/how-tos/getting-started-fulfillment](https://dialogflow.com/docs/how-tos/getting-started-fulfillment)
