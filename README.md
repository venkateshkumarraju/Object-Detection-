# Object Detection Project Using YOLO 11

## Table of Contents
Introduction
Dataset
Installation
Training
Inference
Evaluation
Running on Video
Results
License
## Introduction
This project demonstrates object detection using a YOLO model for detecting vehicle registration plates. The model is trained on a custom dataset of images containing license plates, and the bounding boxes are predicted using YOLO11 architecture.

## Dataset
The dataset consists of vehicle registration plates with corresponding labels. It can be downloaded here.
The directory structure is as follows:


```
Dataset
├── train
│   └── Vehicle registration plate
│       └── Label
└── validation
    └── Vehicle registration plate
        └── Label
```
Each .jpg image has a corresponding .txt file with bounding box data in the format xmin, ymin, xmax, ymax.

## Installation

```
%pip install ultralytics
import ultralytics
ultralytics.checks()
```

## Training
Prepare the dataset by setting up the paths to your images and labels in the data.yaml file:

yaml
```
%%writefile data.yaml
path: '/kaggle/working/datatset' # dataset root dir
train: '/kaggle/working/datatset/train/Vehicle registration plate'
val: '/kaggle/working/datatset/validation/Vehicle registration plate'
nc: 1
names: ['reg plate']
```
Start the training using YOLO:

```
yolo train model=yolo11n.pt data='data.yaml' epochs=50 imgsz=640
```
## Inference
To run inference on images from the validation dataset:

```
yolo task=detect mode=predict model='/path/to/best.pt' imgsz=640 source='/path/to/validation'
```
## Evaluation
Evaluate your model's performance using COCO evaluation metrics:


## Running on Video
To run inference on a video:

```
yolo task=detect mode=predict model='/path/to/best.pt' source='/path/to/input-video.mp4'
```
The video will output with bounding boxes around detected objects.

## Results
The model was able to achieve AP > 0.5 on the validation dataset, with the following performance:

AP50: 0.886
AP75: 0.629
AR: 0.633
## License
This project is licensed under the MIT License.

