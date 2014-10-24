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
3	tBodyAcc-mean-Z
4	tBodyAcc-std-X
5	tBodyAcc-std-Y
6	tBodyAcc-std-Z
7	tGravityAcc-mean-X
8	tGravityAcc-mean-Y
9	tGravityAcc-mean-Z
10	tGravityAcc-std-X
11	tGravityAcc-std-Y
12	tGravityAcc-std-Z
13	tBodyAccJerk-mean-X
14	tBodyAccJerk-mean-Y
15	tBodyAccJerk-mean-Z
16	tBodyAccJerk-std-X
17	tBodyAccJerk-std-Y
18	tBodyAccJerk-std-Z
19	tBodyGyro-mean-X
20	tBodyGyro-mean-Y
21	tBodyGyro-mean-Z
22	tBodyGyro-std-X
23	tBodyGyro-std-Y
24	tBodyGyro-std-Z
25	tBodyGyroJerk-mean-X
26	tBodyGyroJerk-mean-Y
27	tBodyGyroJerk-mean-Z
28	tBodyGyroJerk-std-X
29	tBodyGyroJerk-std-Y
30	tBodyGyroJerk-std-Z
31	tBodyAccMag-mean
32	tBodyAccMag-std
33	tGravityAccMag-mean
34	tGravityAccMag-std
35	tBodyAccJerkMag-mean
36	tBodyAccJerkMag-std
37	tBodyGyroMag-mean
38	tBodyGyroMag-std
39	tBodyGyroJerkMag-mean
40	tBodyGyroJerkMag-std

Variables in frequency domain

41	fBodyAcc-mean-X
42	fBodyAcc-mean-Y
43	fBodyAcc-mean-Z
44	fBodyAcc-std-X
45	fBodyAcc-std-Y
46	fBodyAcc-std-Z
47	fBodyAccJerk-mean-X
48	fBodyAccJerk-mean-Y
49	fBodyAccJerk-mean-Z
50	fBodyAccJerk-std-X
51	fBodyAccJerk-std-Y
52	fBodyAccJerk-std-Z
53	fBodyGyro-mean-X
54	fBodyGyro-mean-Y
55	fBodyGyro-mean-Z
56	fBodyGyro-std-X
57	fBodyGyro-std-Y
58	fBodyGyro-std-Z
59	fBodyAccMag-mean
60	fBodyAccMag-std
61	fBodyBodyAccJerkMag-mean
62	fBodyBodyAccJerkMag-std
63	fBodyBodyGyroMag-mean
64	fBodyBodyGyroMag-std
65	fBodyBodyGyroJerkMag-mean
66	fBodyBodyGyroJerkMag-std

### Transformations on original dataset

1. The original measurement data was merged with 'subject' and 'activity' columns to form a complete data set.

2. 'Mean' and 'std' on each measurement needs to be extracted. There are different types of variable names that denote mean and std. For example - ones ending with    'mean()' (fBodyBodyGyroMag-mean()), ones that contain 'mean' but dont end with it (fBodyBodyGyroMag-meanFreq() or angle(tBodyGyroMean,gravityMean)). The first case    is clearly measurement of the mean, but the second case a bit ambiguous, so I decided to extract only the feature names ending with 'mean()' or 'std()'.

This was done by extracted the variables whose variable names ended with 'mean()' or 'std()' using grep.

3. Original activity labels were numerals from 1-6. These were replaced with descriptive names like 'walking', 'laying', 'walking_upstairs' etc.

4. The current extracted dataset has column names 'v1 v2...' which were replaced with feature names that were extracted in step 2. 'subject' and 'activity' columns were also assigned names accordingly.

5. Finally, all measurements were averaged across each subject and activity. For example, all measurements corresponding to subject 1 Activity 'Walking' were averaged. This resulted in a final tidy data set with 180 rows (6 Activities, 30 Subjects) and 68 columns (66 measurements, 1 each for subject and activity). This dataset has been written to 'tidydata.txt'.  
 

