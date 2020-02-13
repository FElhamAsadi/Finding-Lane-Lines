# **Finding Lane Lines on the Road** 


### Reflection

### 1. My Pipeline

The goal of this project is finding lane lines on the road using Python and OpenCV. My lane finder pipline consists of the following steps:
* Loading the image (each frame)
* Converting to the gray scale
* Noise reduction using OpenCV Guassian smoothing
* Detecting the edges using Canny
* Selecting the region of interest by defining a trapezoid aligned with our lane (region masking)
* Finding all lines in the region-masked image using Hough transform line detection (Several parameters in this part have been tunned)

The new function called Hard_Line has been added to the helper functions for identifying the full extent of the lane (I did not change draw-line function). There are several Hough line segments detected for a lane line. Also, some lane lines are only partially recognized. Hence, first I found the average of Hough line segments in each lane line (the line segments with the positive slope belong to the left line and the negative slope belong to the right line) and then I extrapolated this average line to cover full lane line length.


### 2. Potential shortcomings with my current pipeline
This method will not give a good result for a sharp bending. In addition, it fails to find the lines accurately in presence of a shade in the image.


### 3. Suggest possible improvements to your pipeline
A possible improvement would be implementing the color masking to filter the white and the yellow color seperately. Using HSL color space, we can select particular range of each channels (Hue, Saturation and Light) which define only these two colors and eliminate useless data in the image. This color mask should be applied after loading the image and before converting it to the gray scale. 

