# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### RENEE WATKINS

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
The negative values within the submission needed to be made equal to zero before they would be accepted. 

### What was the top ranked model that performed?
WeightedEnsemble_L2 and L3 performed best each iteration. 

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
It seems like normalizing the values, since the max and mins are so expansive, could possibly assist in the predictions' accuracy. I added additional features by parsing the datetime feature into year, month, day, and hour. 

### How much better did your model preform after adding additional features and why do you think that is?
The model actually seems to have performed worse. At first, I thought a higher score meant better performance; however, looking at the Kaggle leaderboard I see high scores around 0.3. Now I am not really sure what happened.
This is my explanation from beforehand: There was a marked difference between these iterations, with an initial score of 1.37296 and a secondary score of 1.82284. I think this is because the model was able to make predictions using more granular features including the hour, whereas prior to parsing the datetime into individual features, the model was limited to analysing the data using a single, less accurate datetime value per record in the dataset. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Using 'auto' versus 'random' HPO tuning yielded a better score. Adding additional features by parsing datetime was the most significant change, but actually reduced the Kaggle score if I understand correctly. 

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend additional time understanding each type of hyperparameter setting and how changes affect the results. This would allow me to thoughtfully tune the hyperparameters instead of guessing, which is where I am at this point. I would especially like to see how changing the ensemble weights would affect the model's accuracy since WeightedEnsemble performed the best. 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
   "model": ["initial", "add_features", "hpo", "hpo1"],
    "time_limit": [600, 600, 600, 600],
    "presents":['best_quality','best_quality', 'best_quality','best_quality'],
    "hyperparameter_tune_kwargs": ['None', 'None',{'searcher:auto','scheduler:local','num_trials:100'},{'searcher:random','scheduler:local','num_trials:100'}],
    "score": [1.37296, 1.82284, 1.83187, 1.77694]

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![Model Test Score Graph](https://github.com/remiri/MachineLearningStuff/blob/main/model_test_score.png)


### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![Model Train Score](https://github.com/remiri/MachineLearningStuff/blob/main/model_train_score.png)

## Summary
I am wondering why adding features improved the model score(6.6 from 1.7) but reduced the Kaggle score (1.4 to 1.8). Adding hyperparameter optimization kwargs also resulted in negative model scores (-37 and -36) instead of improvements, which confuses me. The Kaggle scores became larger (worse?) as well. 

