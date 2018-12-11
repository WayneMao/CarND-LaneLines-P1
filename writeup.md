# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # "Image References"

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe my pipeline. As part of the description, explain how my modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used Gaussian filtering to remove noise. Third, I used Canny algorithm to extract edges. Forth, I setting a region of interest(ROI), which can  reduce processing time and increase accuracy. Finally, I used Hough transform to get lines in the ROI and I used function draw_lines() to draw lines based on the lines that get from Hough transform.

![sixresult.png](https://github.com/WayneMao/CarND-LaneLines-P1/blob/master/sixresult.png?raw=true)

In fact, I found that function draw_lines() does not perform very well. So, I decided to create a  new function to gain a better result. I named new function as carlines() to instead of  draw_lines(). In order to draw a single line on the left and right lanes, I calculated every line segments' slope. If a slope smaller than a setting value, we can think that this line segment is belong to left lanes. If a slope bigger than another setting value, we can think that this line segment is belong to right lanes. Then, I calculated weighted averaging based on different length of line segment.  After, I calculated average slope and average center point by weight, so that I can draw new lanes. The final result is shown below:

![result.png](https://github.com/WayneMao/CarND-LaneLines-P1/blob/master/result.png?raw=true)


### 2. Identify potential shortcomings with my current pipeline


One potential shortcoming would be what would happen when the current side has a shadow.

Another shortcoming could be function insensitive to clolor.


### 3. Suggest possible improvements to my pipeline

A possible improvement would be to use color space conversion.

Another potential improvement could be to further limit the slope.
