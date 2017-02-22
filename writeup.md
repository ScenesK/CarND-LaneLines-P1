#**Finding Lane Lines on the Road**

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of 9 steps.

1. Image resize (960, 540)
1. Gaussian blur
1. Saturation and Brightness extraction by color conversion to HSV
1. Edge detection in region of interest
1. Hough line transformation
1. Line choice by angle
1. Merge lines into one by weighted average
1. Image resize (original size)
1. Line drawing

It seemed to be too hard to detect lines in grayscale image when in shades of optional challenge, but they were clear in saturation image, so I used both saturation and brightness(grayscale).

Sometimes hough transformation detects too many noisy short lines, but longer lines are likely to be more reliable, so I calculate weighted(length ** 2) average of lines.

In order to draw a line from top to bottom of the region of interest, I just get positions according to the average line.


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be getting lost when changing lanes because I separated the region of interest into left and right. Lanes can't be detected in the middle of them.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to average among time to make positions of lines more stable.
