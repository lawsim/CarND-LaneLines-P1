# **Finding Lane Lines on the Road** 

## Writeup 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[pipeline1]: ./test_images_output/solidWhiteCurve_1_canny_edges.jpg "Pipeline 1 - Canny"
[pipeline2]: ./test_images_output/solidWhiteCurve_2_verify_masking.jpg "Pipeline 2 - Verify Masking"
[pipeline3]: ./test_images_output/solidWhiteCurve_3_masked_edges.jpg "Pipeline 3 - Mask Edges"
[pipeline4]: ./test_images_output/solidWhiteCurve_4_hough.jpg "Pipeline 4 - Hough Transform"
[pipeline5]: ./test_images_output/solidWhiteCurve_5_final.jpg "Pipeline 5 - Final Product"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

1. I converted the images to grayscale.

2. I applied Canny CV2
![alt text][pipeline1]

3. Here I masked the edges.  I also created another image to draw lines and verify that my mask was appropriate.
![alt text][pipeline2]
![alt text][pipeline3]

4. Applied the Hough transform to the image.  In order to draw single lines I modified the draw_lines function to get the minimum and maximum points, calculate the slope and y-intercept and then calculate new x points based on statically set y values.
![alt text][pipeline4]

5. Composited the hough lines onto the original image to make the final output.
![alt text][pipeline5]


### 2. Identify potential shortcomings with your current pipeline


* When I modified draw_lines() to draw solid lines, the lines are now a bit "twitchier" because they are computed from the found min/max x and y values.
* I am using statically configured values for the masking and line lengths, somehow finding optimal values for these seems like a better solution.
* I assume a straight line in draw_lines, I don't believe this will handle a sharp curve well.


### 3. Suggest possible improvements to your pipeline

* Finding a way to smooth the lines between frames seems like it would result in more accurate lines.  Perhaps only some specified maximum change or deviation?
* If I modified draw_lines() further to track and connect line segments rather than drawing one large line this seems like it could be a better solution to getting lines to track better.
