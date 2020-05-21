## README
---
**Object Detection YOLOv3**

[//]: # (Image References)

[image1]: .YOLOv3_implementation/examples/det_andy_murray.jpg "Andy Murray with Objects detected"
[image2]: .YOLOv3_implementation/examples/bball_1.png "Basketball example 1"
[image3]: .YOLOv3_implementation/examples/bball_2.png "Basketball example 2"
[image4]: .YOLOv3_implementation/examples/bball_3.png "Basketball example 3"


### Intro

YOLO is a very effective approach to object detection. I wanted to follow though this tutorial https://blog.paperspace.com/tag/series-yolo/ by AYOOSH KATHURIA and create an implemenation of YOLOv3 in Pytorch.

If you're just looking for an implementation of YOLO then going direct to the YOLO website is recommended. I wanted to walk through the implementation to better understand it.

#### Application
I wanted to apply YOLOv3 to both static and video sports events and understand for myself how well it performs. There are a number of reasons why being able to track objects in sports is useful. One use cases is the ability to automate data gathering from a video. 

I will hopefully soon have a write up on my blog.

### Set up

All instructions for getting started can be found in the original tutorial, but for a quick setup from this source:

You'll need to download the pre-trained weights of the network from https://pjreddie.com/media/files/yolov3.weights

- For object detection with images, navigate to your directory on the command line and run:
		
``` python detect.py --images <FILEPATH> ```

I decided it would be useful to have an implementation available in a Jupyter notebook to allow for easier experiementation. This version also saves down a copy of the annotated video. 'video_experimentation.ipynb' will allow you to test different videos and output the results in the notebook. 

### Results

As a simple test of the system I tested the solution on a static image. 

![alt text][image1]

The tennis ball, racket and person are the three key items in this picture and they're all successfully identified.

This is also a good example of YOLO being able to deal with overlapping objects and objects of various size.

#### Video implementation

For the video test I used an a video from https://www.videvo.net/video/running-basketball-players/8135/. But you could use whatever video you'd like. 

Here are 4 screen shots from the annotated video to highlight a couple of the challenges:

The first image shows the process performing well. 

![alt text][image2]

This second image shows that whilst the picture is nearly identical to the first the basketball is not currently detected. This type of implementation takes each frame as independant. For an application where always keeping track of this ball would be really important a method could applied that takes into account what was in the previous frames. The challenge with this is that it will become computationally more challenging. 

![alt text][image3]

This image highlights two challenges. One is that the ball is no longer detected whilst partially hidden by the carrier. 
The second being that the algorithm has created one large bounding box around the crowd and identified it as a person. 

![alt text][image4] 

These are just a couple of the challenges still facing object detection and it's worth exploring the Confidence and NMS (non-max suppression) thresholds in the code, depending on your application.


 
