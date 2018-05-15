# Setup for my Traffic Project

In this tutorial I will introduce how to setup environment for my project. (keras/tensorflow deep learning environment with GPU and CUDA).
 
## Getting Started

I'm running the project on Ubuntu 16.04, can't guarantee it will work on other Ubuntu version. For Windows or Mac os, please refer to [Windows](https://research.wmz.ninja/articles/2017/01/configuring-gpu-accelerated-keras-in-windows-10.html), [Mac OS](https://www.pyimagesearch.com/2017/09/29/macos-for-deep-learning-with-python-tensorflow-and-keras/) 
### System dependencies


```
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install build-essential cmake git unzip pkg-config
$ sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
$ sudo apt-get install libxvidcore-dev libx264-dev
$ sudo apt-get install libgtk-3-dev
$ sudo apt-get install libhdf5-serial-dev graphviz
$ sudo apt-get install libopenblas-dev libatlas-base-dev gfortran
$ sudo apt-get install python-tk python3-tk python-imaging-tk
```

### Installing Python

A step by step series of examples that tell you have to get a development env running

Say what the step will be

```
$ sudo apt-get install python2.7-dev python3-dev
```
Use the Ubuntu updater to update your driver, and then check out CUDA with cuDNN installation here: [Ubuntu 16.04 + CUDA](https://www.pyimagesearch.com/2017/09/27/setting-up-ubuntu-16-04-cuda-gpu-for-deep-learning-with-python/)

End with an example of getting some data out of the system or using it for a little demo

### Compiling OpenCV

Explain how to run the automated tests for this system
```
$ cd ~
$ wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.3.0.zip
$ wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.3.0.zip


$ unzip opencv.zip
$ unzip opencv_contrib.zip
```


```
$ cd ~/opencv-3.3.0/
$ mkdir build
$ cd build
$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D WITH_CUDA=OFF \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.3.0/modules \
    -D BUILD_EXAMPLES=ON ..
```
make and install opencv.
```	
$$ make -j4

$ sudo make install
$ sudo ldconfig
$ cd ~
```
add open cv to the virtual enviornment.
```
$ cd ~/.virtualenvs/dl4cv/lib/python3.5/site-packages/
$ ln -s /usr/local/lib/python3.5/site-packages/cv2.cpython-35m-x86_64-linux-gnu.so cv2.so
$ cd ~
```


### Keras with Tensorflow
denpendencies for keras/fensorflow
```
$ pip install scipy matplotlib pillow
$ pip install imutils h5py requests progressbar2
$ pip install scikit-learn scikit-image
```
install tensorflow GPU version and keras.
```
$ pip install tensorflow-gpu

$ pip install keras
```
head to ~/.keras/keras.json and check the configuration is as followed.
```
{
    "image_data_format": "channels_last",
    "backend": "tensorflow",
    "epsilon": 1e-07,
    "floatx": "float32"
}
```
### Mask-rcnn model and test video

use```pycocotools``` to test and train MS COCO.
Download pre-trained [coco model](https://github.com/matterport/Mask_RCNN/releases) and [test video]().
Save coco model under ```./Mask-RCNN/models```, test video is for testing only, don't need it for real application.


