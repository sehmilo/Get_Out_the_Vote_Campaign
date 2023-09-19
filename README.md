# Get_Out_the_Vote_Campaign

# Introduction

Prediction is an important part of spatial data science. You can use prediction to forecast future values (for example, predicting tomorrow's air quality for a specified location), downscale information (for example, using voter turnout data at the county level to predict voter turnout at the census tract level), or fill in missing values in a dataset.

ArcGIS provides various prediction tools to help complete these types of analyses. In this exercise, the Forest-based Classification and Regression tool is used, which uses an adaptation of Leo Breiman's random forest algorithm. This supervised machine learning algorithm allows you to use existing data to train models that may be useful for predictive analysis.

The tool creates many decision trees, called an ensemble or a forest, that are used for prediction. Each tree generates its prediction and is used as part of a voting scheme to make final predictions. The strength of the forest-based method is in capturing commonalities of weak predictors (the trees) and combining them to create a powerful predictor (the forest). The Random forest tool is used here to train and evaluate a predictive model, modifying variables and parameters to improve the model performance.

# Scope

The aim is to create models that predict voter turnout. These models will use explanatory variables, such as income and age, to predict the dependent variable, which is voter turnout.

You will use this model to downscale voter turnout from the county level to the census tract level. This information will be used to organize a "Get Out the Vote" canvassing campaign. These campaigns encourage people to vote on Election Day. This model will help identify local regions expected to have low voter turnout so that you know where to target your campaign.

The data and exercise are part of ESRI's MOOC Exercise on Predictions, Spatial Data Science: The New Frontier in Analytics.
