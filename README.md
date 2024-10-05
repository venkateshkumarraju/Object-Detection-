# Object Detection Project Using YOLO 11

## Table of Contents
Introduction

Dataset

Installation

Training

Inference

Evaluation Result

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
![image](https://github.com/user-attachments/assets/25868d39-29d5-491b-9db1-9f562a536da4)

## Evaluation Result
Evaluate your model's performance using COCO evaluation metrics:

Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.671

 Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.910
 
 Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.801
 
 Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.338
 
 Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.735
 
 Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.796
 
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.609
 
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.737
 
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.743
 
 Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = 0.472
 
 Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = 0.813
 
 Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.845
 
COCO Metrics: [0.6710575400833589, 0.9095128113722087, 0.8007368050482824, 0.3376046941597078, 0.7354509923152637, 0.7964158952591477, 0.608984375, 0.7373046875, 0.742578125, 0.4715447154471545, 0.8132352941176471, 0.8448648648648648]

## Running on Video
To run inference on a video:

```
yolo task=detect mode=predict model='/path/to/best.pt' source='/path/to/input-video.mp4'
```
The video will output with bounding boxes around detected objects.


https://github.com/user-attachments/assets/2b0ea3bc-ede6-4cf6-924b-6426b1f4ea78



## License
This project is licensed under the MIT License.

