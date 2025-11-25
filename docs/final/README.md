# Final - Predicting a Continuous Target with Regression (Medical Cost)
**Author:** AARON 
**Date:** November 24, 2025 
**Objective:** Create a Regression Model to predict Medical Claims data.

## Introduction
- Using the Medical Cost Personal Dataset, decide what inputs to use in Regression model to predict Medical Claims.
- Try alternate methods or engineered variables to find an optimal model.

## Section 1. Import and Inspect the Data
### Reflection 1: 
What do you notice about the dataset? The dataset is fully populated with 1338 records.
Are there any data issues?  There were no missing values.

## Section 2. Data Exploration and Preparation

## Section 3. Feature Selection and Justification
### Reflection 2 and 3:
- This dataset just had a handful of inputs to choose from.  I elected to add age and bmi then multiply that sum by 3 if a smoker as case 2.
- I also decided to include all inputs in case 1 to compare the results to my single engineered input.
  
## Section 4. Train a Regression Model (Linear Regression)
### Reflection 4:
Compare the train vs test results for each.


| Model Type        | Case   | Features Used                 | Training R² | Test R²   | RMSE     | MAE    | Notes |
|-------------------|--------|-------------------------------|-------------|-----------|----------|--------|-------|
| Linear Regression | Case 1 | all features                  | 0.7376      | 0.8001    | 30552437 | 4013   | -     |
| Linear Regression | Case 2 | 3ptindex                      | 0.7454      | 0.8247    | 26792600 | 3659   | -     |

![Linear Regression - Case 2](3ptindex.JPG)

- Did Case 1 overfit or underfit? Case 1 is in the nominal range.
- Did Case 2 overfit or underfit? Case 2 is in the nominal range.


### Adding Age + BMI * (2 * Smoker + 1)

- Did adding 3pt index improve the model: The model improved measurably from Case 1 to Case 2.
- Propose a possible explanation (consider how age might affect ticket price, and whether the data supports that):  The 3ptindex formula keeps non-smoker claims as is in determining claims.  But if someone is a smoker it amplifies the age and bmi by 3 times.  This helps the linear regression with these higher values.  
- At first I just had 2 times, but I tried 3 times and the results were better.  
- I did not need to use the other parameters either and still achieved better results.
- I wanted just a single variable to see the plot and in some ways stumbled into a great model.

## Section 5. Compare Alternative Models

### 5.5 Reflection
- What patterns does the cubic model seem to capture:  It is very hard to know for case 1 with all the inputs.  For case 2 it matched the data slightly better than linear regression.
- Where does it perform well or poorly:  According to the residuals plot the result is very balanced for case 1.  I see some values on both sides of zero which is desirable. For case 2, there is still some balance, but it is not quite as good as case 1.
- Did the polynomial fit outperform linear regression: Yes the R² value 0.888 for poly but 0.80 for Linear for case 1.  For case 2 the results were almost the same.
- Where (on the graph or among which kinds of data points) does it fit best:  The prediction works well for smokers and non-smokers for case 1 and case 2. 

| Model Type    | Case   | Features Used                 | Test R²   | RMSE     | MAE    | Notes |
|---------------|--------|-------------------------------|-----------|----------|--------|-------|
| Linear        | Case 1 | All Inputs                    | 0.800     | 30552437 | 4013   | -     |
| Poly Cubic    | Case 1 | All Inputs                    | 0.888     | 17093508 | 2772   | -     |
| Linear        | Case 2 | 3ptindex                      | 0.825     | 26792600 | 3659   | -     |
| Poly Cubic    | Case 2 | 3ptindex                      | 0.824     | 26873381 | 3686   | -     |

![Polynomial Cubic - Case 2](poly_3ptindex.JPG)

### 5.6 Compare All Models
All Models
| Model Type    | Case   | Features Used                 | Test R²   | RMSE     | MAE    | Notes |
|---------------|--------|-------------------------------|-----------|----------|--------|-------|
| Linear        | Case 1 | All Imputs                    | 0.800     | 30552437 | 4013   | -     |
| Ridge         | Case 1 | All Imputs                    | 0.800     | 30632410 | 4025   | -     |
| ElasticNet    | Case 1 | All Imputs                    | 0.610     | 59577764 | 5621   | -     |
| Poly Cubic    | Case 1 | All Imputs                    | 0.888     | 17093508 | 2772   | -     |
| Linear        | Case 2 | 3ptindex                      | 0.825     | 26792600 | 3659   | -     |
| Poly Cubic    | Case 2 | 3ptindex                      | 0.824     | 26873381 | 3686   | -     |

### Reflection 5.7:
- There was just one model that outperformed and that was Polynomial Cubic on Case 1.  It did much better than all other models.  I'm not sure why as it is hard to visualize the data.
- The other models did not perform better than Linear Regression on Case 1.  
- The Polynomial Cubic on Case 2 was slightly underperforming the Linear Regression on Case 2.

## Section 6. Final Thoughts & Insights

### 6.1 Summarize Findings


- What features were most useful?  The engineered feature 3ptindex was a very powerful predictor of claims.

- What regression model performed best?  The Polynomial Cubic Model iterated on Case 1 had the best metrics.  The next best model was Case 2 and a simple Linear Regression.  It performed better than all of Case 1 except the Polynomial Cubic Model, and case 1 had all the inputs whereas Case 2 just had the single 3ptindex input.  
- You could see this in the residual graphics.  The Case 1 Cubic Model did have a quality distribution in the residual graphic.  To the eye the Case 2 Linear Model had the next best residual graphic.  Meaning the data points were around the zero line and not all on one side.  One also wants to see the points close to 0.

### 6.2 Discuss challenges faced.
- I had a hard time visualizing all the inputs for case 1.  That is what drove me to find one variable so I could see the regression line and polynomial cubic line.
- It was a challenge finding a single engineered variable that described the data.  But I did, and I am very pleased with the results.  It performed better that most of the models with all the inputs.

### 6.3 If you had more time, what would you try next?
- I would try adding more inputs to Case 2. 
- I would try Ridge Regression and ElasticNet, but try varying the parameters.  
- I also would try voting.

### Code
- The notebook for this project can be found at: https://github.com/hrawp/applied-ml-hrawp/blob/main/notebooks/final/regression_aaron.ipynb

## Peer Review
- I reviewed Alissa Beaderstadt's Midterm Project.  The review can be found at: [Beaderstadt UCI Mushroom Dataset](https://github.com/hrawp/applied-ml-hrawp/blob/main/docs/midterm/peer_review.md)

## How to Run the Jupyter Notebook

This Jupyter Notebook utilizes some packages in the uv environment and will install some dependencies.  The following set of commands would help you complete these two objectives. 

```shell
uv venv
uv python pin 3.12
uv sync --extra dev --extra docs --upgrade
uv run python --version
```

**Windows (PowerShell):**

```shell
.\.venv\Scripts\activate
```

**macOS / Linux / WSL:**

```shell
source .venv/bin/activate
```

There are imports at the top of the Jupyter Notebook that should also be run to utilize the installed software and run the code in the rest of the Jupyter Notebook.
