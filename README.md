# Overview

## [Preprocessing](Preprocessing.md)

## [Model Building](Model Building.md)

## [Conclusion](Conclusion.md)

### Introduction 
How to handle negative and divisive content online is a serious problem for any major website today. Quora wants to address this issue to keep its site a place where users can freely share their knowledge without having to face online toxicity. 
Quora is a forum for people to learn from one another. On Quora, people can ask questions and connect with others who have unique insights and answers to value. A key challenge is to unravel insincere questions. An insincere question is a question founded upon false premises or intend to make a statement instead of seeking helpful answers. 

### Research problem statement 
In this project, we will be predicting whether a question asked on Quora is sincere or not. We will be identifying the insincere questions using the following constraints: 
1. **Has a non-neutral tone** 
- Has an exaggerated tone to underscore a point about a group of people. 
- Is rhetorical and meant to imply a statement about a group of people. 
2. **Is disparaging or inflammatory** 
- Suggests a discriminatory idea against a protected class of people, or seeks confirmation of a stereotype. 
- Makes disparaging attacks/insults against a specific person or group of people. 
- Based on an outlandish premise about a group of people. 
- Disparages against a characteristic that is not fixable and not measurable. 
3. **Isn't grounded in reality** 
- Based on false information, or contains absurd assumptions. 
4. **Uses sexual content** (incest, bestiality, pedophilia) for shock value, and not to seek genuine answers. 

### Data Acquisition 
For this project, we are using [Quora Questions Data Set](https://www.kaggle.com/c/quora-insincere-questions-classification) which is a part of the **Kaggle Competitions**. The training data includes the question that was asked, and whether it was identified as insincere (target = 1). The ground-truth labels contain some amount of noise. The given dataset is already divided into two sets namely, train.csv and test.csv. Overall, it has more than 1.3 million rows.
#### Loading Data  
```Python
TrainData = pd.read_csv(r'C:\Users\admin\Downloads\Project/Training Data.csv')
TrainData.head(10)
````
|qid	|question_text|	target|
|--------|------|------|
|0	00002165364db923c7e6	|How did Quebec nationalists see their province...	|0
|1	000032939017120e6e44	|Do you have an adopted dog, how would you enco...	|0
|2	0000412ca6e4628ce2cf	|Why does velocity affect time? Does velocity a...	|0
|3	000042bf85aa498cd78e	|How did Otto von Guericke used the Magdeburg h...	|0
|4	0000455dfa3e01eae3af	|Can I convert montra helicon D to a mountain b...	|0
|5	00004f9a462a357c33be	|Is Gaza slowly becoming Auschwitz, Dachau or T...	|0
|6	00005059a06ee19e11ad	|Why does Quora automatically ban conservative ...	|0
|7	0000559f875832745e2e	|Is it crazy if I wash or wipe my groceries off...	|0
|8	00005bd3426b2d0c8305	|Is there such a thing as dressing moderately, ...	|0
|9	00006e6928c5df60eacb	|Is it just me or have you ever been in this ph...	|0

### References
* Brownlee, J. (2019, August 7). How to Clean Text for Machine Learning with Python [Online](https://machinelearningmastery.com/clean-text-machine-learning-python/)
* Malik, U. (2019, February 17). Text Classification with Python and Scikit-Learn [Online](https://stackabuse.com/text-classification-with-python-and-scikit-learn/)
* Brownlee, J. (2019, August 7). How to Prepare Text Data for Machine Learning with scikit-learn [Online](https://machinelearningmastery.com/prepare-text-data-machine-learning-scikit-learn/)
* Li, S. (2018, February 20). Multi-Class Text Classification with Scikit-Learn [Online](https://towardsdatascience.com/multi-class-text-classification-with-scikit-learn-12f1e60e0a9f)

#### Libraries Used
`Python`
* [Python Standard Library](https://docs.python.org/2/library/): Built in python modules.
* [Numpy](http://www.numpy.org/): Scientific computing with python.
* [Pandas](http://pandas.pydata.org/): Data analysis tools.
* [Scikit-learn](http://scikit-learn.org/stable/): Machine learning toolkit.
* [NLTK](http://www.nltk.org/): Human language data processing.
