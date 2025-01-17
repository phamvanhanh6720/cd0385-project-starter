# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Hanh Pham Van

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
Actually, I did not see any negative values in the first predictions of the model. So, I did not add a process function to correct the predictions. And, I saw that the first predictions of the model trained on raw data (no feature engineering) gained really bad results on the leaderboard. 

### What was the top ranked model that performed?
The Autogluon performs multiple models to maximize the metric of a specific task. In my task with raw data, the WeightedEnsemble model has gained the best result on score_val. The WeightedEnsemle method is a machine learning technique that combines several weak learners in order to produce one optimal predictive model. I think that is one of the reasons the WeightedEnsemble model is the best models for this task.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
EDA:
+ Categorical features: holiday, season, workingday, weather. There are some categorical features that is encoded by label encoding method. I think that is not good for the Autogluon framework because of the good ability to detect the type of features and automatic transformation before training models.
+ Numerical features: temp, atemp, humidity, windspeed
+ I saw the DateTime column that gives the time-series property of the dataset. However, I am solving this challenge as regression problems with tabular data

So:
+ I add extract some useful features from datetime feature: hour, date, year, month
+ Add weekday feature because I think the number of registered bikes depends on the weekday. 
+ Decoding features that are encoded above.
### How much better did your model preform after adding additional features and why do you think that is?
I have achieved 1.4 lower scores after adding additional features. It is a good result with some additional features.
Some reasons I explained in the previous question.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Actually, I haven't archived better result than adding addtional features. I think I need to deep into the models of the autogluon framework: how it works, ideal and methodology of models 

### If you were given more time with this dataset, where do you think you would spend more time?
I take into account:
+ perform multiple rounds of hyperparameter tunning.
+ tweak hyperparameter of each model
+ add more usefull features.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hyperparameters|num_trials|search_strategy|score|
|--|--|--|--|--|
|initial|default|None|None|1.80659|
|add_features|default|None|None|0.47442|
|hpo|very_light|5|random|0.51008|

### Create a line plot showing the top model score for the three (or more) training runs during the project.


![model_train_score.png](model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](model_test_score.png)

## Summary
In this project, I have used the Autogluon framework to predict bike sharing demand. I see that it is a very useful framework for a newbie or non-expert Data scientist to start solving machine learning relevant problems or to make the first reference results. However, It also regards a black box if the users do not have deep knowledge about models in the framework. So, I think we need good background knowledge about ML's algorithms as Linear Regression, Logistic Regression, Tree-based algorithms, Neural Network, Ensemble techniques before use it.