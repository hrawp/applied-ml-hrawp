# Machine Learning Final Project: Peer Review

## Project Reviewed: Regression Analysis Project
**Author:** Womenker Karto
**Date:** November 24, 2025 
**Objective:** Analyze the work done in this project and give feedback within the four sections below.

### Notebook Link:
https://github.com/wkarto/ml_regression_karto/blob/main/regression_karto.ipynb

### 1 Clarity & Organization (Is the notebook structured and easy to follow?)

I appreciated the project flow and additional subsections.  Quality detail was provided.  It was helpful to understand the project and some of the building blocks of regression.


### 2 Feature Selection & Justification (Do the chosen features make sense given the objectives?)

I may not fully understand the engineered feature bmi_smoker.  It looks like if smoker than multiply 1 * BMI which outputs BMI.  It looks like if non-smoker then multiply 0 * BMI which outputs 0.  
It may actually work though because you are just getting >0 values when a smoker.  So the models may pick up on that.

I am not sure what bmi_age_interaction, bmi_squared features were in Reflection 4.  They were not mentioned in Section 3: Feature Selection.

### 3 Model Performance & Comparisons (Are the results and comparisons clearly explained?)

The R2 value of 0.8668 is very good.  Karto's mix of inputs and engineered features worked well.  
He explains the results well.
I like how he examined the more complicated model pipelines.  Even though the results were not as good, it was good to see this data.




### 4 Reflection Quality (Are insights well thought out?)

I found the reflections very informative and helpful.  He draws some good conclusions and helps picture what this dataset has to offer in addition to making a quality prediction.