# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I blured grayscale image in order to make gradients smother and after then I apllied Canny filter to obtain gradient of image. Than I selected region ofinterest, since gradient image contains clutters and noise. After that I applied hough transform to gradients of lane to line to connect the dots and get solid lines. And finally I drawed detected lines on originall image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by filtering all deteceted lines by hough transform to lines corresponding to left lane and to lines corresponding to right lane. Decision rule was simple: if coordinate belongs to left half of the image than it is corresponds to left lane otherwise it's corresponds to right lane. After that I fitted all coordinates from that lines to two lines using least squares method. 


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One main shortcoming would be that to separete deteceted lines current pipeline just split them on left and right half of images. This pipeline wouldn't detect lanes properly on crooks and crossroads.

Another shortcoming could be that pipeline fit coordinates with polynome of first degree. So it couldn't generalize on crooks and lanes of more complicated shaoes.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use polynomes of higher degree to fit coordinates

Another potential improvement could be to use deep convolution neural network to detect lines. Because they are more robust to ligh condition and could generalize more complicated shapes
