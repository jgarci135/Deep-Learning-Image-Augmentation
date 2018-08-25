# Practicum-II
Computer Vision for Medical Images

<p align="center">
  <img width="450" height="250" src="https://gdb.voanews.com/A13A1BE6-4C25-48DF-B44F-253481BD4333_w1023_r1_s.jpg">
</p>

## Classification of Medical image files


**Description of data:**
The images were obtained from video of medical procedures.  Due to the nature of the images and the current development within the company the images and the specific objective cannot be shared and is protected by an NDA.  There is an interest in specific features that occur at a specific time point.  The images collected are roughly collected from the same time point and have 5 different classifications present.  The classifications will be labeled simply 0,1,2,3,4+ or labeled with a PN prefix.  This is a limited data set as there is only 3732 samples present. 

**Augmented Images**
Augmented images have been generated through heavy augmentation methods to added to better balance the data as well as noise to the medical images.  The total number are now different with the total number of images in the data set equal to 11553. Test set is now 10223 and the training/validation set now contains 1330 images.

**Objective:**
The objective of this project is to accurately identify the 5 classifications with good accuracy.  This data set is a good candidate for use with transfer learning.  There are not enough samples for a convolution neural network to properly learn the defining features and will benefit from the use of models that have been trained on much larger data sets.

**MobilenetV2**
Mobilenet was used in the original project due to it lightweight applications and its ability to be used in the presence of limited resources.  MobilenetV2 was used in this project to take advantage of some of the updated architecture. The main reason for its implementation here was still for the amount of resources required to train and run on it. 

**Bottle Neck Features**
Bottle neck features were also used to help with resources and the implementation on Google Colab.  While running batch generators from Google Drive to Google Colab there is a resource over head in speed that is persistent and effects training.  A constant error occurred in this set up as an "input/output" error.  To alleviate this issue as well as train faster bottle neck features were generated using the entire MobilenetV2 architecture.  The files were large and needed to be loaded each session the Colab was used but were much easier to manage compared to the overhead errors.


## Results
Originally the model could not correctly identify any images due to the imbalance in the data set.  The result was a guess of a single class and the accuracy corresponded with the percentage that each of the classes made up the data set. This confusion matrix shows this example. Class three was expressed as the accuracy of the model. This is due to all predictions being made as class three.
<p align="center">
  <img width="450" height="500" src="https://github.com/jgarci135/Practicum-I/blob/master/Figures/Confusion%20matrix.JPG">
</p>
With the augmented images added to the data set the results changed in a positive manner.  Useful classification occurred of the medical images and the accuracy, at maximum, reached 72%. The confusion matrix that showed that many of the images were correctly classified and predicted across all classes.

## Evaluation of results
The results were better than the original project.  While fine tuning the hyper-parameters and optimizer is was apparent that the best results were limited to about 70%.  Because this project involves medical imaging the importance of accuracy is high and the expectations of the models accuracy were set to about 95% or better.  

Due to the results a reevaluation of the defined problem occurred.  As this happened the normalized confusion matrix showed there was a 95% accuracy in some cases to class 2.  Class 2 is biological normal for the medical images information.  This class is the most important and the rest can be reduced to “not normal” and be ignored.  When this occurs the accuracy of this model is really about 95%.  A simple reevaluation redefined the problem to help solve some issues using the present resources.

## Summary 
Adding the augmented images had a large impact in reducing the imbalance in the data set and resulted in positive training of the model.  The results indicated that there was not better accuracy than 72% which pushed for differing methods of measuring of success in this particular model.  Precision and recall did not highlight anymore useful information than validation accuracy. Reexamining the purpose and defined problem led to the realization that only class 2 is of interest. Not all classes must be properly classified resulting in accuracy results of class 2 images from 90-95%.  All other classes misclassified as class 2 would have to be reviewed in application but are easy to fix.  There is a significant  reduction in the amount of images that would need be checked as well as the total number misclassified is small. About 5%-13%.

With the addition of new images the accuracy of the model will increase as shown with the simple addition of the augmented files.  The data set is still small comparatively and more data will help create a more accurate model.

Some directions to explore in order to increase the accuracy and reliability of the model.

* Obtain more data to add to the model.  
* Create bottle neck features from a mid output layer.
* Create bottle neck features from a different per-trained model.

There is a strong case that the accuracy of the model was good in reference to ascertaining the class of interest.  Some misclassifications will be acceptable, however the application of classifying class 2 accurately will have a large impact.  
