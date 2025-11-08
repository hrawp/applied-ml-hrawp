# Project 3: Titanic Dataset Analysis
**Author:** AARON 
**Date:** November, 4, 2025 
**Objective:** Setup three model types, Decision Tree, Support Vector Machine, and Neural Network and use these to predict survival rate on the Titanic dataset.

## Introduction
This project uses the Titanic dataset to Explore and Clean data, choose a feature to predict, and split the dataset into train and test subsets.
Setup three model types, Decision Tree, Support Vector Machine, and Neural Network and use these to predict survival rate on the Titanic dataset.  I use three differet test cases with specific features of 'alone', 'age', and 'age' + 'family size'. Compare the output of these models and test cases against the others and see which, if any, predict survival rate better.

## Section 3. Feature Selection and Justification
### 3.1 Choose features and target

Select two or more input features (numerical for regression, numerical and/or categorical for classification)
Use survived as the target. 
We will do three input cases like the example. 

Case 1: 
input features: alone
target: survived

Case 2:
input features - age
target: survived

Case 3:
input features -  age and family_size 
target: survived

### Reflection 3:

Why are these features selected?  These were selected based on reviewing the overview of the data.
Are there any features that are likely to be highly predictive of survival?  I think age will be the most predictive.

### 4.3 Predict and Evaluate Model Performance (Decisiont Tree)


| Model Type    | Case   | Features Used     | Accuracy | Precision | Recall | F1-Score  | Notes |
|---------------|--------|-------------------|----------|-----------|--------|-----------|-------|
| Decision Tree | Case 1 | alone             | 63%      | 64%       | 63%    | 63%       | -     |
|               | Case 2 | age               | 61%      | 58%       | 61%    | 55%       | -     |
|               | Case 3 | age + family_size | 59%      | 57%       | 59%    | 58%       | -     |

### Reflection 4:
How well did the different cases perform?  I for sure could see a disitction with the feaure 'alone' showing the best results.
Are there any surprising results?  I was very suprised to see the 'alone' feature being a better predictor of survival than the age based features.
Which inputs worked better? The 'alone' input worked the best.

## Section 5. Compare Alternative Models (SVC, NN)


| Model Type           | Case   | Features Used     | Accuracy | Precision | Recall | F1-Score  | Notes |
|----------------------|--------|-------------------|----------|-----------|--------|-----------|-------|
| Decision Tree        | Case 1 | alone             | 63%      | 64%       | 63%    | 63%       | -     |
|                      | Case 2 | age               | 61%      | 58%       | 61%    | 55%       | -     |
|                      | Case 3 | age + family_size | 59%      | 57%       | 59%    | 58%       | -     |
|----------------------|--------|-------------------|----------|-----------|--------|-----------|-------|
| SVM (RBF Kernel)     | Case 1 | alone             | 63%      | 64%       | 63%    | 63%       | -     |
|                      | Case 2 | age               | 63%      | 66%       | 63%    | 52%       | -     |
|                      | Case 3 | age + family_size | 63%      | 66%       | 63%    | 52%       | -     |
|----------------------|--------|-------------------|----------|-----------|--------|-----------|-------|
| Neural Network (MLP) | Case 1 | alone             | ---      | ----      | ---    | --        | -     |
|                      | Case 2 | age               | ---      | ----      | ---    | --        | -     |
|                      | Case 3 | age + family_size | 66%      | 65%       | 66%    | 65%       | -     |


### Reflection 5:
How well did each of these new models/cases perform?  'The 'alone' case again performed the best in the SVM model type.  But the distinction between the three SVM cases narrowed as compared to the Decision Tree.  The Neural Network outperformed every other model.
Are there any surprising results or insights?  I am surprised case 3 was so much better than the same case in the Decision Tree.
Why might one model outperform the others?  I think the Neural Network performed better since it had two variables to work with and had feedback from both into each node.

## Section 6. Final Thoughts & Insights

At first I was a little discouraged at the accuracy of the models and other parameters.  It seemed like just knowing if a passenger was alone or not told most of the tale.  But when I worked with the Neural Network I saw noticeable improvement in the results.  I was glad to see that.  These differences can be seen in the table below.
I look forward to using Neural Networks in the future for classification models.