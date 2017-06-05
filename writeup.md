# **Finding Lane Lines on the Road** 

## Writeup

### Project Writeup.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./output_test_images/solidWhiteCurve/step1_gray.jpg "step1_gray"


[image2]: ./output_test_images/solidWhiteCurve/step2_blur.jpg "step2_blur"


[image3]: ./output_test_images/solidWhiteCurve/step3_canny_edges.jpg "step3_canny_edges"


[image4]: ./output_test_images/solidWhiteCurve/step4_masked_edges.jpg "step4_masked_edges"


[image5]: ./output_test_images/solidWhiteCurve/step5_hough_lines.jpg "step5_hough_lines"


[image6]: ./output_test_images/solidWhiteCurve/step6_left_lane.jpg "step6_left_lane"


[image7]: ./output_test_images/solidWhiteCurve/step7_final_lanes.jpg "step7_final_lanes"


[image8]: ./output_test_images/solidWhiteCurve/step8_final.jpg "step8_final"

---

### Reflection

### 1. Pipeline Description.

My pipeline consisted of 8 steps.
Step 1 - I converted the image to grayscale.
![alt text][image1]
Step 2 - I blurred the image so as to better prepare it for edge detection.
![alt text][image2]
Step 3 - I applied the Canny edge detection algorithm.
![alt text][image3]
Step 4 - I used a mask to retrieve only the region of interest.
![alt text][image4]
Step 5 - Applied Hough transform to get the lines from points in above image. Here's showing the lines returned:
![alt text][image5]
Step 6 - In order to draw a single line on the left and right lanes, I first split the lines returned into ones with negative slope and ones with positive slope. Ones with negative slope are left lines and ones with positive slope are right lines. 
Next, I calculated average slope of left lines and right lines. Also calculated endpoints of left and right lines. If the y co-ordinate of bottom endpoints is not equal to hight of image, then I used the slope to extend the line till the bottom of the image.
Here's showing left and right lane lines:
![alt text][image7]
Step 7 - Here's showing lanes on the original image:
![alt text][image8]

### 2. Potential shortcomings with my current pipeline
I see sometimes the right lane detects upper endpoint somewhere on the left of the image and thus skews the right lane considerably. This only happens at the last step of extrapolation. So looks like these is some bug witch I could not figure out.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use the extrapolation in its own function line draw_lines instead of current inline implementation.

Another potential improvement could be to use python slicing instead of for loops; I need to brush up my python.
