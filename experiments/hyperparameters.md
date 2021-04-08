# Hyperparameters used

The following table shows the hyperparameters experimented with in our approach to find the best-performing ML regression algorithm for TweetExpert. Please note that a grid search was used to determine the best-fit of hyperparameters.

|     Algorithm     	|                           Hyperparameters                           	|
|:-----------------:	|:-------------------------------------------------------------------:	|
|  Majority Voting  	|                                 N/A                                 	|
| Linear Regression 	|                                 N/A                                 	|
|   Random Forest   	|                     n_estimators = [10, 50, 100]                    	|
|        KNN        	|     n_neighbors = [3,5,7,9],  weights = ["uniform", "distance"]     	|
|        SVR        	| C = [1, 10, 50, 100, 500],  epsilon = [0.001, 0.05, 0.01, 0.1, 0.5] 	|