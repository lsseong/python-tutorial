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
To see a list of Anaconda environment, type:
```
conda env list
```

More here: https://conda.io/docs/user-guide/tasks/manage-python.html

Installation link: https://www.anaconda.com/download/

### Verify Python environment 
Open All Programs -> Anaconda3 -> "Anaconda Prompt", then type the following:
```
> python --version
Python 3.6.3 :: Anaconda, Inc.
```

### Useful Modules
The following modules are useful in machine learning. Open Anaconda Prompt and type the following (you can also install the following module by activating an environment first):
```
conda install numpy
conda install scipy
conda install matplotlib
conda install pandas
conda install scikit-learn
```

### Cuda Installation 
Cuda is the C/C++ library to harness the processing power of the graphics processing unit (GPU). CUDA-capable GPUs have hundreds of cores that can collectively run thousands of computing threads. 

First of all, tensorflow requires a GPU with CUDA Compute Capability (CC) 3.0 or higher. For NVIDIA card, check here: https://developer.nvidia.com/cuda-gpus. For example, my laptop has GeForce GTX 960M	with CC 5.0 so that's good news!

Before proceeding, check the TensorFlow installation guide (https://www.tensorflow.org/install/install_windows) to find out the  required version of CUDA Toolkit and cuDNN (any other version will not work). At the time of writing, it requires CUDA® Toolkit 9.0 and cuDNN v6.0 or v6.1.

Next, install CUDA® Toolkit 9.0:
 1. Get the installer from https://developer.nvidia.com/cuda-toolkit-archive
 2. The version of the CUDA Toolkit can be checked by running `nvcc -V` in a Command Prompt window
 ```
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Mon_Jan__9_17:32:33_CST_2017
Cuda compilation tools, release 8.0, V8.0.60
 ```
 
 3. To verify a correct configuration of the hardware and software, it is highly recommended that you run the `deviceQuery` program located at
 ```
 C:\ProgramData\NVIDIA Corporation\CUDA Samples\v9.0\bin\win64\Release
 ```

Next, install cuDNN v6 or v6.1. The NVIDIA CUDA® Deep Neural Network library (cuDNN) is a GPU-accelerated library of primitives for deep neural networks. cuDNN provides highly tuned implementations for standard routines such as forward and backward convolution, pooling, normalization, and activation layers. Follow these steps:
 1. Get the library from https://developer.nvidia.com/rdp/cudnn-download. 
 2. At the time of writing, the tensorflow installation for Window says that TensorFlow will not load if it cannot find cuDNN64_6.dll. So we have to download the cuDNN v6.0 (April 27, 2017), for CUDA 8.0. 
 3. Put the files under a directory (e.g. C:\ProgramData\NVIDIA Corporation\cuDNN\v6\cuda8). There should be cuDNN64_6.dll under the bin directory.
 4. Add the bin directory to System PATH (e.g. C:\ProgramData\NVIDIA Corporation\cuDNN\v6\cuda8\bin)


### Install Tensorflow with Anaconda
Guide: https://www.tensorflow.org/install/install_windows
 1. Create a conda environment named tensorflow by invoking the following command: 
 ```
 conda create -n tf36 python=3.6
 ```
 2. Activate the conda environment by issuing the following command:
 ```
 activate tf36
 ```
 3. Install GPU version of TensorFlow:
 ```
 pip install --ignore-installed --upgrade tensorflow-gpu
 ```

Reference here: https://www.tensorflow.org/install/install_windows

To verify installation is successful, open "Anaconda Prompt" and invoke python from the shell by tpying `python`, then enter the following short prpgram:
```
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))
```
Which sould produce the following output (note the output of your card model, GeForce GTX 860M in my case)
```
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
2017-10-26 22:34:26.374731: W C:\tf_jenkins\home\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions,
 but these are available on your machine and could speed up CPU computations.
2017-10-26 22:34:26.375459: W C:\tf_jenkins\home\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX2 instructions
, but these are available on your machine and could speed up CPU computations.
2017-10-26 22:34:27.245315: I C:\tf_jenkins\home\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\common_runtime\gpu\gpu_device.cc:955] Found device 0 with properties:
name: GeForce GTX 860M
major: 5 minor: 0 memoryClockRate (GHz) 1.0195
pciBusID 0000:01:00.0
Total memory: 4.00GiB
Free memory: 3.89GiB
2017-10-26 22:34:27.245687: I C:\tf_jenkins\home\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\common_runtime\gpu\gpu_device.cc:976] DMA: 0
2017-10-26 22:34:27.245887: I C:\tf_jenkins\home\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\common_runtime\gpu\gpu_device.cc:986] 0:   Y
2017-10-26 22:34:27.255244: I C:\tf_jenkins\home\workspace\rel-win\M\windows-gpu\PY\35\tensorflow\core\common_runtime\gpu\gpu_device.cc:1045] Creating TensorFlow device (/gpu:0) -> (device: 0, name: G
eForce GTX 860M, pci bus id: 0000:01:00.0)
>>> print(sess.run(hello))
b'Hello, TensorFlow!'
```


### R-integration: Setting up Keras/tensorflow interface using RStudio 'keras' package
1. Install devtools so we can install packages from github: install.packages("devtools")
2. Install kera (in RStudio): devtools::install_github("rstudio/keras")
3. Next step to install TensorFlow is skipped but noted here for completion: install_tensorflow()
4. Locating already installed Tensorflow (by Anaconda/pip): see "Custom installation" https://tensorflow.rstudio.com/installation.html

## Python IDE
### Spyder
Anaconda installation comes with Spyder IDE, which can be launched directly by Programs -> Anaconda3 -> Spyder

### PyCharm
There's a free Community version available: https://www.jetbrains.com/pycharm/download/#section=windows

When you first launch PyCharm, it will set your Python intepreter to C:\ProgramData\Anaconda3\python.exe

If you want PyCharm to use another Anaconda environment you have created earlier, figure out the Anaconda environment folder (`conda env list`) and do the following in PyCharm:
 1. File -> Settings -> Project [name] -> Project Interpreter
 2. Click the "Wheels" icon -> Add Local -> (point to python.exe in the conda env folder)

### Jupyter (formerly, IPython) Notebook
Programs -> Anaconda3 -> Jupyter Notebook

Good intro: https://media.readthedocs.org/pdf/jupyter-notebook-beginner-guide/latest/jupyter-notebook-beginner-guide.pdf

### Sublime Text 3
https://www.youtube.com/watch?v=zVLJfrIwEP8&list=PL-osiE80TeTtHH8BZngXEsLPGotQxZa6z

## Useful Tutorials 
Collection of useful Python tutorials

Array slice notation: https://stackoverflow.com/questions/509211/explain-slice-notation
