# ai-predictive-maintenance-System-for-Bearing-Fault-Diagnosis
Predictive maintenance model trained on CWRU bearing vibration data &Classifies: Normal, Ball Fault, Inner Race Fault, Outer Race Fault.

# dataset
you can download data set from https://www.kaggle.com/datasets/brjapon/cwru-bearing-datasets & https://engineering.case.edu/bearingdatacenter/download-data-file
remember to place .mat files into a folder named as "sample" and in that make sub folder for outer race , inner race, ball fault and normal ( i have used only one file in it  but try using more it will provide you with better prediction)

# result
Random Forest — 97% accuracy ,SVM Accuracy - 74.47%  on held-out test set.

# Usage
import joblib
model = joblib.load('bearing_fault_rf_model.pkl')
