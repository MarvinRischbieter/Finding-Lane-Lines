# **Finding Lane Lines on the Road**

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./test_images_output/gray.jpg "Gray"
[image3]: ./test_images_output/gaussian_blur.jpg "Gaussian Blur"
[image4]: ./test_images_output/canny_edge.jpg "Cany Edge"
[image5]: ./test_images_output/interest_region.jpg "Interest Region"
[image6]: ./test_images_output/hough_lines.jpg "Hough Lines"
[image7]: ./test_images_output/final_image.jpg "Final Image"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps.

First I converted the images to a grayscale using the grayscale helper function.

The result:
![alt text][image2]

The second step was to convert the images and apply a blue filter with a specific kernel size.

The result:
![alt text][image3]

The third step I did was to apply the canny function to the image.

The result:
![alt text][image4]

The fourth step was to select only a region of the image that we will work with so the computer doesn't have to process all the image on the next step.

The result after selecting only the region of interest:
![alt text][image5]

The next step was to draw the Hough lines on the image.

Hough Images:
![alt text][image6]

And in the last step I used weighted_image() function to draw the semi-transparent lane lines. 

The Final Result:
![alt text][image7]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function in the next way: I used a function called lane_lines() that has as an argument the image and the lines. It returns the left and the right line separated. Inside the lane_lines() function I used an another function which is average_slope_intercept() which is used to calculate the average slope and interecept. By calling this function in lane_lines() I could get the average slope and intercept for the left and the right line. After that I used an another function which is make_line_points() that converted the slope and intercept into a line. So I had the average left and right lines from the lane_lines() function. After that I was just able to get the points of every line and to draw the line using the line() function from cv2 library.

### 2. Identify potential shortcomings with your current pipeline

A potential shortcoming would be that the camera would change on every image. In this case the lanes could be out of the interest region and they wouldn't be recognized.


### 3. Suggest possible improvements to your pipeline

A good improvement would be to change the pipeline so it could display also curve lines.

And for sure an another good improvement would be to improve the pipeline so that it could work on different camera positions and to detect the lines regardless of where is the camera placed.
