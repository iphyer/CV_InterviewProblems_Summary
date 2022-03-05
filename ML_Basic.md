# ML Basics for MLE Interview

## Table of Contents

[1. What is softmax function?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#1-what-is-softmax-function)

[2. What is sigmoid function?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#2-what-is-sigmoid-function)

[3. What is sensitivity and specificity? ](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#3-what-is-sensitivity-and-specificity)

[4. What is Confusion Matrix?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#4-what-is-confusion-matrix)

[5. What is Drop-out? Any difference for Drop-out in Training and Inference?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#5-what-is-drop-out-any-difference-for-drop-out-in-training-and-predicting)

[6. What is Batch Norm? Any difference for Batch Norm in Training and Inference?](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/ML_Basic.md#6-what-is-batch-norm-any-difference-for-batch-norm-in-training-and-predicting)

### 1. What is softmax function? 

### 2. What is sigmoid function? 

### 3. What is sensitivity and specificity? 

### 4. What is Confusion Matrix? 

### 5. What is Drop-out? Any difference for Drop-out in Training and Inference? 

### 6. What is Batch Norm? Any difference for Batch Norm in Training and Inference? 



Batch Norm is a neural network layer that is now commonly used in many architectures. It often gets added as part of a Linear or Convolutional block and helps to stabilize the network during training. In other words, if we are able to somehow normalize the activations from each previous layer then the gradient descent will converge better during training. This is precisely what the Batch Norm layer does for us. [ [ref](https://towardsdatascience.com/batch-norm-explained-visually-how-it-works-and-why-neural-networks-need-it-b18919692739) ]

A Batch Norm layer also has parameters of its own:
* Two learnable parameters called beta and gamma.
* Two non-learnable parameters (Mean Moving Average and Variance Moving Average) are saved as part of the ‘state’ of the Batch Norm layer.

Order of placement of Batch Norm layer

There are two opinions for where the Batch Norm layer should be placed in the architecture — before and after activation. The original paper placed it before, although I think you will find both options frequently mentioned in the literature. Some say ‘after’ gives better results.

**Batch Norm during Training**

![BN Training](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/Resources/Pics/BN_Training.png)

**Batch Norm during Inference**

As we discussed above, during Training, Batch Norm starts by calculating the mean and variance for a mini-batch. However, during Inference, we have a single sample, not a mini-batch. How do we obtain the mean and variance in that case?
Here is where the two Moving Average parameters come in — the ones that we calculated during training and saved with the model. We use those saved mean and variance values for the Batch Norm during Inference.

![BN Inference ](https://github.com/iphyer/MLE_Interview_Preparation/blob/main/Resources/Pics/BN_Inference.png)


## Q1.你了解lstm吗

## Q2.你了解xgboost算法吗，说下情况

## Q3.说下你了解的深度学习网络

## Q4.说下bp的过程

## Q5.深度学习的激活函数

## Q6.深度学习的优化函数

## Q7.说下牛顿法（上面的优化函数我没提）

## Q8.BN，BN和普通的Normalization的区别

## Q9.过拟合的相关问题

## Q10.svm

## Q11.反卷积具体怎么实现的

## Q12.为什么dropout能减少过拟合

## Q13.rcnn, fast rcnn,fater rcnn,yolo,问了我具体的yolo的那个anchor,反正好多具体的东西

## Q14.常见 Loss 的形式

## Q15. 常见网络架构的名字和特点

## Q16. 有什么生成模型你知道的。
