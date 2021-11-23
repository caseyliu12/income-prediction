# Team pd.read_csr('Casey_Spencer_Robb')

## Problem Statement

Given a limited csv file that contained fewer than 20 features, can we create a model that accurately predicts whether someone has an income over $50,000.

## Process

Initially, we checked the baseline accuracy rate of .7592, which meant that if we predicted that income was below $50,000, we would be correct 75.92% of the time.

Next, we determined that there were no null values in any of the features, and that all feature data types seemed correct based on the data dictionary provided. Since all of this seemed correct, there was little data cleaning to perform.

Then, since there was little data cleaning and several relevant features that were object data types, we created dummy variables of all the object columns. We then checked the correlations in a heatmap to see if there were any signal features. We saved this as a new csv file for all team members to share.

After creating the new csv, we delegated each team member to grid search different models to find the best parameters for each model. Spencer took Logistic Regression. Casey took Random Forest. Robb took Gradient Booster and KNN. After discovering the best parameters for each model, we then created a stacked model that contained each model. We then also tested which of the 4 models was best as the final estimator. We discovered that Logistic Regression as the final model gave the best cross val score.

![](./Visuals/logregstackedmatrix.png)

We then plotted a confusion matrix and looked at the accuracy, sensitivity, specificity, precision, and f1 scores for the stacked model. We also plotted a ROC AUC curve, which had a high score of .92, suggesting that the positive and negative populations had relatively little overlap. 

![](./Visuals/logregstackcurve.png)

We believed, however, that the false negatives from our model were too high, causing our sensitivity score to be low. We wanted to better this score so we optimized the model for sensitivity and raised our sensitivity score from .612 to .752, meaning that we lowered the number of false negatives. This had the effect of reducing the precision score, but the drop was less than the amount gained in the sensitivity score, so we determined that optimizing the model in this way had an overall positive effect.

![](./Visuals/scoredistribution.png)

## Conclusion

Our best model is the stacked logistic regression model that produced an accuracy of 86%, which beat the baseline accuracy score of 75.92%. When we optimized for sensitivity, we also increased the effectiveness of the model.
