# Get_Out_the_Vote_Campaign

# Introduction

Prediction is an important part of spatial data science. You can use prediction to forecast future values (for example, predicting tomorrow's air quality for a specified location), downscale information (for example, using voter turnout data at the county level to predict voter turnout at the census tract level), or fill in missing values in a dataset.

ArcGIS provides various prediction tools to help complete these types of analyses. In this exercise, the Forest-based Classification and Regression tool is used, which uses an adaptation of Leo Breiman's random forest algorithm. This supervised machine learning algorithm allows you to use existing data to train models that may be useful for predictive analysis.

The tool creates many decision trees, called an ensemble or a forest, that are used for prediction. Each tree generates its prediction and is used as part of a voting scheme to make final predictions. The strength of the forest-based method is in capturing commonalities of weak predictors (the trees) and combining them to create a powerful predictor (the forest). The Random forest tool is used here to train and evaluate a predictive model, modifying variables and parameters to improve the model performance.

# Scope

The aim is to create models that predict voter turnout. These models will use explanatory variables, such as income and age, to predict the dependent variable, which is voter turnout.

You will use this model to downscale voter turnout from the county level to the census tract level. This information will be used to organize a "Get Out the Vote" canvassing campaign. These campaigns encourage people to vote on Election Day. This model will help identify local regions expected to have low voter turnout so that you know where to target your campaign.

The data and exercise are part of ESRI's MOOC Exercise on Predictions, Spatial Data Science: The New Frontier in Analytics.

## Create Prediction Model 


Start Time: Tuesday, September 19, 2023 6:05:54 AM
Random Seed: 496184

![Model Characteristics](/Images/Model_characteristics_training.png)

![Model out of Bag Erro and Top Variable Importance](/Images/Model_out_of_bag__Top_Variable.png)

By default, forest-based classification and regression reserves 10 percent of the data for validation. The model is trained without this random subset, and the tool returns an R-squared value that measures how well the model performed on the unseen data.

When a model is evaluated based on the training dataset rather than a validation dataset, it is common for estimates of performance to be overstated due to a concept called overfitting. Therefore, the validation R-squared value is a better indicator of model performance than the training R-squared value. The model returned a validation R-squared value of 0.456, indicating that the model predicted the voter turnout value in the validation dataset with an accuracy of about 45 percent.


![Training Data: Regression Diagnostics and Validation Data: Regression Diagnostics](/Images/TrainingValidation_RegressionDiagnostics.png)

![Expplanatory Variable Range](/Images/Explanatory_Variable_Range_Diagnostics.png)


Here we review how important each explanatory variable was in generating a prediction. The Out_Trained_Features layer displays the predicted voter turnout for each county in the contiguous United States. A variable importance table and associated bar chart are added to the Contents pane and can be used to explore which variables were most important in this prediction.

The 2022 Per Capita Income and 2022 Pop Age 25+: High School/No Diploma: Percent variables have the highest importance, meaning that they were the most useful in predicting voter turnout.

![Summary of Variable Importance chart](/Images/Summary Of Variable Importance chart.jpg)

As previously mentioned, each time that you run the Forest-based Classification and Regression tool, you may get slightly different results due to the randomness introduced in the algorithm. To understand and account for this variability, you will use a parameter that allows the tool to create multiple models in one run. This output will allow you to explore the distribution of model performance.

## Examine Model Stability

In this step, you will review the prediction intervals in this model to see whether the model's performance is relatively stable across all values.


Start Time: Friday, September 22, 2023 5:43:15 AM
Random Seed: 569216

The tool trained 10 models with random subsets of validation data. In the example shown here, the most representative R-squared value across the 10 runs is 0.487, corresponding to about 48 percent accuracy in prediction of the validation data. You can use a histogram to review the distribution of R-squared values returned over the 10 runs.


In the Contents pane, in the Standalone Tables section, open the Validation R2 chart.

![Validation R2 chart](/Images/validation R2.jpg)

The histogram shows the variability in model performance by visualizing the distribution of R-squared values returned over the 10 runs. The mean R-squared value for the 10 runs of this model is 0.487

In the Contents pane, open the Distribution Of Variable Importance chart.

![Distribution of Variable Importance chart](/Images/Distribution of variable importance.jpg)


Instead of a bar chart, the variable importance is visualized using a box plot to show the distribution of importance across the 10 runs of the model. In some runs of the model, Per Capita Income was more important, and in other runs, Pop Age 25+: High School/No Diploma: Percent was also important. Overall, both variables are strong candidates for the predictive model.

For prediction interval

![Prediction Interval](/Images/Prediction interval.jpg)

The Prediction Interval chart displays the level of uncertainty for any given prediction value. By considering the range of prediction values returned by the individual trees in the forest, prediction intervals are generated, indicating the range in which the true value is expected to fall. You can be 90 percent confident that new prediction values generated using the same explanatory variables would fall in this range. This chart can help you identify whether the model is better at predicting some values than others. For example, if the confidence intervals were much larger for low voter turnout values, then you would know that the model is not as stable for predicting low voter turnout as it is for predicting high voter turnout. The prediction intervals in this model are fairly consistent, indicating that the model performance is relatively stable across all values.


Random Seed: 484451


Median R2 0.514 was approximately reached at seed 780081


Succeeded at Friday, September 22, 2023 5:45:30 AM (Elapsed Time: 2 minutes 14 seconds)

At this point, the attributes in the dataset were used as the explanatory variables in the model.

## Adding many variables to the model

The Forest-based Classification and Regression tool uses a random subset of the available explanatory variables in each decision tree. Commonalities in the predictions and variables used among all the trees in the forest are quantified in the variable importance diagnostic. In general, that means that you can test adding variables to the model without diminishing the model's predictive power. Variables that are useful result in higher variable importance scores, and variables that are not useful result in lower variable importance scores.

In this step, variables are added to the model to see if they enhance model's performance for predicting voter turnout.
Many variables are now added as explanatory training variables. Voter turnout for 2020 is the variable that you are trying to understand, and the same variable should not be used as both the independent and dependent variables for this analysis. The Forest-based Classification and Regression tool can also use categorical variables, which are variables of a string field type instead of a numeric field type. The State_Abbr and the 2022 Dominant LifeMode Grp Code variables are both marked as categorical variables in the Explanatory Training Variables list.

Reviewing the R-squared value in the validation data regression diagnostics.
![R-squared validation data regression](/Images/validation R2_manyVAR.jpg)


In this example, the model's R-squared value increased to 0.879, which means that it is now predicting with almost 88 percent accuracy based on the validation data. 

Slightly different results may arise due to the randomness introduced in the algorithm to prevent the model from overfitting to the training data. 
The more categories that a variable contains, the more likely it is that the variable will dominate the model and lead to less effective prediction results. When selecting variables for your model, consider this effect on results.


Reviewing the Distribution Of Variable Importance chart.

![Distribution of Variable Importance](/Images/Summary Of Variable Importance chart_manyVAR.jpg)


The voter turnout variables have the highest variable importance in the model, but several new variables have contributed to the model and raised its performance. There are also several variables that may not be helping the model, represented by their low variable importance.

With the Forest-based Classification and Regression tool, you can also calculate new variables based on distances to meaningful locations. In the next step, I will calculate distance variables and assess their importance to the model.

