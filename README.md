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

# Define the features extraction functions

Tunning the functions given in the course I got decent results. See below the functions I used and some example of the outputs I got from them:

* Spatial binned feature extraction function:
The plots below show the Binned features extracted from cars and not cars images when in 'LUV' color space

![imagen](https://user-images.githubusercontent.com/41348711/46920359-79a73480-cfed-11e8-9a1d-91481e08f0a7.png)

* Color Histogram feature extraction function:
The plots below show the YCrCb color space Histogram of a car image. Note that the bin range is 0-1.

![imagen](https://user-images.githubusercontent.com/41348711/46920413-487b3400-cfee-11e8-9b2f-6005ecafc493.png)

* Histogram of gradient feature extraction function:

![imagen](https://user-images.githubusercontent.com/41348711/46970090-58f7e100-d0b8-11e8-9dae-bad46e592db3.png)

# Define the features extraction functions

Covert color function is also used in combination with the above mentioned functions to get features of images of different color spaces
After some tunning I got a set of parameters with a good accuracy:

| Spatial Bin 	        					| 
|:------------------------------------------------------------------:| 
|       	 YCrCb color image input  							| 
|                         Spatial size = (16,16)	| 


| Color Histogram |  
|:-----------------------------------------------------------------:| 
|    YCrCb color image input                                     |
|                       Number of bins = 32	| 
|                       Bins range = (0,1)	| 



| Histogram of Gradients (HOG)                                         |
|:------------------------------------------------------------------:| 
|                         YCrCb color image input  	| 
|                         Number of orientations = 12	| 
|                       Pixels per cell = 8	| 
|                         Cells per block = 2	| 
|                         HOG channels = ALL	| 

![imagen](https://user-images.githubusercontent.com/41348711/46921441-8af73d80-cffb-11e8-96ed-eee49fd46468.png)


# Extract features of the cars and Nor cars data sets:

![imagen](https://user-images.githubusercontent.com/41348711/46921457-d7427d80-cffb-11e8-87b0-efdf8940b88b.png)


# Normalization:
At this step the training data set is Normalized using the standard scalarer function from sklearn.
The dataset is splitted in 80%-Training set 20%-Test set

![imagen](https://user-images.githubusercontent.com/41348711/46921535-f68dda80-cffc-11e8-93f3-83e95803a564.png)

# Model Fitting: 
I used for this linear SVR fitting , as recommended in the course. I was able to get 99% accuracy

![imagen](https://user-images.githubusercontent.com/41348711/46921587-8e8bc400-cffd-11e8-8879-2f915ff5d1ec.png)

# Find cars Function
I just tunned the fucntion given on the course, setting the same parameters used when training the model

![imagen](https://user-images.githubusercontent.com/41348711/46921900-8d5c9600-d001-11e8-9540-596241a48057.png)

# Heat functions
The pipeline detects relatively good vehicles but has some false positives. To solve this, Heat fucntions are added to the pipeline . These functions will keep overlaping detections but discard the single detections. These functions are copied from the the course.
* Add Heat: Returns the Heat map
* Apply Threshold - In my case I used threshold =2, so only pixels with some overlapping are kept
* Draw labeled Boxes - Using the boxes inside the threshold, define new boxes to be drawn over the raw image

![imagen](https://user-images.githubusercontent.com/41348711/46923489-d8ce6e80-d018-11e8-9fea-c61f23e645e8.png)

# Define the process image pipeline
This pipeline just gathers all the functions above defined. 
I defined different searchs:

![imagen](https://user-images.githubusercontent.com/41348711/46923353-c3f0db80-d016-11e8-9a67-8ab24b58ce93.png)

![imagen](https://user-images.githubusercontent.com/41348711/46923204-bf2b2800-d014-11e8-8a39-bd04f7150a70.png)

# Apply above mentioned pipeline to the project video 

![imagen](https://user-images.githubusercontent.com/41348711/46923379-1df1a100-d017-11e8-863c-0cfd00028f69.png)
