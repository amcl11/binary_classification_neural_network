# Alphabet Soup: Deep Learning Challenge


## Overview of the analysis
The purpose of this analysis is to predict whether applicants will be successful if funded by Alphabet Soup.


To do this we will use a binary classifcation neural network model. Once an initial model is built, we'll test feature engineering and hyperparameeter tuning to see if convergence of 75% is possible. 


### Data Preprocessing:
* What variable is the Dependent Variable (Target):
`IS_SUCCESSFUL`

* Which variables are the features for the model:

*(Bin numbers were experimented with a few times)*

 - `APPLICATION_TYPE` (9 Bins)  
 - `INCOME_AMT` (9 Bins)  
 - `CLASSIFICATION` (7 Bins)  
 - `ASK_AMT` (6 Bins)  
 - `USE_CASE` (4 Bins)  
 - `AFFILIATION` (3 Bins)    
 - `ORGANIZATION` (3 Bins)  


What variables should be removed from the input data because they are neither targets nor features?

 - `EIN`  
 - `NAME`  


### Compiling, Training, and Evaluating the Model
**How many neurons, layers, and activation functions did you select for your neural network model, and why?**

- Initially the number of neurons and layers was set based on the shape of the starter code output. While there doesn't seem to be an agreed-upon best practice for determining the number of neurons and layers, the initial structure served as a foundation point before experimenting with the model's architecture. One heuristic is having double the amount of neurons compared to the inputs for the first layer and then reducing the number of neurons in subsecuent layers.

- The `sigmoid` activation function was applied to the output layer for all iterations due to this being a binary classification problem.  

 - For Model 1's first and hidden layers we started with `relu` before experimenting further with `leaky relu`, `tanh`, and `sigmoid` in future models

- `tuner.search` was used to run multiple hyperparameter options to find the best model and iterate over different neurons, layers, and activation functions. 

**Were you able to achieve the target model performance?**

- I was unable to score over 75% on the validation data without overfitting the training data. 

**What steps did you take in your attempts to increase model performance?**

 - I created multiple binning options across the below categories:
 `ASK_AMT`  
 `INCOME_AMT`  
 `APPLICATION_TYPE`  
 `ORGANIZATION`  
 `USE_CASE`
 
- Additional steps included `Permutation Importance` and `Feature Interactions` to try and improve model performance. 


## Summary

**Model 1** (First Run)
 - Train Accuracy: `74.28%`
 - Validation Accuracy: `72.54%`

**Model 2** (Best Model iteration) 
 - Train Accuracy: `73.44%`
 - Validation Accuracy: `72.62%`

Model 2 performs best overall.
While its training accuracy is slightly lower than that of Model 1, its validation accuracy is marginally higher. 

A model's performance on validation data is a more reliable indicator of its ability to generalize to unseen data. Additionally, the closer training and validation accuracies are to each other, the less likely the model is overfitting. In this case, Model 2 shows a smaller gap between training and validation accuracy, suggesting it might generalize better to new data.

A recommendation for a different model could be to use an ensemble method like Random Forest. It may help with it's ability to rank feature importance and reduce overfitting. Its ensemble nature, being made up of multiple decision trees, can capture a diverse set of patterns and relationships in the data, possibly enhancing the model's predictive performance.

