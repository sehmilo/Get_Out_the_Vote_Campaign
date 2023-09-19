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
json:
[{"element": "table", "data": [["Number of Trees", "100"], ["Leaf Size", "5"], ["Tree Depth Range", "20-32"], ["Mean Tree Depth", "25"], ["% of Training Available per Tree", "100"], ["Number of Randomly Sampled Variables", "1"], ["% of Training Data Excluded for Validation", "10"]], "elementProps": {"striped": "true", "noHeader": true, "title": "Model Characteristics", "0": {"align": "left", "pad": "0px", "wrap": true}, "1": {"align": "right", "pad": "0px", "wrap": true}}}]
json:
[{"element": "table", "data": [["Number of Trees", "50", "100"], ["MSE", "0.005", "0.005"], ["% of variation explained", "43.318", "45.994"]], "elementProps": {"striped": "true", "noHeader": true, "title": "Model Out of Bag Errors", "0": {"align": "left", "pad": "0px", "wrap": true}, "1": {"align": "right", "pad": "0px", "wrap": true}, "2": {"align": "right", "pad": "0px", "wrap": true}}}]
json:
[{"element": "table", "data": [["Variable", "Importance", "%"], ["2022 Per Capita Income", "9.33", "38"], ["2022 Pop Age 25+: High School/No Diploma: Percent", "7.99", "33"], ["2022 Median Age", "7.10", "29"]], "elementProps": {"striped": "true", "title": "Top Variable Importance", "0": {"align": "left", "pad": "0px", "wrap": true}, "1": {"align": "right", "pad": "0px", "wrap": true}, "2": {"align": "right", "pad": "0px", "wrap": true}}}]
json:
[{"element": "table", "data": [["R-Squared", "0.896"], ["p-value", "0.000"], ["Standard Error", "0.005"]], "elementProps": {"striped": "true", "noHeader": true, "footnote": ["*Predictions for the data used to train the model compared to the observed categories for those features"], "title": "Training Data: Regression Diagnostics", "0": {"align": "left", "pad": "0px", "wrap": true}, "1": {"align": "right", "pad": "0px", "wrap": true}}}]
json:
[{"element": "table", "data": [["R-Squared", "0.456"], ["p-value", "0.000"], ["Standard Error", "0.033"]], "elementProps": {"striped": "true", "noHeader": true, "footnote": ["*Predictions for the test data (excluded from model training) compared to the observed values for those test features"], "title": "Validation Data: Regression Diagnostics", "0": {"align": "left", "pad": "0px", "wrap": true}, "1": {"align": "right", "pad": "0px", "wrap": true}}}]

json:
[{"element": "table", "data": [[{"data": "Variable", "prop": {"rowspan": 2}}, {"data": "Training", "prop": {"colspan": 2}}, {"data": "Validation", "prop": {"text-align": "left", "colspan": 2}}, {"data": "Share", "prop": {"colspan": 2}}], ["Minimum", "Maximum", "Minimum", "Maximum", {"data": ["Training", {"element": "sup", "data": "a"}], "prop": {"text-align": "right"}}, ["Validation", {"element": "sup", "data": "b"}]], ["2022 Median Age", "22.30", "64.60", "25.20", "59.10", "1.00", "0.80*"], ["2022 Per Capita Income", "12514.00", "85462.00", "12749.00", "85173.00", "1.00", "0.99*"], ["2022 Pop Age 25+: High School/No Diploma: Percent", "0.63", "33.77", "1.09", "24.82", "1.00", "0.72*"]], "elementProps": {"striped": "true", "footnote": ["(a) % of overlap between the ranges of the training data and the input explanatory variable", "(b) % of overlap between the ranges of the validation data and the training data", "*  Data ranges do not coincide. Training or validation is occurring with incomplete data.", "+  Ranges of the training data and prediction data do not coincide and the tool is attempting to extrapolate."], "title": "Explanatory Variable Range Diagnostics", "0": {"align": "left", "pad": "0px", "wrap": true}, "1": {"align": "left", "pad": "0px", "wrap": true}, "2": {"align": "left", "pad": "0px", "wrap": true}, "3": {"align": "left", "pad": "0px", "wrap": true}, "4": {"align": "left", "pad": "0px", "wrap": true}, "5": {"align": "right", "pad": "0px", "wrap": true}, "6": {"align": "right", "pad": "0px", "wrap": true}}}]
Succeeded at Tuesday, September 19, 2023 6:06:24 AM (Elapsed Time: 30.53 seconds)

