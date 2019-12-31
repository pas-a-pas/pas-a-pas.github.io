---
layout: post
title:  Hsv histogram 
date:   2019-12-29 15:26:00 +0900
---
A small C++ code project to calculate histogram of images using OpenCV with following features:
 * Pick interesting regions - patches - in an image. Picking goes through with numbers of images in a directory.
 * The HSV histogram of image patches is visualized in hue-saturation histogram chart.
 * Areas of patches are available later for calculating histograms with different parameters.

It can be used to build HSV histogram of human skin. Collect images of peoples under different illumination conditions. The program is running with a directory path to the image collection. It first shows each image and waits for user's input to get interesting area - skin area. Then it calculates histogram of hue and saturation of each pixels in specified areas. The chart is shown with hue along with X axis and saturation along with Y axis. The color of data point of the chart is according to an intensity of a given histogram value. For example, if all data point in the histogram has full intensity, a chart is shown like below:

![Image Alt A](/assets/img/huesaturationchart.png)

When testing the program with several skin areas, it results like below:

![Image Alt B](/assets/img/skinhistogram.png)

The full code can be found [Git hub repository](https://github.com/pas-a-pas/VisionPractice/tree/ad089108011261ff2d26fe611218baf5af02b990). Following diagram will provide a brief introduction into the code:

![Image Alt Hsv Histogram Module View](/assets/img/hsvhistogrammoduleview.png)

