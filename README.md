## Lane Keeping and Navigation of a Self-driving RC Car Based on Image Semantic Segmentation and GPS Fusion
This repository contains the code and resources for the 2022 IEEE research paper "Lane Keeping and Navigation of a Self-driving RC Car Based on Image Semantic Segmentation and GPS Fusion". The paper discusses an approach to autonomous vehicle navigation, combining image semantic segmentation and GPS data fusion.

## Notice
Some of the code may have been deprecated due to changes in NVIDIA SDK, and TensorRT engines, conversion modules from NVIDIA. As of now, we don't have access to the hardware used in the paper but we will try to help in issue.

## Getting Started
Instructions on how to set up the project locally.

## Prerequisites
### Hardware (our setup)
* Ububtu >=18.04 PC with NVIDIA GTX 1050 and above for model training
* NVIDIA-Jetson TX2/ Xavier/ Nano(possibly) with Jetpack >4.0 to run deployment code, TensorRT conversion
If you want to build a running car model, these might help:
* Camera: For image processing, HD camera recommended
* A 1/12 RC car model. RC cars can be found in hobby shops (Swap their servo for 3pin servo to control with Servo controller and Arduino for steering control, as for the drive motor, use a H-Bridge)
* PCA9865 servo driver (Connect the 3pin servo and 3 pins from the H-Bridge)
* Arduino Nano/UNO (A direct control from the Jetson to servo driver might work but might risk damaging the Jetson)
* 20kg Digital servo
* Power supply: 12V 5000mAH for the Jetson TX2, 7.4V 5000mAH for the servo and drive motor
### Software
* Pytorch > 1.1
* Python >= 3.7
* Anaconda3/Miniconda3 (optional)

## Installation
In the conda environment, run
`pip install -r requirements.txt`

## Usage
### Training the model

### Deploying the model

### TensorRT conversion
TensorRT conversion is in tensorrt/trt_utils

### Run the RC-car
To be run in a bash script
* Description:
    This script runs the driving algorithm. Here is a breakdown:
    - Running this python script in a bash or .sh scipt along with a scrip that receive driving signals from the Hand controlller.
    - The script runs as 2 proccess.
        + A client that receives GPS (lat, lon) and IMU data (yaw) from the phone app.
        + A controller that runs the driving algorithm based on the received sensor data above.
            o The controller uses yaw angle passed from a script that runs the Pytorch model in realtime with video input from the Top camera of the vehicle. 
            This will keep the vehicle running within the road lane.
            o The controller uses GPS/IMU data passed from the client to calculate the distance between the vehicle and the next waypoint AND estimate the steering angle.
            This will keep the vehicle running on the right, predifined GPS path. This will help the vehicle cross the intersection and drive along a designated GPS route.

## Research Paper
If you find this repo helpful for your work, consider citing our paper:

`“Lane Keeping and Navigation of a Self-driving RC Car Based on Image Semantic Segmentation and GPS Fusion | IEEE Conference Publication | IEEE Xplore,” ieeexplore.ieee.org. https://ieeexplore.ieee.org/document/9989054.`
‌
## References
`https://github.com/dctian/DeepPiCar.git`
`https://github.com/olliematthews/phone_animation.git`
