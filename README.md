# Object Detection and Action Recognition for Self-Driving Vehicles

## Introduction

We provide a robust and accurate visual system for autonomous vehicles. The system is able to detect objects and identify behaviour of pedestrian, cyclist or other road users.

Object Detection [11 classes]:
- person, bicycle, car, bus,train, truck, traffic light, fire hydrant, stop sign, parking meter, bench

Behaviour Recognition [13 classes]:
- Regular actions: running, walking, jumping, waving hands
- Dangerous actions: riding a bike, riding a horse, texting message, phoning, pushing a cart, holding an umbrella, fixing a bike, fixing a car, walking the dog

The model is built on Yolo v3 but any newer version can be easily used.

## Get Ready

Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

### 1. According to the configuration of your computer, edit the Makefile and compile by the command: 
	cd darknet
	make

### 2. backup file includes all the trained weights:
	action1.weights - 13 pedestrian actions from Stanford Action Dataset - training by YOLOv2
	actionVOC.weights - 8 pedestrian actions from re-built PASCAL VOC Dataset' - training by YOLOv3
	actionVOC_544.weights - improve the resolution and generate the appropriate anchors using k means clustering
	coco_traffic_2017.weights - 14 types of objects in the traffic scenario - collected from COCO Dataset
		
Please download weights https://drive.google.com/file/d/1vXJTkrWZxue_nqbCpKQK23t48BpTWWxV/view?usp=sharing
		
### 3. cfg file includes all the network architectures and the dataset path:
	action1.cfg		action1.data
	actionVOC. cfg		actionVOC.data
	actionVOC_544.cfg	actionVOC_544.data
	coco_traffic_2017.cfg	coco_traffic_2017.data

### 4. data file includes all the category lists:
	action1.data
	actionVOC. cfg
	actionVOC_544.cfg
	coco_traffic_2017.cfg

### 5. All the dataset are too large, please download from the following links:
	Modified Stanford Action Dataset: https://drive.google.com/file/d/1w9uiDB1TDKfCcnve7ilYJ1PeXUTYg0OU/view?usp=sharing
	Modified PACSAL VOC Dataset: https://drive.google.com/file/d/1wwztVMlmmwuA8mM5K3460tvnyIizFMbv/view?usp=sharing
	Modified COCO Dataset: https://pan.baidu.com/s/1JKzGP4qGJUUgpn11ywKF2A
	Full COCO Dataset: http://cocodataset.org/#download	- if you want to add or remove some categories you can download 'annotations' 'train2017' 'val2017'

### 6. Command for detecting using the trained models: (replace '~' with the specific name of the model you want to use)

Detect in images:
			
```
./darknet detector test cfg/~.data cfg/~.cfg backup/~.weights test_image.jpg
```

detect in videos:

```
./darknet detector demo cfg/~.data cfg/~.cfg backup/~.weights test_video.mp4
```
### 7. Command for training a new model: (replace '~' with the specific name of your model)
by YOLOv3: 
```
./darknet detector train cfg/~.data cfg/~.cfg darknet53.conv.74
```
by YOLOv2:
```
./darknet detector train cfg/~.data cfg/~.cfg darknet19_448.conv.23
```


## Visualisation

### Object Detection

<img src="src/objectDet.png" width="400">

### Action Recognition

<img src="src/actRec1.png" width="550">


<img src="src/actRec2.png" width="600">




## For more information see the [Darknet project website](http://pjreddie.com/darknet).
