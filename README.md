# GreenBot
DialogFlow Interface for Georgia Park Data

Work in progress: [data.georgia.org/parks](https://data.georgia.org/parks)

US Census Data - Google BigQuery: https://cloud.google.com/bigquery/public-data/us-census

To Do: Install https://github.com/MishUshakov/dialogflow-web

If install issue occurs, provide version of Node.JS, npm and Operating System here:
https://github.com/MishUshakov/dialogflow-web/issues/9

## Firebase Function Install Steps

cd firebase/functions

npm install

firebase login

firebase init

These can differ:<br>
? What language would you like to use to write Cloud Functions? JavaScript<br>
? Do you want to use ESLint to catch probable bugs and enforce style? No<br>
? File functions/package.json already exists. Overwrite? No<br>
i  Skipping write of functions/package.json<br>
? File functions/index.js already exists. Overwrite? No<br>
i  Skipping write of functions/index.js<br>
? Do you want to install dependencies with npm now? No<br>
Allow Firebase to collect anonymous info - n


Deploy your Cloud Function for Firebase with:<br>
 firebase deploy --only functions:dialogflowFirebaseFulfillment

Source: [https://dialogflow.com/docs/how-tos/getting-started-fulfillment](https://dialogflow.com/docs/how-tos/getting-started-fulfillment)


# About Machine Learning

Machine learning takes a set of inputs and outputs and figures out the correlation all by itself through a set of hidden intermediate steps. Then, when given a new input, it can use the correlation that it “learned” to predict the output for some new input. 

In the case of our chatbot, the machine learning algorithm analyzes some voice input, such as "Find a park near me.", and looks for important segments to input, such as "Find parks" and "near me." The algorithm then prioritizes different input variables pertinent to the user input, which, in this case includes recreational facilities and the location of the user, along with other indirectly related variables such as the weather and reviews of the park.

Once the array input is ready and the algorithm is adjusted for it, the input is inserted into the neural network. The neural network predicts an output and compares it to the actual output. Once it calculates the inaccuracy, the algorithm slightly adjusts itself and calculates a new inaccuracy. If the change in inaccuracy is positive, then the algorithm adjusts itself in the opposite direction, and vice versa. For input with many variables, a partial derivative of the inaccuracy with respect to all of the variables is calculated and the algorithm adjusts itself in the direction where the derivative is negative.

![alt text](https://rasbt.github.io/mlxtend/user_guide/general_concepts/gradient-optimization_files/ball.png)

This optimization algorithm is commonly known as gradient descent, and the inaccuracy is commonly known as cost.

In order to adjust for large data sets and significant clusters, we use a histogram of oriented gradients (HOG). This approach is commonly employed in face detection since everyone has a different shade of skin due to different lightings from image-to-image, but everyone’s skin color for each specific skin pixel stays the same relative to the pixels around it. In order to implement this, we turned all of the input arrays into vectors based on the magnitude and direction averages for the values around each cell of the spreadsheet. The HOG was the true input of the neural network, not the input array itself.

![alt text](https://zone.ni.com/images/reference/en-XX/help/370281AC-01/hog_histogram.gif)

Using HOG also allows for feature extraction in data analysis, so trends in data can be observed across the spreadsheet.
