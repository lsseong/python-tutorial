# python-tutorial
The aim is to setup a research/development environment using Python with the option to integrate with R (i.e. calling Python from R).

## Python and Machine Learning
Theano and TensorFlow (by Google) are two main backend libraries for Deep Learning research and development. Both are accessible via Python API.

Keras is a wrapper API that presents a higher-level, more intuitive set of abstractions that make it easy to configure neural networks regardless of the backend library. Essentially Keras Python library provides a clean and convenient way to create a range of deep learning models on top of Theano or TensorFlow. 

## Installation of Keras with Tensorflow at the backend
A good reference is https://www.datacamp.com/community/tutorials/keras-r-deep-learning

You use Anaconda to setup Python environment. For Tensorflow installation, there are two options:
 1. Use Anaconda (recommended) or pip 
 2. Use the RStudio kera package

### Install Anaconda
Two main features about Anaconda:
 1. Install/update packages (e.g. Python, numpy)
 2. Switching between environments (e.g. between Python 3.6 and 2.7)

Only install Anaconda 2.x or Anaconda 3.x (recommended). After installing Anaconda 3.x, you can create an 2.x environment by:
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

### Install Tensorflow with Anaconda
Guide: https://www.tensorflow.org/install/install_windows
 1. Create a conda environment named tensorflow by invoking the following command: 
 ```
 conda create -n tensorflow python=3.5
 ```
 2. Activate the conda environment by issuing the following command:
 ```
 activate tensorflow
 ```
 3. Install GPU version of TensorFlow:
 ```
 pip install --ignore-installed --upgrade tensorflow-gpu
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
