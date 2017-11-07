# **Finding Lane Lines on the Road** 

## Writeup 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work in a written report

[image1]: ./examples/solidWhiteCurve_blur.jpg "Gaussian blur"

[image2]: ./examples/solidWhiteCurve_RG.jpg "Drop blue channel"

[image3]: ./examples/solidWhiteCurve_ROI.jpg "ROI"

[image4]: ./examples/solidWhiteCurve_edge.jpg "Edge detection"

[image5]: ./examples/solidWhiteCurve_hough.jpg "Hough transformation"

[image6]: ./examples/solidWhiteCurve_out.jpg "Image with road lines detected"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:

(1) Apply Gaussian blue function to the image in order to reducing the noise. The kernel size can be set as 3 or 5. A smaller kernel size is sufficient to reduce the noise. Too larger size makes it hard for edge detection.

![Gaussian Blur][image1]

(2) Set the blue color channel to be 0. The road lines are more commom to be drawn in yellow and white. To make the edge detection more efficient, I drop the blue channel by setting all numbers as 0.

![RG Channel][image2]

(3) Select a trapezoid area with its 4 points set as (0, 540), (548, 265), (548, 275), (960, 540). Selecting a ROI area avoids false detection of road lane linse.

![ROI][image3]

(4) Apply Canny edge detection to extract edge lines in the image. I set the low and the high threshold as 50 and 150 respectively.

![Edge Detection][image4]

(5) Use hough transformation to make edge lines smooth and continous. The shape of road lines is rectangle with a larger length to width ratio. Thus, a continuous linear line in the image is more likely to be a road lane line.

![Hough Transformation][image5]

(6) In order to draw a single line on the left and right lanes, I modified the draw_lines() function by picking the maximun and minimum x and y values forming all lines from the output of the previous step. The parameters are set as following: (rho = 2, theta = pi/180, threshold = 10, minimum line length = 50, max line gap = 30). 

!Final Image[image6]

---

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...

---

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...