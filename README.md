# Seed-point-detection-brain-MRI

## ABSTRACT

Seed point is assumed to be a point which points out a region of high probability where a tumor
may be present in a slice of an MRI scan. Below is a ground truth image pointing out a tumor in
the brain tissue , Where the red dot is known as the seed point , which indicates the presence of
a tumor.

<img src="images/Ground truth - Seed point detection in medical imaging (brain tumor).jpg">

## METHOD 
### Data preprocessing:
Before training the data is normalized to fit a pixel range value of zero to one and the ground
truth seed points are also normalized to zero to one range to deal with an overall consistent
data , i.e , The input range and the output range of the model matches. Data augmentation
could be applied to vary the brightness of individual pixels to make more data samples in case
of overfitting. Since it’s a regression task the maximum augmentation that could be done with
data is very less.
### Model build:
The model is optimized in such a way that the no. of features extracted is not too detailed , nor
is very naive. As the feature resolution increases , the ability to put them up for the task at handis very less, The no of convolutional filters were chosen in such a way that there is optimized
amount of feature points for a regression task.
Since the data has high variance and inconsistencies a deep neural network with two dense
layers with ReLU activation functions, as to deal with the highly non linear nature of the data.
The optimizer used is adam with a tuned learning rate and other hyperparameters kept to their
standard values,
The output layer is kept to be a sigmoid to avoid overfitting and to avoid overflow of the
estimated value , The value obtained from the network is to be in the range of zero to one.

## Model: ARCHITECTURE

|Layer (type)| Output Shape| Param #|
|:----------:|------------:|-------:|
|conv2d (Conv2D)| (None, 240, 240, 32)| 320|
|activation (Activation)| (None, 240, 240, 32)| 0|
|max_pooling2d (MaxPooling2D)|(None, 120, 120, 32)| 0|
|conv2d_1 (Conv2D)| (None, 120, 120, 64) |18496|
|activation_1 (Activation) |(None, 120, 120, 64)| 0|
|max_pooling2d_1 (MaxPooling2)|(None, 60, 60, 64)| 0|
|conv2d_2 (Conv2D)| (None, 60, 60, 128)| 73856|
|activation_2 (Activation) |(None, 60, 60, 128)| 0|
|max_pooling2d_2 (MaxPooling2)|(None, 30, 30, 128)| 0|
|conv2d_3 (Conv2D)| (None, 30, 30, 128)| 147584|
|activation_3 (Activation)| (None, 30, 30, 128)| 0|
|max_pooling2d_3 (MaxPooling2)|(None, 15, 15, 128)| 0|
|flatten (Flatten)| (None, 28800) |0|
|dense (Dense)| (None, 512)| 14746112|
|activation_4 (Activation)| (None, 512)| 0|
|dense_1 (Dense)| (None, 128)| 65664|
|activation_5 (Activation) |(None, 128)| 0|
|dense_2 (Dense)| (None, 2)| 258|
|activation_6 (Activation)| (None, 2)| 0|
 
## Prediction and Convergence:
The estimated seed point obtained is within an error limit of + or - 3 pixels or less from the
ground truth given , which shows high accuracy and fast convergence of the model

<img src="images/loss.jpg>
          
<img src="images/accuracy.jpg>

### Covergence curve
## Results

<img src="images/Results 1 - Seed point detection in medical imaging (brain tumor).jpg>
          
<img src="images/Results 2 - Seed point detection in medical imaging (brain tumor).jpg>

<img src="images/Results 3 - Seed point detection in medical imaging (brain tumor).jpg>
   
<img src="images/Results 4 - Seed point detection in medical imaging (brain tumor).jpg>

## Validation using standard Techniques
The True positive is considered as the point that lies in +or- 15 pixels around the ground
truth, The False positive is considered as a point which lies outside the Region of intrest,
The test is done on the prediction of the test images , A graph is plotted between
normalized True positive and False positive.
<img src="images/ROC curve.jpg>
