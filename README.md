# EMNIST_CNN_VGG
A convoluted neural network and a VGG Network trained and tested on EMNIST dataset to classify digits and numbers correctly, using pytorch

**EMNIST dataset**
- 36 classes of digits 0-1 and alphabets A-Z each with 2800 images 
- Each image is RGB wof 28*28 pixels

**CNN**
- The architecture has 4 convolutional layers and three fully connected layers. Output of last convolutional
layer is flattened and input to first fully connected layer. To describe in detail the following are the layer
distributions:

Convolutional Layers:
conv1: 1 input channel, 32 output channels, 3x3 kernel, followed by GELU activation, max pooling (2x2), and
20% dropout.
conv2: 32 input channels, 64 output channels, 3x3 kernel, followed by Tanh activation, max pooling (2x2),
and 20% dropout.
conv3: 64 input channels, 128 output channels, 3x3 kernel, followed by GELU activation, max pooling (2x2),
and 20% dropout.
conv4: 128 input channels, 256 output channels, 3x3 kernel, followed by Tanh activation, average pooling
(2x2), and 20% dropout.
Fully Connected Layers:
fc1: 256 input units, 256 output units, followed by Tanh activation and 20% dropout.
fc2: 256 input units, 128 output units, followed by Tanh activation and 20% dropout.
fc3: 128 input units, n_classes output units.
Pooling:
Max pooling is applied after conv1, conv2, and conv3; average pooling is applied after conv4

- Optimisations to improve model accuracy was tried: Learning rate scheduler, early stopping and batch normalisation.
- Learning rate scheduler gives best accuracy of 0.92

**ModifiedVGG_13 Implementation**
- The ModifiedVGG_13 model we built is based on the VGG -13 architecture, which consists of sequential
convolutional layers followed by fully connected layers.

Convolutional Layers:
conv1 & conv2: 64 filters, 3x3 kernel, followed by ReLU activations.
conv3 & conv4: 128 filters, 3x3 kernel, followed by ReLU activations.
conv5 & conv6: 256 filters, 3x3 kernel, followed by ReLU activations.
conv7 & conv8: 512 filters, 3x3 kernel, followed by ReLU activations.
conv9 & conv10: 512 filters, 3x3 kernel, followed by ReLU activations.

After each 2 sets of convolution layer, there is a max pool layer to reduce spatial dimension by factor of 2.

Fully Connected Layers:
fc1: Fully connected layer with 4096 units, followed by ReLU and Dropout.
fc2: Fully connected layer with 4096 units, followed by ReLU and Dropout.
fc3: Final fully connected layer with 36 output units, which indicate number of classes.
Each of convlution and fully connected layer is followed by Relu activation function. There is dropout layer of
50 percent applied after each FC layer.

Weight initialisation has been introduced for the model to perform better, Kaiming (He) initialization for
convolution layers and Normal distribution for fully connected layers.

The ModifiedVGG_13 model has 10 convolutional layers whereas there are only in Part3 model, making it
significantly deeper and more complex.

- The accuracy on testing data is 0.92 percent. The Precision and Recall scores are high, indicating that the
model is performing classifications correctly. The closeness of f1-score to precision and recall signals that
there is no significant bias for the model towards or against specific classes.
