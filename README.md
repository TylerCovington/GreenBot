# GreenBot
DialogFlow Interface for Georgia Park Data. Work in progress: [data.georgia.org/parks](https://data.georgia.org/parks)

Iframe uses: https://github.com/MishUshakov/dialogflow-web
Note: Avoid "npm init", use "npm install" instead.

[Parks Trust Public Land Deserts (Curbed)](https://atlanta.curbed.com/2018/5/1/17307034/atlanta-parks-trust-public-land-deserts) - [View Map](https://parkserve.tpl.org/mapping/index.html?CityID=1304000)

Census Tracts: https://georgia-map.carto.com/tables/total_population_2016/public/map

2016 Census Block Groups (sets of census blocks): https://www.census.gov/geo/maps-data/data/tiger-data.html
(Census blocks are only available every 10 years.)

Atlanta Greenspace: https://mycommunity.carto.com/dashboard

Firestore setup:  https://miningbusinessdata.com/firebase-guide-part-1-create-new-dialogflow-agent/

<!--
US Census Data - Google BigQuery: https://cloud.google.com/bigquery/public-data/us-census
-->



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
