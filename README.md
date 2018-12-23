# **Finding Lane Lines on the Road** 

## Writeup

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following important steps. 
    
   1. Converting the images to grayscale.
   2. Applying the Gaussian blur to the images.
   3. Applying Canny edge detection
   4. Masking the images through region of interest.(Triangular region of interest)
   5. Appplying the Hough transform to identify lines from the masked images.
   6. Drawing the right and left lane lines through averaging of lines from hough transform. 
   7. Merging the lane lines with the the  initial test images.


In order to draw a single line on the left and right lanes, I modified the draw_lines() function. The function does the following steps.

   1. Calculate the slopes of all the lines.
   2. Separate the lines to right and left based on slopes.
   3. Averaging separately the left and right slopes.
   4. Averaging separately, all the X & Y coordinates on the left and X & Y coordinates on the right.
   5. Calculating the new intercepts for creating the new left and right lines.
   6. Calculating the end points using the intercepts and mean slopes.
   7. Drawing the lines with the new extrapolated end points.


### 2. Identify potential shortcomings with your current pipeline
  
  The pipeline works on the first 2 videos with decent accuracy but I am getting NAN error on the optional video challenge. I tried many parameter changes but not able to rectify the issue. I think, the pipeline is recognising the lines in some frames which leads to zero slopes and to NAN error.
  
The pipeline might also have issues with drawing lanes on sharper turns.
 

### 3. Suggest possible improvements to your pipeline

A possible improvement would beto have finding optimal values for parameters for Hough transform, guassian blur, canny detection rather than being programmer dependent. It might be better if a machine learning program using various computer vision techniques for identifying optimal values for various conditions. 

Another potential improvement could be to make it accurately identify the lanes without the flickering I find in my output videos, may be by having more color gradient identifying functions, which currently I am not technically sound to create.  
