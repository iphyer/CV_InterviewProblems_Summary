# ML System Design Basics for MLE Interview

## Table of Contents

[1. What is softmax function?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#1-what-is-softmax-function)

[2. What is sigmoid function?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#2-what-is-sigmoid-function)

[3. What is sensitivity and specificity? ](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#3-what-is-sensitivity-and-specificity)

[4. What is Confusion Matrix?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#4-what-is-confusion-matrix)

[5. What is Drop-out? Any difference for Drop-out in Training and Inference?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#5-what-is-drop-out-any-difference-for-drop-out-in-training-and-predicting)

[6. What is Batch Norm? Any difference for Batch Norm in Training and Inference?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#6-what-is-batch-norm-any-difference-for-batch-norm-in-training-and-predicting)

### 1. Design a classification for Uber about whether a user will need a trip or not .

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

### 2. What is sigmoid function? 

### 3. What is sensitivity and specificity? 






