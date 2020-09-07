# Conclusion

Our main objective in this project is to predict whether question is sincere or insincere by reducing bias and variance among different base classifiers. Thus, we have employed Ensemble Method to combie similar or conceptually different learning classifiers via majority or plurality voting. Below is the comparison of the the output of the above-mentioned base models with Ensemble Voting classifier: 

|Accuracy|	F Score|	Model|	Precision	Recall|
|----------|----|--------|-----------------|
|0.945506	|0.637851	|Naive Bayes	|0.818340	|0.594740|
|0.939035	|0.484280	|Random Forest|	0.469518|	0.500000|
|0.951858	|0.739748	|Logistic Regression	|0.819533|	0.695003|
|0.945764	|0.625433	|Voting Classifier |	0.842325|	0.584077|
 
As we can observe that Ensemble method gives best precision of 84.2% among all the base classifiers with a second highest accuracy of 94.5% after Logistic Regression. Thus, we can say that ensemble method gives a balanced prediction of target by covering up the loopholes and errors caused by base algorithms.
