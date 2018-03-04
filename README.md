# GreenBot
DialogFlow Interface for Georgia Park Data

Machine Learning:

Machine learning takes a set of inputs and outputs and figures out the correlation all by itself through a set of hidden intermediate steps. Then, when given a new input, it can use the correlation that it “learned” to predict the output for some new input. 

In the case of our chatbot, the machine learning algorithm analyzes some voice input, such as "Find a nice park near me.", and looks for important segments to input, such as "Find parks" and "near me." The algorithm then prioritizes different input variables pertinent to the user input, which, in this case includes recreational facilities and and location of the user, along with other indirectly related variables such as the weather and the Google review of the park.

Once the array input is ready and the algorithm is adjusted for it, it is inserted into the neural network. The neural network predicts an output and compares it to the actual output. Once it calculates the inaccuracy, the algorithm slightly adjusts itself and calculates a new inaccuracy. If the change in inaccuracy is positive, then the algorithm adjusts itself in the opposite direction, and vice versa. For input with many variables, a partial derivative of the inaccuracy with respect to all of the variables is calculated and the algorithm adjusts itself in the direction where the derivative is negative.

![alt text](https://rasbt.github.io/mlxtend/user_guide/general_concepts/gradient-optimization_files/ball.png)

This optimization algorithm is commonly known as gradient descent, and the inaccuracy is commonly known as cost.

In order to adjust for large data sets and significant clusters, a histogram of oriented gradients (HOG) was used. This system is commonly employed in face detection since everyone has a different shade of skin due to different lightings from image-to-image, but everyone’s skin color for each specific skin pixel stays the same relative to the pixels around it. In order to implement this, we turned all of the input arrays into vectors based on the magnitude and direction averages for the values around each cell of the spreadsheet. The HOG was the true input of the neural network, not the input array itself.

![alt text](https://zone.ni.com/images/reference/en-XX/help/370281AC-01/hog_histogram.gif)

Using an HOG also allows for feature extraction in data analysis, so trends in data can be observed across the spreadsheet.
