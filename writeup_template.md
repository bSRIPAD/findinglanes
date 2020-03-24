# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

* Convert the images to grayscale
* Perform Gausian smoothing and apply Canny edge detection
* Select region of interest and mask other areas of the image
* Apply Hough Transform to detect lane lines
* Superimpose the lane lines on the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
* Calculated slope and center of each line. Then based on the slope, sort it into right or left lane line
* Calculate the average slope and the center of right and left lane
* Then using the Y coordinates, based on Region of Interest, figure out the X cordinates using the avg slope and center point of lane lines [equation used: (y-y') = M (x-x')]

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline
* The region of interest in Image masking is static, hence it can only work in specific scenarios
* Slope conditions used for detecting right and left lanes do not work in case of a curve in the road

### 3. Suggest possible improvements to your pipeline
* Make the image mask selection dynamic, so that it could work in different scenarios
* Modify the slope conditions, so that they work with curve in the road
