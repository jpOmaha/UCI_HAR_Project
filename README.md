UCI_HAR_Project
===============

Project for Coursera Getting and Cleaning Data

**README:   **** Human Activity Recognition Using Smartphones Dataset**

**Author:** _[Name withheld during grading process]                _ **Date** : June 16, 2014

**Data Source:**

Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz, _Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine_, International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain, Dec 2012

**Data Retrieval:**

[https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)

****

**Project Objective:**

Create an R script that transforms the retrieved data for subsequent analysis, in two steps:

_STEP 1_

1. Merge the "training" and the "test" datasets
2. For each "measurement", the mean and standard deviation values are recorded
3. Descriptive names are given to each of the "activities"
4. Descriptive variable names are provided
5. Descriptive labels are given to the dataset(s)

_STEP 2_

Create a "tidy dataset" with the "average" (only) of each activity and each "subject"

**Definition of Terms:**

_"training dataset"_ –70% of observations selected at random to build model(s)

           Subjects _(n1=21):_ # 1 3 5 6 7 8 11 14 15 16 17 19 21 22 23 25 26 27 28 29 30    

_"test dataset"_ –30% of observations withheld for subsequent model testing

           Subjects _(n2= 9): _# 2 4 9 10 12 13 18 20 24

_"subject" _– 30 volunteers, aged 19-48, each wearing a smartphone on their waist

_"activities"_ – Six physical activities are recorded:

1. WALKING

2. WALKING\_UPSTAIRS

3. WALKING\_DOWNSTAIRS

4. SITTING

5. STANDING

6. LAYING

_"measurements"_ – A 561-feature vector with time and frequency domain variables for each subject and each activity with respect to:

1. Triaxial acceleration from the accelerometer (total acceleration)
2. Estimated body acceleration.
3. Triaxial Angular velocity from the gyroscope. 

_"tidy dataset"_ – one that adheres to principles established in Hadley Wickham article,

"_Tidy Data_", retrieved from [http://vita.had.co.nz/papers/tidy-data.pdf](http://vita.had.co.nz/papers/tidy-data.pdf) on June 16, 2014

**run\_analysis.RData****     ---         ****How the Script Works**



My R working directory is /Users/jerry/Desktop/JHU DS Certif/UCI HAR Dataset; it contains all necessary files.


**STEPS**

1. To download the data, I changed https:// to http://
2. Read in 3 test files, 3 training files, a features file and an activity labels file
3. Used cbind and rbind to create a data table data, 10299 x 563
4. Used grep to reduce to data table with mean or stdmoments\_data, 10299 x 81
5. Removed the 13 columns with Freq mean\_std\_data, 10299 x 68
6. Reshape2 bombed; used reshape package to melt and casttidy\_averages, 180 x 68
7. Applied plyr package to revalue activity levels
8. Randomly sampled tidy\_averages to test all is well
9. Extended max.print to 999999 to assure output file would not be cut short
10. Used capture.output to print tidy\_averages as a file  UCI.HAR.JP.tidy.averages.txt
