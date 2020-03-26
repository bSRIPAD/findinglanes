# **Finding Lane Lines on the Road** 


Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
My pipeline consists of series of steps from taking image as an input to marking lane line in the image . At first convert the input image to gray scale ,then perform the guassian  smoothing to suppress the noise and apply the canny edge detection algorithm to detect the edges in the images .Then select the 4 vertices which is suitbale to area of intrest then mask other region in the image . Then apply the Hough transform to the image to detect lane lines.After detecting superimpose detected lane lines on the original image .

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
* Calculated slope and center of each line. Then based on the slope, sort it into right or left lane line
* Calculate the average slope and the center of right and left lane
* Then using the Y coordinates, based on Region of Interest, figure out the X cordinates using the avg slope and center point of lane lines [equation used: (y-y') = M (x-x')]


### 2. Identify potential shortcomings with your current pipeline
* The region of interest in Image masking is static, hence it can only work in specific scenarios
* Slope conditions used for detecting right and left lanes do not work in case of a curve in the road

### 3. Suggest possible improvements to your pipeline
* Make the image mask selection dynamic, so that it could work in different scenarios
* Modify the slope conditions, so that they work with curve in the road



