# Module 20 Challenge:  Credit Risk Analysis

## Overview of the Analysis

The purpose of this analysis is to build a supervised machine learing model to identify the creditworthiness of borrowers.

The data used for this analysis is contained within the file, "lending_data.csv". This file contains 77,536 records. For each record, the following attributes were available:
* loan size
* interest rate
* borrower income
* debt to income ratio
* number of accounts
* number of derogatory marks
* total debt
* loan status

"loan status" is the attribute of interest: By using the other attributes in our model, we want to predict whether loan status is '0' (healthy) or '1' (high-risk).

My approach:
1. The dependencies were imported. These included numpy, pandas, Path, confusion_matrix, classification_report, train_test_split, and LogisticRegression
2. The source data (CSV) was read into a Pandas DataFrame and inspected.
3. I then separated the data into labels ("y", loan status - the attribute of interest) and features ("X", all attributes other than loan status)
4. Next, I used train_test_split to split the data into 4 arrays:
   * X training data
   * X testing data
   * y training data
   * y testing data
5. After splitting the data, a logistic regression model was instantiated, and the model was fitted using the training data.
6.  Predictions were then made using the testing data, and the predictions along with the actual values of loan status were saved to a DataFrame.
7.  Lastly, I generated a confusion matrix and a classification report. These are used to evaluate the efficacy of the model.

## Results

* My Machine Learning Model's results:
    * Accuracy = (TP + TN)/(TP + TN + FP + FN) = (18,663 + 563)/(18,663 + 563 + 102 + 56) = 0.99. This indicates the model's predictions are correct across all classes nearly always. The data, however, contains many more "healthy" loans than "high-risk" loans. It's important to evaluate precision and recall as well!
    * Precision = TP/(TP + FP) = 563 / (563+102) = 0.8466. Precision indicates the model's ability to avoid false positives. 0.8466 is fairly high, though a domain expert (someone who is knowlegeable of the lending industry) would need to opine as to whether this is sufficiently high.
    *  Recall = TP/(TP + FN) = 563/(563+56) = 0.90953. Recall is the ratio of correctly predicted positive observations. At just over 90%, this model's recall is, in my opinion, great. 

## Summary

Overall, the logistic regression model created herein is accurate (in the colloquial sense) and can be used to identify the creditworthiness of borrowers. The standard metrics (accuracy, precision, and recall) are all high (+80%) which should give the user confidence in this model. Moreover, this model is not overly complicated, and doesn't require a plethora of features.

It is important to note that performance depends on the problem we are trying to solve. That is, it is more important that we predict the "1s" (high-risk loans) than it is the "0s" (healthy loans). Because
* We aren't (shouldn't?) be concerned about healthy loans - the lender won't lose their capital. 
* It's possible that by identifying high-risk loans, the lender could take proactive steps with the borrower, e.g., reconfigure the terms of the loan, to avoid default.