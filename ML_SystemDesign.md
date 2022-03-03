# ML System Design Basics for MLE Interview

## Table of Contents

[1. Design a classification for Uber about whether a user will need a trip or not.](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_SystemDesign.md#1-design-a-classification-for-uber-about-whether-a-user-will-need-a-trip-or-not-)

[2. Design a classification for Tinder about whether a user will like the recommanded user suggestions or not based only on user profile images](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_SystemDesign.md#2-design-a-classification-for-tinder-about-whether-a-user-will-like-the-recommanded-user-suggestions-or-not-based-only-on-user-profile-images)

[3. Design a model that predicts Heart Attack Risk of a patient within the next 5 years ](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_SystemDesign.md#3-design-a-model-that-predicts-heart-attack-risk-of-a-patient-within-the-next-5-years)


### 1. Design a classification for Uber about whether a user will need a trip or not.

(1) Pull data to generate labels, 0, not call; 1, call
(2) ML Model: Xgboost of trees
(3) Metrics: Cross Entropy
(4) Pull Training data
  * User Proflile
     * Age
     * Gender
     * Job
     * Histroy Data, frequency of calling uber etc.
  * Weather
  * Current Time in 24 hour format
  * post code
  * Geo-Code, the starting place type e.g. hourse, shopping mall, hopstial etc
  * Holiday / Game Day / special day for locals

### 2. Design a classification for Tinder about whether a user will like the recommanded user suggestions or not based only on user profile images

Binary Classification

(1) Pull data to generate data, 1 like, 0 dislike
(2) ML Model: CNN 
(3) Pull img data and use feature vector to do classifcation

**Follow Up: How to deal with twins users, two user might look alike based on profile image**

(1) Pull other data like hobby / post code/ address/ personal data
(2) Train CNN to be able to differentiate twins, there shall be some thing different e.g. dress/ hair style etc.

### 3. Design a model that predicts Heart Attack Risk of a patient within the next 5 years

Your are tasked to design a model that predict Heart Attack Risk of a patient within the next 5 years.

Input: 
* images of eyes ~ 100k images
* binary label of whether a patient experience a heart attack or not ~ only 2% of 50k patients have heart attacks
* days to the heart attack if the patient did expereince a heart attack ~ only 2% of 50k patients have heart attacks


Prediction Target
* The heart attach Probabilty of a patient in the next 5 years
* days to the next heart attach

**Follow Up**

Above cases is only image data, what about if we can get more clinical data like age, gender, blood pressure etc? How to add these data into your model and improve the performance of your model?


**Answer**

(1) System Requirements

input
- 100K images of left, right eyes == > CNN as feature extractor
- binary variable indicating if a patient/image has experienced a heart attack == > y1:0, 1
      0: no heart attack ~ 0.98 * 50k = 49k
      1: heart attack ~ 1k 
- continuous variable indicating time (days) to heart attack (from time image was taken) ==> y2
      ~ 1k. 
      ~ 0 ~ 365 * 5 

Output
- Probability of having a heart attack within the next 5 years
  binary classifcation y_hat_1, 0, 1 ~ y1 ~ 50k
- time (days) until heart attack, y_hat_2, y2 ~ 1k

(2) Metrics

y1_hat_1 == > G_Mean, F1, RoC
y2_hat_2 == > MSE

(3) Pipeline of system - Two Stages of System

(3.1) Stage 1 Classifer

50k patients == > Classifer - > y_hat_1

Data Cleaning
DataSet Splitting: 80 % for training, 10% for validation, 10% for testing
Smapling: Oversampling + Undersampling for training dataset
Data Augmentation: Roataion, Fliping, Cut-Paste etc
Classifer: Resnet-50
Loss Function: Focual Loss + Weights for different Classes

(3.2) Stage 2 Predictor

Assuming we achieve a good performance for stage 1, then we build on stage 1 for stage 2.

~1k patients == > Predictor - > y_hat_2

DataSet Splitting: 80 % for training, 10% for validation, 10% for testing
Resnet-50-Regression + Transfer Learning to use wegihts from stage 1 + MSE

Training:
*   Prevent overfiting:  Early Stoping + Dropout + Regulizer into loss function
*   Learning Rate Scheduler 


**Follow Up for Adding more features**

image == > ResNet == > feature vector  1x256
added features ==> vectorlize == > 1x20

Combine two feacture vector together to make the mixed feature vector as input to FNN/SVM/RF
MinMax for each feature to make them into the same range 0~1 
