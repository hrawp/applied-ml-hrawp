# Project 5 Research on Ensemble Models (Red Wine)
**Author:** AARON 
**Date:** November 19, 2025 
**Objective:** Gain an understanding of ensemble model setup and performance refinement.


## Introduction
I have three objectives in this project:
- Gain an understanding of ensemble model setup and performance refinement.  
- Compare work with other peers' research.  
- Give a summary of findings.

## Section 1. Import and Inspect the Data

## Section 2. Data Preparation

## Section 3. Feature Selection and Justification

## Section 4. Split the Data into Train and Test
 
## Section 5.  Evaluate Model Performance (Choose 2)

### 5.1a Gradient Boosting (100)
Gradient Boosting (100, 0.1) Results
Confusion Matrix (Test):
[[  0  13   0]
 [  3 247  14]
 [  0  16  27]]
Train Accuracy: 0.9601, Test Accuracy: 0.8562
Train F1 Score: 0.9584, Test F1 Score: 0.8411

### 5.1b Gradient Boosting (175)
Gradient Boosting (175, 0.03) Results
Confusion Matrix (Test):
[[  1  12   0]
 [  2 250  12]
 [  0  16  27]]
Train Accuracy: 0.9281, Test Accuracy: 0.8688
Train F1 Score: 0.9222, Test F1 Score: 0.8546

### 5.1c Reflection on Gradient Boosting
- I think a well defined improvement was made by increasing the n_estimators to 175 and decreasing the learning_rate to 0.03.  I see a Test Accuracy and Test F1 Score improvement of > 1%, an accurate prediction for one "low" classification, and a 3% drop in the Train Accuracy and Train F1 Score.  
- I gain accuracy and reduce the difference between the Train and Test metrics from 10% to 6%.  This in turn leads to less overfitting.  
- I feel this is a great addition to this model and something to keep in mind.  Namely, adjust the parameters of the model to get a good balance.

### 5.2a Voting (RF 100 + LR 1K + KNN)
Voting (RF 100 + LR 1K + KNN) Results
Confusion Matrix (Test):
[[  0  13   0]
 [  0 258   6]
 [  0  27  16]]
Train Accuracy: 0.9179, Test Accuracy: 0.8562
Train F1 Score: 0.9010, Test F1 Score: 0.8236

### 5.2b Voting (RF 100 + LR 1K + KNN)
Voting (RF 300 + LR 2K + KNN) Results
Confusion Matrix (Test):
[[  0  13   0]
 [  1 258   5]
 [  1  23  19]]
Train Accuracy: 0.9124, Test Accuracy: 0.8656
Train F1 Score: 0.8977, Test F1 Score: 0.8391

### 5.2c Reflection on Voting
- Here I found that fine tuning the parameters increased accuracy and reduced overfitting just like I saw in Gradient Boosting refinement.  It was only 1 percent, but it improved the counts in the "High" correct category by 3 so about 18%.  This is important because in a lot of cases we are trying to find what makes the wine the best.  We want to identify those high performing combinations correctly.  
- If we were just using one model instead of three I think overfitting would happen by increasing the parameters the way I did.  But according to the data, the Training Accuracy and Training F1 values went down.  This is good news for the overfitting problem.
- I also tried changing from "soft" voting to "hard" voting.  This also proved helpful.  Just going with the most vote getters instead of the probability of the three was better.

### Section 6. Compare Results 
### 6.1 Make the comparison table.
### 6.2 Comparison table for the data I studied.

| Model Type                    | Train Accuracy| Test Accuracy| Train F1 | Test F1 | Test Acc_Diff| Train-Test Acc_Diff | Train-Test F1_Diff |
|-------------------------------|---------------|--------------|----------|---------|--------------|---------------------|--------------------|
| Gradient Boosting (175, 0.03) | 0.928069	    |0.868750	   |0.922212  |0.854639	|0.012500	   |0.059319	         |0.067573     |
| Voting (RF 300 + LR 2K + KNN) | 0.912432	    |0.865625	   |0.897654  |0.839116	|0.009375	   |0.046807	         |0.058538     |
| Gradient Boosting (100, 0.1)  | 0.960125	    |0.856250	   |0.958410  |0.841106	|0.000000	   |0.103875	         |0.117304     |
| Voting (RF 100 + LR 1K + KNN) | 0.917905	    |0.856250	   |0.901043  |0.823627	|0.000000	   |0.061655	         |0.077416     |


