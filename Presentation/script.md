- 1. **Introduction**

  - We both worked on field of region based CNN's. In the next slides you will find out what it's all about.
  - Structure of lecture:

    - 1. I start with the clarification of object detection, explain how it works and show challenges
    - 2. and then head over to RCNN
    - 3. Tran starts with explaining the next architecture fast rcnn
    - 4. And will also explain faster rcnn
    - 5. then we achieved the end of our presentation

- 2. **Object detection**

  - I demonstrate object detection with help of my laptop camera
  - You try to detect all classes with which the model was trained which appear in the image
  - the model which detects me here as an person was trained on persons
  - Embedd this one somehow to make clear why ==== Since Convolution Neural Network (CNN) with a fully connected layer is not able to deal with the frequency of occurrence and multi objects. So, one way could be that we use a sliding window brute force search to select a region and apply the CNN model on that, but the problem of this approach is that the same object can be represented in an image with different sizes and different aspect ratio. While considering these factors we have a lot of region proposals and if we apply deep learning (CNN) on all those regions that would computationally very expensive.

- 3. **How does object detection work?**

  - 1. Large set of bounding boxes
    - 1. take image
    - 2. run algorithm for generation of a lot of bounding boxes
      - bouding boxes are the small boxes which getting generated
    - 3. classify all of the visual features
  - 1. All overlapping bounting boxes are combined to one and final results getting showned.

- 4. **How to select bounding boxes**

  - 1. Intersection over Union
    - The boxes with label which getting shown in the last step of our typical object detection need to be shown as accurate as possible
    - for that we compare bounding boxes
    - Ground truth is created which is the best prediction for an image
    - IoU is area of overlap divided by union of ground truth and prediction
    - the higher the result the better the match between prediction and ground truth
  - 2. Non-max suppression
    - Scenario where you have all the classified objects from your object detection with bounding box and objectiveness score
    - Algorithm
      - 1. select highest scoring box
      - 2. Eliminate lower-scoring boxes with IoU > threshold (e.g. 0.7)
        - threshold can be any but needs to be realistic to remove all overlapping images
      - 3. If any boxes remain, GOTO 1

- 5. **Metrics**

  - 1. **average precision**
  - 2. **mean average precision**

- 6. **Overview of famous models**

  - horizontal axis is time and vertical axis is box ap (TP/total positiv results (the more FP the higher box ap))
  - it is possible to see a fast increase in precision of models

- 7. **Challenges**

  - 1. Object localisation
    - Problem of finding correct x and y coordinates around object of interest
  - 2. Viewpoint variation
    - object has different angle for example
  - 3. Multiple aspect ratios and spatial sizes
    - just reference to headline and and let image be present
  - 4. Deformation
    - human in different positions
  - 5. Occlusion
    - something conceals the target object
  - 6. Lighting
    - objects can look different when light falls on them
  - 7. Cluttered or textured background
    - example of tools
  - 8. Intra class variation
    - you have the same class but variations between the class like the chairs from the picture
  - 9. Real time detection speed
    - can be difficult because of the high speed which is required for detection algrithms
  - 10. Limited data
    - having not enough data available is always a problem

- **RCNN** (slide 9 https://web.eecs.umich.edu/~justincj/slides/eecs498/WI2022/598_WI2022_lecture14.pdf), (slide 61 https://web.eecs.umich.edu/~justincj/slides/eecs498/WI2022/598_WI2022_lecture13.pdf
  - https://d2l.ai/chapter_computer-vision/rcnn.html)

  1. After talking about object detection in general we look now into a specific techniques of object detection - RCNN's
  2. RCNN stands for region based CNN and is a object detection technique
  3. First you have an input image from where you eventually detect something from.
  4. Selective search is applied to detect multiple region proposals

  - 1. Region proposal
    - smaller regions of image that possibly contains the objects we are searching for in input image
  - 2. Selective search
    - Algorithm to create this region proposals
    - predicts approx 2000 of this (why is 2000 good)

  5. The region proposals getting warped into image region
  6. This regions getting forwarded through an convolutional neural network.
  7. The result of the neural network determines the class of the region.
  8. With the transform which is predicted from the model the correct region proposal or bounding box gets created

- **Challenges** (https://www.geeksforgeeks.org/r-cnn-region-based-cnns/)

  - Regionproposal are not detected from learning algorithm

- **Questions**
  - 3. 1. 3. how is that happening from the prior step?
  - 5. 1. Dont understand calculation of example
