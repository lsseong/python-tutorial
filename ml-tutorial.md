http://www.wildml.com/2016/10/learning-reinforcement-learning/

Overview	of	mini-batch	gradient	descent	
http://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf

Softmax intro
https://github.com/Kulbear/deep-learning-nano-foundation/wiki/ReLU-and-Softmax-Activation-Functions

Convolution neural network intro
https://medium.com/technologymadeeasy/the-best-explanation-of-convolutional-neural-networks-on-the-internet-fbb8b1ad5df8


## Convolution notes
A convolution in CNN is nothing but a element wise multiplication i.e. dot product of the image matrix and the filter. A filter is to learn a characteristic of an image.

A convolution layer takes an input volume, apply k-number of filters and produces an output volume. Why do we speak of input/output volume? Because data dimension is 3D. Why? Say input is a 100 x 100 image, with each pixel being represent as 3 RGB floats, then data dimension is {100,100,3} or {width, height, depth}. Similar, output data will have a depth of k (because there are k filters).

What's the dimension of each filter? Kernel size (width/heigh) is a hyperparameter (i.e. user can set it to any value), but depth will be the same as input depth. That's right! If input has depth of 3, then each filter has a depth of 3 too! For example if kernel size is 5, then kernel matrix dimension is {5, 5, 3}. Why depth of 3? Well, we use {5, 5, 1} to produce first dot product (a scalar) at depth = 1, then use {5, 5, 2} at depth = 2 and {5, 5, 3} at depth = 3. Then we sum up these 3 scalar values (plus a bias) to produce a final value. This single value is also the output of a neuron. As a result of the sum over depth, each filter will produce just a 2D image.

Kernel size, padding, stride and input width/height will determine the output width and height. Assuming it is N, then output volume dimension will be {N, N, K} where we have K-filters. Each output layer (i.e. k=1, 2, 3...) is also called a feature map. 

What about ReLU, the activation function? Its common practice to place ReLU logic after each neuron output. ReLU dimension will be the same as output volume dimension i.e. {N, N, K}.

It is a good practice to apply "batch normalization" after each layer because this technique potentially helps in two ways: faster learning and higher overall accuracy by addressing a phenomena called "internal covariance shift". Further reading here: https://www.quora.com/Why-does-batch-normalization-help
