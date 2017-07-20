# **Finding Lane Lines on the Road** 


---

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 

- Step 1: Convert the images to Grayscale.
- Step 2: Applied Gaussian Blur to the images.
- Step 3: Applied Canny edge detection.
- Step 4: Set a specific area (Masking) to process only that region of interest.
- Step 5: Ran the Hough transform to the lines.
- Step 6: Smoothing the result with a moving average filter and plot the lines on top of the image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

- Calculate the current slope
- Checked if the value of the slope is negative or positive (right or left)
- Stored the current value of the coordinates
- Calculate the average of negative and positive slope
- Using the slope and intercept, extend the lines
- Update the moving average of the last few lines and the new lines
- Plot the moving average lines

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One shortcoming is that the region of interest is static, for this reason, it will work in just some specific cases.
Another shortcoming is that using the average of the slope is very limited, for example, that will not work if the car is passing on a zone with a curve.

### 3. Suggest possible improvements to your pipeline

The first improvement should be define a dynamic region of interest.
A second improvement should be recalculate the slope of the line and identify if that slope is changing very fast. If that is the case, a curve could be identified in that case.
