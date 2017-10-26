# python-tutorial
The aim is to setup a research/development environment using Python with the option to integrate with R (i.e. calling Python from R).

## Python and Machine Learning
Theano and TensorFlow (by Google) are two main backend libraries for Deep Learning research and development. Both are accessible via Python API.

Keras is a wrapper API that presents a higher-level, more intuitive set of abstractions that make it easy to configure neural networks regardless of the backend library. Essentially Keras Python library provides a clean and convenient way to create a range of deep learning models on top of Theano or TensorFlow. 

## Installation of Keras with Tensorflow at the backend
A good reference is https://www.datacamp.com/community/tutorials/keras-r-deep-learning

We use Anaconda to setup Python environment. For Tensorflow installation, there are two options:
 1. Use Anaconda (recommended) or pip 
 2. Use the RStudio kera package

### Install Anaconda
Two main features about Anaconda:
 1. Install/update packages (e.g. Python, numpy)
 2. Switching between environments (e.g. between Python 3.6 and 2.7)

Only install Anaconda 2.x or Anaconda 3.x (recommended). After installing Anaconda 3.x, you can create an 2.x environment (optional) by:
 ```
 conda create -n py27 python=2.7
 activate py27
 conda install numpy
 ```
More here: https://conda.io/docs/user-guide/tasks/manage-python.html

Installation link: https://www.anaconda.com/download/

### Verify Python environment 
Open All Programs -> Anaconda3 -> "Anaconda Prompt", then type the following:
```
> python --version
Python 3.6.3 :: Anaconda, Inc.
```

### Cuda Installation 
Cuda is the C/C++ library to harness the processing power of the graphics processing unit (GPU). CUDA-capable GPUs have hundreds of cores that can collectively run thousands of computing threads. 

First of all, tensorflow requires a GPU with CUDA Compute Capability (CC) 3.0 or higher. For NVIDIA card, check here: https://developer.nvidia.com/cuda-gpus. For example, my laptop has GeForce GTX 960M	with CC 5.0 so that's good news!

Next, install CUDA® Toolkit 8.0:
 1. Get the installer from http://developer.nvidia.com/cuda-downloads
 2. The version of the CUDA Toolkit can be checked by running `nvcc -V` in a Command Prompt window
 ```
 nvcc: NVIDIA (R) Cuda compiler driver
 Copyright (c) 2005-2017 NVIDIA Corporation
 Built on Fri_Sep__1_21:08:32_Central_Daylight_Time_2017
 Cuda compilation tools, release 9.0, V9.0.176
 ```
 
 3. To verify a correct configuration of the hardware and software, it is highly recommended that you run the `deviceQuery` program located at
 ```
 C:\ProgramData\NVIDIA Corporation\CUDA Samples\v9.0\bin\win64\Release
 ```

Next, install cuDNN v6 or v6.1. The NVIDIA CUDA® Deep Neural Network library (cuDNN) is a GPU-accelerated library of primitives for deep neural networks. cuDNN provides highly tuned implementations for standard routines such as forward and backward convolution, pooling, normalization, and activation layers. Follow these steps:
 1. Get the library from https://developer.nvidia.com/rdp/cudnn-download. Window 7 version can be used under Window 8.1
 2. Put the files under a directory (e.g. C:\ProgramData\NVIDIA Corporation\cuDNN)
 3. Add the bin directory to System PATH (e.g. C:\ProgramData\NVIDIA Corporation\cuDNN\bin)


### Install Tensorflow with Anaconda
Guide: https://www.tensorflow.org/install/install_windows
 1. Create a conda environment named tensorflow by invoking the following command: 
 ```
 conda create -n tensorflow35 python=3.5
 ```
 2. Activate the conda environment by issuing the following command:
 ```
 activate tensorflow35
 ```
 3. Install GPU version of TensorFlow:
 ```
 pip install --ignore-installed --upgrade tensorflow-gpu
 ```
 4. (Alternatively) install CPU version:
 ```
 pip install --ignore-installed --upgrade tensorflow
 ```

To verify installation is successful, open "Anaconda Prompt" and invoke python from the shell by tpying `python`, then enter the following short prpgram:
```
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
```

### R-integration: Setting up Keras/tensorflow interface using RStudio 'keras' package
1. Install devtools so we can install packages from github: install.packages("devtools")
2. Install kera (in RStudio): devtools::install_github("rstudio/keras")
3. Next step to install TensorFlow is skipped but noted here for completion: install_tensorflow()
4. Locating already installed Tensorflow (by Anaconda/pip): see "Custom installation" https://tensorflow.rstudio.com/installation.html

## Python IDE

### Jupyter (formerly, IPython) Notebooks

## Useful Tutorials 
Collection of useful Python tutorials

Array slice notation: https://stackoverflow.com/questions/509211/explain-slice-notation
