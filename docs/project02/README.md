# Project 02

# Titanic Dataset Analysis
**Author:** AARON 
**Date:** October, 29, 2025 
**Objective:** Untilize the first four steps in the model creation process with the Titanic dataset.

## Introduction
- This project uses the Titanic dataset to Explore and Clean data, choose a feature to predict, and split the dataset into train and test subsets.

### Note: 
- I think it is appropriate to have data examples and graphs in the notebook rather than copying into the README.  - Here I include the oultine of the project and reflections for summaries.

## Include Imports
## Section 1. Load and Explore the Data

### 1.1 Load the dataset and display basic information

### 1.2 Check for missing values and display summary statistics

## Section 2. Data Exploration and Preparation
### 2.1 Explore Data Patterns and Distributions


### Reflection 2.1:


- What patterns or anomalies do you notice?  
    1. There were a lot of very young children aboard.  
    2. There must have been some reason third class had such a high mortality rate.
- Do any features stand out as potential predictors? It looks like higher fares were paid by women.
- Are there any visible class imbalances? Younger people appear to be in third class.


### 2.2 Handle Missing Values and Clean Data

### 2.3 Feature Engineering

### Reflection 2.3
- Why might family size be a useful feature for predicting survival?  
  - This may help if a families were together.  I suspect there were seperations though.
- Why convert categorical data to numeric? It helps for mathematical cacluations for models and one-hop encoding.

## Section 3. Feature Selection and Justification
### 3.1 Choose features and target

### 3.2 Define X and y
- Input features: age, fare, pclass, sex, family_size
- Target: survived

### Reflection 3:

- Why are these features selected?  These were determined in anaylsis above to have an impact.
- Are there any features that are likely to be highly predictive of survival?  I think class and sex will be the most predictive.

## Section 4. Splitting
 

- Split the data into training and test sets using train_test_split first and StratifiedShuffleSplit second. Compare.

### 4.1 Basic Train/Test split

Original Class Distribution:

- Class 3    0.551066
- Class 1    0.242424
- Class 2    0.206510

Train Set Class Distribution:

- Class 3    0.557584
- Class 1    0.233146
- Class 2    0.209270

Test Set Class Distribution:

- Class 3    0.525140
- Class 1    0.279330
- Class 2    0.195531


### 4.2 Stratified Train/Test split

Original Class Distribution:

- Class 3    0.551066
- Class 1    0.242424
- Class 2    0.206510

Train Set Class Distribution:

- Class 3    0.561798
- Class 1    0.227528
- Class 2    0.210674

Test Set Class Distribution:

- Class 3    0.508380
- Class 1    0.301676
- Class 2    0.189944


### 4.3 Compare Results

### 4.4 Reflection 4

- Why might stratification improve model performance?  I don't think stratification would improve model performance.  It looks to have a distribution less like the original class distribution than the basic class distribution. 
- How close are the training and test distributions to the original dataset?  The stratisfied results look farther away from the original distribution for both the training and test set disbributions as compared to the basic one.
- Which split method produced better class balance?  The basic Train method looks to have a better class distribution to the original class distribution.




