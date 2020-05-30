# OpenCV age detection with deep learning 
 Automatic age detection/prediction using OpenCV, Deep Learning, and Python.

### Code Requirements
The example code is in Python ([version 3.6](https://www.python.org/download/releases/3.6/) or higher will work). 

### Dependencies

1) import cv2
2) import imutils
3) import numpy


### Description

A computer vision system that can Automatically predicting age in static image files and real-time video streams with reasonably high accuracy. Predicted age would be a classification of age in a form age buckets e.g (15-20) for a teenager.

### What is age detection?

 
 ![age detection](https://github.com/msalmankhaliq/Age-detector/blob/master/opencv_age_detection_examples.jpg)

Age detection is the process of automatically discerning the age of a person solely from a photo of their face.

### Implementation

Typically, you’ll see age detection implemented as a two-stage process:

    *Stage #1: Detect faces in the input image/video stream
    *Stage #2: Extract the face Region of Interest (ROI), and apply the age detector algorithm to predict the age of the person

For Stage #1, any face detector capable of producing bounding boxes for faces in an image can be used, including but not limited to Haar cascades, HOG + Linear SVM, Single Shot Detectors (SSDs), etc.

Exactly which face detector you use depends on your project:

    *Haar cascades will be very fast and capable of running in real-time on embedded devices — the problem is that they are less accurate and highly prone to false-positive detections
    *HOG + Linear SVM models are more accurate than Haar cascades but are slower. They also aren’t as tolerant with occlusion (i.e., not all of the face visible) or viewpoint changes (i.e., different views of the face)
    *Deep learning-based face detectors are the most robust and will give you the best accuracy, but require even more computational resources than both Haar cascades and HOG + Linear SVMs

When choosing a face detector for your application, take the time to consider your project requirements — is speed or accuracy more important for your use case? I also recommend running a few experiments with each of the face detectors so you can let the empirical results guide your decisions.

Once your face detector has produced the bounding box coordinates of the face in the image/video stream, you can move on to Stage #2 — identifying the age of the person.

Given the bounding box (x, y)-coordinates of the face, you first extract the face ROI, ignoring the rest of the image/frame. Doing so allows the age detector to focus solely on the person’s face and not any other irrelevant “noise” in the image.

The face ROI is then passed through the model, yielding the actual age prediction.

There are a number of age detector algorithms, but the most popular ones are deep learning-based age detectors so we used it.

#### age detector model

 ![age detection algorithm](https://github.com/msalmankhaliq/Age-detector/blob/master/opencv_age_detection_arch.png)
 
We are using a pre-trained age detector model implemented and trained by Levi and Hassner usinf very famous Adience Dataset in their 2015 publication, Age and Gender Classification Using Convolutional Neural Networks.

For more information, [see](https://talhassner.github.io/home/publication/2015_CVPR/)

### Examples / outputs
![age detection example 1](https://github.com/msalmankhaliq/Age-detector/blob/master/output%202.PNG)

Above image is mine. The model is predicting my age correctly in the bucket of 19-24 as I am 21.

![age detection example 2](https://github.com/msalmankhaliq/Age-detector/blob/master/output.PNG)

Above image is correctly predicted by the model as the kid in the picture looks 8-12 years old.

### License 

 Licensed under the Apache License, Version 2.0. Copyright 2019.

