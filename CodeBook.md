Variable descriptions and Data Transformations for the UCI HAR DATASET
=============

### Summary

The original dataset for this assignment along with experiment description is as provided on the course project page. Speicifc columns were extracted from the dataset, descriptive variable names assigned, descriptive labels assigned, the resulting data set was summarized and written to a text file 'tidydata.txt'.

### Variable Descriptions

"Subject" -  numbered 1:30, since this experimental data was collected from 30 subjects

"Activity" - can be one of the 6 activities  
 WALKING  
 WALKING_UPSTAIRS  
 WALKING_DOWNSTAIRS  
 SITTING  
 STANDING  
 LAYING  
 
The rest of the variables that follow are variables corresponding to measurements. Here is the fundamental signal description.

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

Variables estimated from these signals are the 'mean' and standard deviation of these measurements.

* <b>Naming conventions

prefix 't' - time domain
prefix 'f' - frequency domain

BodyAcc-X,Y,Z , GravityAcc-X,Y,Z - Body and Acceleration Signals

BodyAccJerk- X,Y,Z, BodyGyroJerk - X,Y,Z, - Jerk Signals

BodyAccMag, GravityAccMag, BodyAccJerkMag, BodyGyroMag, BodyGyroJerkMag - Magnitudes of the above listed signals by applying Euclidean norm

Variables containing 'mean' denote that the variable represents the mean measurement.
Variables containing 'std' denote that the variable represents the standard deviation on the measurement.

* <b>New Naming Convention</b>: The original naming convention was tBodyAcc-mean()-X. The only difference between the old and new variable names is that '()' has been removed. I have retained everything else from the old convention since it was very informative as such, and the '-' made the names more readable. () I thought was unnecessary, and so removed it but decided to retain the '-' to preserve the readability.


Variables in time domain:  
tBodyAcc-mean-X  
tBodyAcc-mean-Y  
tBodyAcc-mean-Z  
tBodyAcc-std-X  
tBodyAcc-std-Y  
tBodyAcc-std-Z  
tGravityAcc-mean-X  
tGravityAcc-mean-Y  
tGravityAcc-mean-Z  
tGravityAcc-std-X  
tGravityAcc-std-Y  
tGravityAcc-std-Z  
tBodyAccJerk-mean-X  
tBodyAccJerk-mean-Y  
tBodyAccJerk-mean-Z  
tBodyAccJerk-std-X  
tBodyAccJerk-std-Y  
tBodyAccJerk-std-Z  
tBodyGyro-mean-X  
tBodyGyro-mean-Y  
tBodyGyro-mean-Z  
tBodyGyro-std-X  
tBodyGyro-std-Y  
tBodyGyro-std-Z  
tBodyGyroJerk-mean-X  
tBodyGyroJerk-mean-Y  
tBodyGyroJerk-mean-Z  
tBodyGyroJerk-std-X  
tBodyGyroJerk-std-Y  
tBodyGyroJerk-std-Z  
tBodyAccMag-mean  
tBodyAccMag-std  
tGravityAccMag-mean  
tGravityAccMag-std  
tBodyAccJerkMag-mean  
tBodyAccJerkMag-std  
tBodyGyroMag-mean  
tBodyGyroMag-std  
tBodyGyroJerkMag-mean  
tBodyGyroJerkMag-std  

Variables in frequency domain  

fBodyAcc-mean-X  
fBodyAcc-mean-Y  
fBodyAcc-mean-Z  
fBodyAcc-std-X  
fBodyAcc-std-Y  
fBodyAcc-std-Z  
fBodyAccJerk-mean-X  
fBodyAccJerk-mean-Y  
fBodyAccJerk-mean-Z  
fBodyAccJerk-std-X  
fBodyAccJerk-std-Y  
fBodyAccJerk-std-Z  
fBodyGyro-mean-X  
fBodyGyro-mean-Y  
fBodyGyro-mean-Z  
fBodyGyro-std-X  
fBodyGyro-std-Y  
fBodyGyro-std-Z  
fBodyAccMag-mean  
fBodyAccMag-std  
fBodyBodyAccJerkMag-mean  
fBodyBodyAccJerkMag-std  
fBodyBodyGyroMag-mean  
fBodyBodyGyroMag-std  
fBodyBodyGyroJerkMag-mean  
fBodyBodyGyroJerkMag-std  

### Transformations on original dataset

1. The original measurement data was merged with 'subject' and 'activity' columns to form a complete data set.

2. 'Mean' and 'std' on each measurement needs to be extracted. There are different types of variable names that denote mean and std. For example - ones ending with    'mean()' (fBodyBodyGyroMag-mean()), ones that contain 'mean' but dont end with it (fBodyBodyGyroMag-meanFreq() or angle(tBodyGyroMean,gravityMean)). The first case    is clearly measurement of the mean, but the second case a bit ambiguous, so I decided to extract only the feature names ending with 'mean()' or 'std()'.

This was done by extracted the variables whose variable names ended with 'mean()' or 'std()' using grep.

3. Original activity labels were numerals from 1-6. These were replaced with descriptive names like 'walking', 'laying', 'walking_upstairs' etc.

4. The current extracted dataset has column names 'v1 v2...' which were replaced with feature names that were extracted in step 2. 'subject' and 'activity' columns were also assigned names accordingly.

5. Finally, all measurements were averaged across each subject and activity. For example, all measurements corresponding to subject 1 Activity 'Walking' were averaged. This resulted in a final tidy data set with 180 rows (6 Activities, 30 Subjects) and 68 columns (66 measurements, 1 each for subject and activity). This dataset has been written to 'tidydata.txt'.  
 

