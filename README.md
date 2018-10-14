# SDCND_Vehicle_Detection_and_Tracking

Project 5: Vehicle Detection and Tracking

The goals / steps of this project are the following:

* Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier Linear SVM classifier
* Optionally, you can also apply a color transform and append binned color features, as well as histograms of color, to your HOG feature vector.
* Note: for those first two steps don't forget to normalize your features and randomize a selection for training and testing.
* Implement a sliding-window technique and use your trained classifier to search for vehicles in images.
* Run your pipeline on a video stream (start with the test_video.mp4 and later implement on full project_video.mp4) and create a heat map of recurring detections frame by frame to reject outliers and follow detected vehicles.
* Estimate a bounding box for vehicles detected.

# Import  the data sets and plot some pictures

At this step I just imported the data sets (car and not cars) and plotted 8 random images of each of them:

![imagen](https://user-images.githubusercontent.com/41348711/46919583-9c335080-cfe1-11e8-9bb9-203cfeb570d3.png)

# Define the features extraction features

Using the functions given in the course, 

* Spatial binned feature extraction function:
The plots below show the Binned features extracted from cars and not cars images when in 'LUV' color space

![imagen](https://user-images.githubusercontent.com/41348711/46920302-7cedf080-cfec-11e8-85ad-0c1695aea451.png)

* Color Histogram feature extraction function:

![imagen](https://user-images.githubusercontent.com/41348711/46920349-49f82c80-cfed-11e8-87d6-edeab5b4b881.png)

![imagen](https://user-images.githubusercontent.com/41348711/46920329-eff76700-cfec-11e8-9684-a95a989dfdff.png)

* Histogram of gradient feature extraction function: 

Covert color function is also used in combination with the above mentioned functions to get features of images of different color spaces

