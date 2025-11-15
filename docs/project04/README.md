# Project 4 - Predicting a Continuous Target with Regression (Titanic)
**Author:** AARON 
**Date:** November 14, 2025 
**Objective:** Gain an understanding of four types of regression models and their characteristics.


## Introduction
- Using the Titanic dataset four use cases with linear regression will be explored.  The fourth case will have an engineered feature.  The best performing case will be used to see how four different regression models predict the values of fare price from the Titanic dataset.  This exercise should give some insights into how these four model types behave.


## Section 3. Feature Selection and Justification
### 3.1 Choose features and target


Case 1: 
input features: 'Age'
target: fare

Case 2:
input features - 'Family Size'
target: fare

Case 3:
input features -  'Age' and 'Family Size'
target: fare

Case 4:
input features -  'Class Survive' and 'Family Size'
target: fare

### Reflection 2 and 3:
- Why might these features affect a passenger’s fare:   I'm not sure age would help determine fare much except for younger children.  Family size would have some bearing as they could buy at a group rate.  
- List all available features:  survived, pclass, sex, age, sibsp, parch, embarked, class, who, adult_male, deck, embark_town, alive, alone 
- Which other features could improve predictions and why:  I think class is the main determining factor on fare. 
- How many variables are in your Case 4:  Three.  I combined class and survived to produce a number between -3 and 0.  I also have family size.
- Which variable(s) did you choose for Case 4 and why do you feel those could make good inputs:  I don't know for sure, but fare may have had an impact on who survived.  I am combining that with class to get two variable into one.  It also weights the equation nicely.  I'm real excited to see how this predicts the result.

### Reflection 4:
Compare the train vs test results for each.


| Model Type    | Case   | Features Used                 | Training R² | Test R²   | RMSE    | MAE    | Notes |
|---------------|--------|-------------------------------|-------------|-----------|---------|--------|-------|
| Decision Tree | Case 1 | Age                           | 0.0099      | 0.0034    | 1441.84 | 25.28  | -     |
|               | Case 2 | Family Size                   | 0.0499      | 0.0222    | 1414.62 | 25.02  | -     |
|               | Case 3 | Age, Family Size              | 0.0734      | 0.0497    | 1374.76 | 24.28  | -     |
|               | Case 4 | Family Size, Survived, Class  | 0.3293      | 0.4128    | 849.46  | 19.76  | -     |


- Did Case 1 overfit or underfit? Explain:  Case 1 is an underfit.  R2 are very low.
- Did Case 2 overfit or underfit? Explain:  Case 2 is an underfit.  The is a small improvement, but R2 are very low.
- Did Case 3 overfit or underfit? Explain:  Case 3 is an underfit.  The is a small improvement, R2 are very low.
- Did Case 4 overfit or underfit? Explain:  Case 4 is not overfit or underfit.  It's odd that the test set did better, but that does not mean it's overfit.

### Adding Age

- Did adding age improve the model: The model improved slightly from Case 2 to Case 3.
- Propose a possible explanation (consider how age might affect ticket price, and whether the data supports that):  I think age coupled with family size would improve where an entry was a child who was part of a family.  The fare price for the family would account for that.

### Worst

- Which case performed the worst: Case 1 - Age
- How do you know: The R2 value was almost 0.
- Do you think adding more training data would improve it (and why/why not):  I don't think adding more training data would help.  Age does not make a meaningful impact.

### Best

- Which case performed the best: Case 4 - Family Size, Class + Survived
- How do you know: The R2 was 10 times better. and the RMSE and MAE we noticeable lower.
- Do you think adding more training data would improve it (and why/why not):  I'm not sure.  In my case the test set performed better than the training set.  So it makes me think I had a good split or I maxed out any training data.

### 5.4 Reflections (in a Markdown cell):
- What patterns does the cubic model seem to capture:  For smaller family sizes it predicted lower fare values.
- Where does it perform well or poorly:  It does a little better than a straight linear line does when the family size is bigger.
- Did the polynomial fit outperform linear regression: Yes the R2 value 0.088 for poly but 0.022 for Linear.
- Where (on the graph or among which kinds of data points) does it fit best:  The prediction is best for two family members.  Followed by alone and then three family members.

| Model Type    | Case   | Features Used                 | Test R²   | RMSE    | MAE    | Notes |
|---------------|--------|-------------------------------|-----------|---------|--------|-------|
| Linear        | Case 2 | Family Size                   | 0.022     | 1414.62 | 25.02  | -     |
| Poly Cubic    | Case 2 | Family Size                   | 0.088     | 1319.24 | 24.07  | -     |


### Cubic vs 5th Order Polynomial Comparison 

- The 5th order Polynomial underperforms the cubic Polynominal model because it shows as almost a straight line for the first six family number values.  It is almost linear for those first six feature points.  The last two feature points it dropped aggressively which did not really help the prediction.  
- Although the Cubic Polynomial was not great, it did better than linear and the 5th order.  The main reason is seen by the prediction line bending after feature point three instead of a steady slope up which does not correspond to the actual outcomes.


| Model Type      | Case   | Features Used                 | Test R²  | RMSE   | MAE    | Notes |
|-----------------|--------|-------------------------------|----------|--------|--------|-------|
| Linear          | Case 4 | Family Size, Class + Survived | 0.413    | 849.46 | 19.77  | -     |
| Ridge Case      | Case 4 | Family Size, Class + Survived | 0.413    | 849.11 | 19.75  | -     |
| ElasticNet      | Case 4 | Family Size, Class + Survived | 0.429    | 825.78 | 18.18  | -     |
| Polynomial Cubic| Case 4 | Family Size, Class + Survived | 0.469    | 768.20 | 15.49  | -     |
| Polynomial Cubic| Case 2 | Family Size                   | 0.088    | 1319.24| 24.07  | -     |
| Poly 5th Order  | Case 2 | Family Size                   | 0.065    | 1352.24| 24.34  | -     |



## Section 6. Final Thoughts & Insights

### 6.1 Summarize Findings


- What features were most useful?  The engineered feature class and survival had the largest positive effect on predicting fare.

- What regression model performed best?  The Polynomial Cubic Model iterated on Case 4 had the best metrics. Yet, I don't think it is the best model.  I had a hard time visualizing these models.  I added a "residuals" graphic to each of Case 4 models.  
- The goal is to have it evenly distributed around 0 all the way through the range with as little amplitude as possible.
- The first three models had that characteristic for 2/3 of the range and then started having higher amplitudes at the larger fare values.
However, the Polynomial Cubic Model had only three areas with very high amplitude.  This leads me to believe that it has overfitted the training data and that Ridge or ElasticNet should be used. 

- How did model complexity or regularization affect results?  I think regularization had some positive effect, but it was pretty minor.  I was a little disappointed Ridge and ElasticNet did not have a higher impact.  I suspect the input features would need to be adjusted for more of a step function change.
  
- Further Discussion:  I chose to combine class and survived as a engineered feature.  After doing some more reading that may have a causality type effect.  I'll need to keep an eye out for this in the future, but I feel like the use of both here enhanced the prediction without causing a causality type effect.

### 6.2 Discuss Challenges
- Was fare hard to predict? Why?  Fare was hard to predict with the given inputs.  There was a very low R2 value for Age, Family Size, and even for Age and Family Size engineered parameter.  Class really is what helped the models perform up to 10 times better when coupled with Family Size. 

- Did skew or outliers impact the models?  Outliers had a decided effect on the models.  A few points were so high with no real basis in the features used in the models.

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