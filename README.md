# Overview

### Introduction 
How to handle negative and divisive content online is a serious problem for any major website today. Quora wants to address this issue to keep its site a place where users can freely share their knowledge without having to face online toxicity. 

Quora is a forum for people to learn from one another. On Quora, people can ask questions and connect with others who have unique insights and answers to value. A key challenge is to unravel insincere questions. An insincere question is a question founded upon false premises or intend to make a statement instead of seeking helpful answers. 


### Research problem statement 
In this project, we will be predicting whether a question asked on Quora is sincere or not. For this, we have developed models that will identify and flag insincere questions. We will be identifying the insincere questions using the following constraints: 

1. **Has a non-neutral tone** 
- Has an exaggerated tone to underscore a point about a group of people 
- Is rhetorical and meant to imply a statement about a group of people 

2. **Is disparaging or inflammatory** 
- Suggests a discriminatory idea against a protected class of people, or seeks confirmation of a stereotype 
- Makes disparaging attacks/insults against a specific person or group of people 
- Based on an outlandish premise about a group of people 
- Disparages against a characteristic that is not fixable and not measurable 

3. **Isn't grounded in reality** 
- Based on false information, or contains absurd assumptions 

4. **Uses sexual content** (incest, bestiality, pedophilia) for shock value, and not to seek genuine answers 


### Data Acquisition 
For this project, we are using [Quora Questions Data Set](https://www.kaggle.com/c/quora-insincere-questions-classification) which is a part of the **Kaggle Competitions**. The training data includes the question that was asked, and whether it was identified as insincere (target = 1). The ground-truth labels contain some amount of noise. The given dataset is already divided into two sets namely, train.csv and test.csv. Overall, it has more than 1.3 million rows. 