### 6.3 Comparison table for the data I studied with additional data from Dan Miller and Megan Chastain research.
| Model Type                    | Train Accuracy| Test Accuracy| Train F1 | Test F1 | Train-Test Acc_Diff | Train-Test F1_Diff |
|-------------------------------|---------------|--------------|----------|---------|---------------------|--------------------|
| Random Forest                 | 1.0           | 0.888        | 1.0      |0.866    | 0.112               |    0.134    |
| Bagging                       | 1.0           | 0.884        | 1.0      |0.865    | 0.116               |    0.135    |
| Gradient Boosting (175, 0.03) | 0.928069	    |0.868750	   |0.922212  |0.854639	|0.059319	          |0.067573     |
| Voting (RF 300 + LR 2K + KNN) | 0.912432	    |0.865625	   |0.897654  |0.839116	|0.046807	          |0.058538     |
| Gradient Boosting (100, 0.1)  | 0.960125	    |0.856250	   |0.958410  |0.841106	|0.103875	          |0.117304     |
| Voting (RF 100 + LR 1K + KNN) | 0.917905	    |0.856250	   |0.901043  |0.823627	|0.061655	          |0.077416     |
| Voting (DT + SVM + NN)        | 0.916341      | 0.85625      | 0.897973 |0.831882 | 0.060091            | 0.066091    |
| AdaBoost                      | 0.840         | 0.856        | 0.816    |0.833    | -0.017              |   -0.017    |
| MLP Classifier                | 0.851446      | 0.84375      | 0.814145 |0.807318 | 0.007696            | 0.006827    |

### Section 7. Conclusions and Insights
- By far the biggest takeaway for me from this project is to make overfitting reduction a priority.  Second, work with parameters of the models to reduce overfitting and increase accuracy.
- I studied Gradient Boosting and Voting (RF + RL + KNN).  I found an appreciable difference in both accuracy and overfitting when I fine tuned the parameters.
- I actually would use Gradient Boosting (175, 0.03) and Voting (RF 300 + LR 2K + KNN) over any of the models I reviewed for the following reasons.  
- The Random Forest and Bagging Test and F1 Accuracy were better, but I think they were overfitting.  The difference for them both between the Train and Test Accuracy was 11.6%.  Also their Train Accuracy came in at 100%.
- In contrast, the Gradient Boosting (175, 0.03) model had a Train and Test Difference of just 6%. And Voting (RF 300 + LR 2K + KNN) came in at 5%.
- Both of these refined models had higher Test Accuracies than the other models reviewed.

### Section 8.  Next Steps
- I feel the best next step would be to review the model parameters on each of the other models.  I did not go through everyone's results to see if others did this.  I suspect Random Forest and Bagging models could have parameters changed to reduce overfitting.  I also think some of the lower performing models could be tuned to get a better test accuracy without causing overfitting.  The two models I reviewed were just par with most of the others until I dove into tuning them.
- After that, I like the voting system.  I would just add a few more in and keep an odd number.  Then I would run voting with "soft" and "hard" voting to see what did best.  I do think voting helps reduce overfitting.

### Acknowledgments:  
I referenced Dan Miller and Megan Chastain research in these results.

Dan Miller's referenced model metrics can be found in notebook:
https://github.com/DMill31/applied-ml-miller/blob/main/notebooks/project05/ensemble-miller.ipynb

Megan Chastain referenced model metrics can be found in notebook:
https://github.com/Megan-Chastain1/applied-ml-Chastain/blob/main/docs/project05/%20ensemble-Chastain.ipynb

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