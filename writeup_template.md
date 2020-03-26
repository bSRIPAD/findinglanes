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

[image2]: ./test_images_output/solidWhiteCurve.jpg_after.jpg

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
My pipeline consists of series of steps from taking image as an input to marking lane line in the image . At first convert the input image to gray scale ,then perform the guassian  smoothing to suppress the noise and apply the canny edge detection algorithm to detect the edges in the images .Then select the 4 vertices which is suitbale to area of intrest then mask other region in the image . Then apply the Hough transform to the image to detect lane lines.After detecting superimpose detected lane lines on the original image .

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
