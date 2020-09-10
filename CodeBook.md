# Data Introduction
- The project will use the floowing six data: `x_train.txt`, `x_test.txt`, `y_train.txt`, `y_test.txt`, `subject_train.txt` and `subject_test.txt`. Allof them can be found inside the downloaded dataset **UCI HAR Dataset**.
- The `features.txt` contains the correct variable name, which corresponds to each column of `x_train.txt` and `x_test.txt`.
- The `activity_labels.txt` contains the desciptive names for each label of the activity; which of them correspond to each number in the `y_train.txt` and `y_test.txt`.
- The `README.txt` is the overall description about the process that I used to do the experiment and got the results.

# Course Project Introduction
The script `run_analysis.R` performs data preparation and then followed the 5 steps required as described in the course project’s:


1. Merges the training and the test sets to create one data set.
  - `x_bind` is created merging x_train and x_test using rbind() function
  - `y_bind` is created merging y_train and y_test using rbind() function
  - `subject_bind` is created by merging subject_train and subject_test using rbind() function
  - `merged_data` is created by merging `subject_bind`, `y_bind` and `x_bind` using cbind() function


2. Extracts only the measurements on the mean and standard deviation for each measurement. 
  I createed `tidy_data` by subsetting merged_data, selecting only columns: subject, code and the measurements on the mean and standard deviation for each measurement.


3. Uses descriptive activity names to name the activities in the data set.
  In the `tidy_data` code column I replaced the numbers with the corresponding activity taken from the second column of the activities variable.


4. Appropriately labels the data set with descriptive variable names. 
  - `code` column in `tidy_data` was renamed `activities`
  - `Acc` in column’s name was replaced by `Accelerometer`
  - `Gyro` in column’s name was replaced by `Gyroscope`
  - `BodyBody` in column’s was name replaced by `Body`
  - `Mag` in column’s was name replaced by `Magnitude`
  - All lines starting with the character `t` in column’s name were replaced by `Time`
  - All lines starting with the character `f` in column’s name were replaced by `Fequency`
  - `tBody` in column’s name was replaced by `TimeBody`
  - `angle` in column’s name was replaced by `Angle`
  - `gravity` in column’s name was replaced by `Gravity`

5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.   
  `finalized_data` was created sumarizing `tidy_data` taking the means of each variable for each activity and each subject, after being groupped by subject and activity.
  Lastly `finalized_data` was exported into FinalizedData.txt.
