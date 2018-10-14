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


Covert color function is also used in combination with the above mentioned functions to get features of images of different color spaces
After some tunning I got a set of parameters with a good accuracy:
| Feature Layer        		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Spatial Bin       	| YCrCb color image   							| 
|                        | Spatial size = (16,16)	| 
|:---------------------:|:---------------------------------------------:| 
| Color Histogram        |
| RELU	activ. fucntion				|												|
| Max pooling	      	| 2x2 stride,  valid padding,  outputs 14x14x6 	|
| Convolution 5x5	    | 1x1 stride, valid padding, outputs 10x10x6 	|
| RELU	activ. fucntion				|			
| Max pooling	      	| 2x2 stride,  valid padding,  outputs 5x5x16 	|
| Flatten				|
| Fully connected		|         							outputs 120		|
| RELU	activ. fucntion				|		
| Dropout				|	0.5 |	
| Fully connected		|         							outputs 84		|
| RELU	activ. fucntion				|		
| Fully connected		|         							outputs 43		|	
