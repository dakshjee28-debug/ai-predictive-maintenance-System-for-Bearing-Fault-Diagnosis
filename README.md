# ai-predictive-maintenance-System-for-Bearing-Fault-Diagnosis
Predictive maintenance model trained on CWRU bearing vibration data &Classifies: Normal — no fault
Ball Fault — defect on the rolling element
Inner Race Fault — defect on the inner raceway
Outer Race Fault — defect on the outer raceway

# dataset
you can download data set from https://www.kaggle.com/datasets/brjapon/cwru-bearing-datasets & https://engineering.case.edu/bearingdatacenter/download-data-file
remember to place .mat files into a folder named as "sample" and in that make sub folder for outer race , inner race, ball fault and normal ( i have used only one file in it  but try using more it will provide you with better prediction)

# How It Works
Signal loading:reads the driveend (DE_time) vibration signal from each ".mat file"
Windowing : slices each signal into fixed length segments (2048 samples each )
Feature extraction : computes 15 features per segment, combining time domain statistics (RMS, kurtosis, skewness, crest factor, etc.) and frequency domain statistics (FFT mean,std, max, dominant frequency, spectral entropy).
Model training :trains and compares two classifiers:

Random Forest :250 trees and max depth 12
Support Vector Machine (RBF kernel)



Evaluation :confusion matrix(compares the actual classes with the predicted classes)
           per class precision(it states out of all samples predicted as a class, how many were actually that class)
           recall(it stateshow many did the model correctly find)
           F1(it finds balance between Precision and Recall)
           feature importance ranking( it ranks every feature that is extracted from the analysis on the basis of their contribution to model prediction)
Health scoring : converts model confidence into a bearing health index (%) and a plain language maintenance recommendation for user friendly application

# result
Trained on 2,369 extracted feature samples (711 each for ball fault, inner race, and outer race; 236 for normal) 
split 80/20 with stratification.
              precision    recall  f1-score   support

  ball fault       0.94      0.94      0.94       142
  inner race       0.99      0.99      0.99       142
      normal       1.00      0.98      0.99        47
  outer race       0.95      0.96      0.95       143

    accuracy                           0.97       474
   macro avg       0.97      0.97      0.97       474
weighted avg       0.97      0.97      0.97       474

The most predictive features were FFT-derived statistics and peak-to-peak amplitude, consistent with the fact that bearing faults introduce distinct periodic impact peaks in the frequency spectrum

<img width="835" height="568" alt="result" src="https://github.com/user-attachments/assets/cee21285-f6d0-481c-b473-45767e24cb2c" />

Random Forest — 97% accuracy ,SVM Accuracy - 74.47%  on held-out test set.

# Usage
import joblib
model = joblib.load('bearing_fault_rf_model.pkl')

The 15 expected features, in order:
RMS, Mean, STD, Variance, Peak, PeakToPeak, Kurtosis, Skewness, CrestFactor, FFT_Mean, FFT_STD, FFT_Max, DominantFreq, Energy, SpectralEntropy

# requirement
numpy
pandas
scipy
matplotlib
seaborn
scikit-learn
joblib
fft knowledge
how bearing is classified and its part
what part produce vibration
how vibration increases
what fault occurs in bearing
basic to medium knowledge about machine learning

# Acknowledgments

Dataset courtesy of the :
Case Western Reserve University Bearing Data Center 
CWRU Bearing Dataset from kaggle( # used here )

