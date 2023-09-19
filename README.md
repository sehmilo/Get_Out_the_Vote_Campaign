# Get_Out_the_Vote_Campaign

# Introduction

Prediction is an important part of spatial data science. You can use prediction to forecast future values (for example, predicting tomorrow's air quality for a specified location), downscale information (for example, using voter turnout data at the county level to predict voter turnout at the census tract level), or fill in missing values in a dataset.

ArcGIS provides various prediction tools to help complete these types of analyses. In this exercise, the Forest-based Classification and Regression tool is used, which uses an adaptation of Leo Breiman's random forest algorithm. This supervised machine learning algorithm allows you to use existing data to train models that may be useful for predictive analysis.

The tool creates many decision trees, called an ensemble or a forest, that are used for prediction. Each tree generates its prediction and is used as part of a voting scheme to make final predictions. The strength of the forest-based method is in capturing commonalities of weak predictors (the trees) and combining them to create a powerful predictor (the forest). The Random forest tool is used here to train and evaluate a predictive model, modifying variables and parameters to improve the model performance.

# Scope

The aim is to create models that predict voter turnout. These models will use explanatory variables, such as income and age, to predict the dependent variable, which is voter turnout.

You will use this model to downscale voter turnout from the county level to the census tract level. This information will be used to organize a "Get Out the Vote" canvassing campaign. These campaigns encourage people to vote on Election Day. This model will help identify local regions expected to have low voter turnout so that you know where to target your campaign.

The data and exercise are part of ESRI's MOOC Exercise on Predictions, Spatial Data Science: The New Frontier in Analytics.


Forest-based Classification and Regression
=====================
Parameters

Prediction Type     TRAIN
Input Training Features     CountyElections2020
Variable to Predict     voter_turnout_2020
Treat Variable as Categorical     
Explanatory Training Variables     gender_MEDAGE_CY false;householdincome_PCI_CY false;educationalattainment_SOMEHS_CY_P false
Explanatory Training Distance Features     
Explanatory Training Rasters     
Input Prediction Features     
Output Predicted Features     
Output Prediction Surface     
Match Explanatory Variables     
Match Distance Features     
Match Explanatory Rasters     
Output Trained Features     C:\EsriTraining\Prediction\Prediction_Data.gdb\Out_Trained_Features
Output Variable Importance Table     C:\EsriTraining\Prediction\Prediction_Data.gdb\Out_Variable_Importance_Table
Convert Polygons to Raster Resolution for Training     TRUE
Number of Trees     100
Minimum Leaf Size     
Maximum Tree Depth     
Data Available per Tree (%)     100
Number of Randomly Sampled Variables     
Training Data Excluded for Validation (%)     10
Output Classification Performance Table (Confusion Matrix)     
Output  Validation Table     
Compensate for Sparse Categories     FALSE
Number of Runs for Validation     1
Calculate Uncertainty     FALSE
Output Uncertainty Raster Layers     
Output Trained Model File     
=====================
Messages

Start Time: Tuesday, September 19, 2023 6:05:54 AM
Random Seed: 496184
![Model Characteristics](/Images/Model_characteristics_training.png)
![Model out of Bag Erro and Top Variable Importance](/Images/Model_out_of_bag__Top_Variable.png)
By default, forest-based classification and regression reserves 10 percent of the data for validation. The model is trained without this random subset, and the tool returns an R-squared value that measures how well the model performed on the unseen data.

When a model is evaluated based on the training dataset rather than a validation dataset, it is common for estimates of performance to be overstated due to a concept called overfitting. Therefore, the validation R-squared value is a better indicator of model performance than the training R-squared value. The model returned a validation R-squared value of 0.456, indicating that the model predicted the voter turnout value in the validation dataset with an accuracy of about 45 percent.
![Training Data: Regression Diagnostics and Validation Data: Regression Diagnostics](/Images/TrainingValidation_RegressionDiagnostics.png)
![Expplanatory Variable Range](/Images/Explanatory_Variable_Range_Diagnostics.png)
![alt text](image.jpg)
