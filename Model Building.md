## [Overview](README.md)

## [Preprocessing](Preprocessing.md)

# Model Building

## [Conclusion](Conclusion.md)

# Ensemble Learning

Ensemble learning is a process that uses multiple learning algorithms to obtain better predictive performance that could not be obtained if any of the constituent learning algorithms were used alone. 

There are 3 different Ensemble learning technique:   
1. **Boosting-based Ensemble learning**: Boosting is a sequential process, where each subsequent model attempts to correct the errors of the previous model.   
2. **Bagging based Ensemble learning**: Multiple subsets are created from the original dataset, selecting observations with replacement and fed to different models.   
3. **Voting based Ensemble learning**: The predictions by each model are considered as a ‘vote’. The predictions which we get from majority of the models are used as the final prediction. The method starts with creating two or more separate models with the same dataset. Then a Voting based Ensemble model can be used to wrap the previous models and aggregate the predictions of those models.   

***We have used Voting based Ensemble learning for our purpose.***  

Below are the base classifiers which we have implemented: 

### Model 1: Naïve Bayes 
```Python
nb_ = MultinomialNB()
nb_clf = nb_.fit(X=xtrain_tf, y=y_train)
```
```Python
Model_Comparision = Model_Comparision.append({"Model" : "Naive Bayes", "Accuracy" : accuracy_score(y_test,nb_.predict(xtest_tf)), "F Score" : f1_score(y_test,nb_.predict(xtest_tf), average="macro"), "Precision" : precision_score(y_test,nb_.predict(xtest_tf), average="macro"), "Recall": recall_score(y_test,nb_.predict(xtest_tf), average="macro")}, ignore_index=True) 
```
### Model 2: Random Forest 
```Python
rf_clf = RandomForestClassifier(n_estimators=25, max_depth=15,random_state=42)
rf_clf.fit(X=xtrain_tf,y=y_train)
```
```Python
Model_Comparision = Model_Comparision.append({"Model" : "Random Forest","Accuracy" : accuracy_score(y_test,rf_clf.predict(xtest_tf)), "F Score" : f1_score(y_test,rf_clf.predict(xtest_tf), average="macro"), "Precision" : precision_score(y_test,rf_clf.predict(xtest_tf), average="macro"), "Recall": recall_score(y_test,rf_clf.predict(xtest_tf), average="macro")}, ignore_index=True) 
```
### Model 3: Logistic Regression  
```Python
lreg_clf = LogisticRegression(solver='lbfgs', multi_class='multinomial',random_state=42)
lreg_clf.fit(X=xtrain_tf, y=y_train) 
```
```Python
Model_Comparision = Model_Comparision.append({"Model" : "Logistic Regression", "Accuracy" : accuracy_score(y_test,lreg_clf.predict(xtest_tf)), "F Score" : f1_score(y_test,lreg_clf.predict(xtest_tf), average="macro"), "Precision" : precision_score(y_test,lreg_clf.predict(xtest_tf), average="macro"), "Recall": recall_score(y_test,lreg_clf.predict(xtest_tf), average="macro")}, ignore_index=True) 
```
### Ensemble Model: Voting Classifier
```Python
Voting_clf = VotingClassifier(estimators=[('lr',lreg_clf), ('rf',rf_clf), ('NB', nb_)], voting='hard')
Voting_clf.fit(X=xtrain_tf, y=y_train)
```
```Python
Model_Comparision = Model_Comparision.append({"Model" : "Voting Classifier", "Accuracy" : accuracy_score(y_test,Voting_clf.predict(xtest_tf)), "F Score" : f1_score(y_test,Voting_clf.predict(xtest_tf), average="macro"), "Precision" : precision_score(y_test,Voting_clf.predict(xtest_tf), average="macro"), "Recall": recall_score(y_test,Voting_clf.predict(xtest_tf), average="macro")}, ignore_index=True)
```
