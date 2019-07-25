# Quantization
Light version of convolutional neural network YoloV3 & DroNet for objects detection with a minimum of dependencies (INT8-inference)

### Inspired and based on
* **https://github.com/AlexeyAB/yolo2_light**
* **https://github.com/gplast/DroNet**

### Software Requirements
A Linux (Ubuntu 18.04) build environment needs these components:
* [`OpenCV 3.4`](https://docs.opencv.org/3.4.2/d7/d9f/tutorial_linux_install.html) or higher
* [`GNU Compiler Collection (GCC) 3.4`](https://linuxconfig.org/how-to-install-gcc-the-c-compiler-on-ubuntu-18-04-bionic-beaver-linux) or higher
* [`CMake 2.8`](https://cmake.org/install/) or higher
* [`Python 3.6`](https://www.python.org/downloads/) or higher

### Clone Repository
```bash
cd ~
https://github.com/constandinos/quantization.git
```

### Install
```bash
cd quantization
make
cd ..
```

How to compile:
* To compile for CPU just do `make` on Linux or build `yolo_cpu.sln` on Windows
* To compile for GPU set flag `GPU=1` in the `Makefile` on Linux or build `yolo_gpu.sln` on Windows
    
    Required both [CUDA >= 8.0](https://developer.nvidia.com/cuda-toolkit-archive) and [cuDNN >= 7.1.1](https://developer.nvidia.com/rdp/cudnn-archive)

### Run (**INT8**-inference)
```bash
cd bin

# DroNet
./darknet detector test names/car.names cfg/DroNet_car.cfg weights/DroNet_car.weights -thresh 0.4 images/car.png -quantized

# DroNetV3
./darknet detector test names/car_ped.names cfg/DroNetV3_car.cfg weights/DroNetV3_car.weights -thresh 0.4 images/car.png -quantized

# Tiny-Yolo
./darknet detector test names/coco.names cfg/yolov3-tiny-car.cfg weights/yolov3-tiny-car.weights -thresh 0.4 images/car.png -quantized
```


