# Combine Jetbot Road Following and Collision Avoidance tasks

**Notice: This repo was created solely as a requirement for receiving the Nvidia Jetson AI Specialist Certificate**

Jetbot is an open source AI Robot based on the Nvidia Jetson Nano ([Jetbot Repository](https://github.com/NVIDIA-AI-IOT/jetbot))

It is used for educational purpose and can perform multiple tasks including Road Following, Collision Avoidance and Object Following.

## Collision Avoidance

Collision Avoidance in Jetbot is a binary classification task which consists of 2 classes ```blocked``` and ```free``` which is used to keep the Jetbot safe and avoid collisions with obstacles.  

## Road Following

Road Following in Jetbot is a regression task which teaches the Jetbot to detect a continuous target x and y which will enable the Jetbot to follow a specific path on a track.

## Road Following + Collision Avoidance

This project focuses on combining both optimized **regression** and **classification** models into one notebook to enable the Jetbot to follow a specific path on the track and at the same time also be able to avoid collisions with obstacles that come on it's way in real-time by bringing the Jetbot into a complete halt.

## How to Run

1) Collect image regression dataset, train and optimize your Road Following model using the notebooks provided in the original [Jetbot Repository](https://github.com/NVIDIA-AI-IOT/jetbot/tree/master/notebooks/road_following).

```
data_collection.pynb: Collect image regression dataset which consists of image coordinate target points x and y.
train_model.ipynb: Perform model training using ResNet18 model architecture to predict two continuous values x and y corresponding to a target point.
live_demo_build_trt.ipynb: Optimize the trained model by using TensorRT for faster inference on the Jetson Nano.
```

2) Collect image classification dataset, train and optimize your Collision Avoidance model using the notebooks provided in the original [Jetbot Repository](https://github.com/NVIDIA-AI-IOT/jetbot/tree/master/notebooks/collision_avoidance).

```
data_collection.pynb: Collect image classification dataset which consists of two classes, Blocked and Free.
train_model_resnet18.ipynb: Perform model training using ResNet18 model architecture to detect the two classes and help Jetbot to avoid collisions.
live_demo_build_trt.ipynb: Optimize the trained model using TensorRT for faster inference on the Jetson Nano.
```

**Note**: For Collision Avoidance, the ```Blocked``` class should include images of obstacles such as **vehicles**, **people**, **stop signs** etc. captured on the track, meanwhile the ```Free``` class should include background images of the empty track where the Jetbot should be free to move around in.

3) Save the TRT models inside the "combine_scripts" folder and run the "RoadFollowing+CollisionAvoidance.ipynb" notebook.

**Note**: The object detection threshold can be adjusted using the "blocked threshold" slider and the time for stop (after an object has been removed) can be adjusted using the "time for stop" slider.

## Live Demo

![jetbot-gif1-small-10mb](https://user-images.githubusercontent.com/68045710/119227944-040b8980-bb43-11eb-9ea0-78e677f407ff.gif)

Example of images used for training both models can be found in this [link](https://drive.google.com/drive/folders/1Dry1vjTSaar014Pxlp1s3_ckTt5B6zeE).
