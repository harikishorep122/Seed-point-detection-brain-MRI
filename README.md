# Seed-point-detection-brain-MRI

## ABSTRACT

Seed point is assumed to be a point which points out a region of high probability where a tumor
may be present in a slice of an MRI scan. Below is a ground truth image pointing out a tumor in
the brain tissue , Where the red dot is known as the seed point , which indicates the presence of
a tumor.

![groud truth](https://github.com/harikishorep122/Seed-point-detection-brain-MRI/blob/master/Ground%20truth%20-%20Seed%20point%20detection%20in%20medical%20imaging%20(brain%20tumor).jpg)
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
 
## Validation using standard Techniques
