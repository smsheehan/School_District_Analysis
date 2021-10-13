# School_District_Analysis

## Overview of the school district analysis: 
The purpose of this exercise is to address a need to remove from analysis the 9th grade testing data from one of the fifteen schools in the district.  With the 9th grade data removed, we were asked to re-analyze the school district data and help the school board see if the new analysis changes the interpretation from our previous analysis where all grades were included.  From a skills development standpoint, the purpose of this exercise was to introduce the concept of replacing values in a data frame with "NaN" which stands for "Not a Number".  This also required us to dive specifically into the school in question and learn how to use .loc to find and replace values.  Lastly, comparing the new output with the previous output helps us to see the impact of removing a subset of data.

The first critical aspect of the code was to use the loc method to select all of the 9th grade reading scores at Thomas High School (THS) and replace the values with "NaN".  I used conditionals to first select 9th grade and then to select Thomas High School.  After the conditionals, I put the name of the column I wished to replace and set it to NaN using "np.nan".  I did this for reading score and for math score as shown in the code below:

![image](https://user-images.githubusercontent.com/90977689/137179114-e379dd71-a730-42a7-8735-90517c0c586a.png)

A quick check of the data frame tail provided the verification that this code worked as intended:
![image](https://user-images.githubusercontent.com/90977689/137179330-76534009-3c87-4357-bc98-df5f47440669.png)

Since removing the THS 9th grade students changes the total number of students in the analysis, I wrote code to do the quick math to calculate the new total.  This was just counting the number of students in 9th grade at THS and subtracting it from the total number of students count to get the new count:

![image](https://user-images.githubusercontent.com/90977689/137179948-6c778a8f-475b-4925-941f-e7b2cf647fee.png)

This new count was used to recalculate the passing math percentage and the passing reading percentage.  I simply took the passing math count and passing reading count, divided them by the new total count and multiplied by 100:

![image](https://user-images.githubusercontent.com/90977689/137180226-d92f8f8c-12d2-4072-adcc-99e63eb7106a.png)

After using a similar approach to calculating the overall passing percentage with the new total student count and building a "district_summary_df" dataframe, I received the following output:

![image](https://user-images.githubusercontent.com/90977689/137180596-7733f8e3-8a55-4eea-8dfd-ba0045796711.png)

Creating the new school summary required some specific code for handling Thomas High School.  First I needed to calculate the number of 10-12th graders through simple subtraction of the 9th grade count from the total THS student count:

![image](https://user-images.githubusercontent.com/90977689/137181167-0bb7e53e-ffc2-4d56-a64e-6a39f8ebd678.png)

Then I used some conditionals to get the students passing math, the students passing reading, and the students passing math and reading:

![image](https://user-images.githubusercontent.com/90977689/137181374-d254f102-ecc1-48de-b641-7dd6a87cd2bb.png)

This was then followed by straightforward calculations to determine passing percentages:

![image](https://user-images.githubusercontent.com/90977689/137181700-73728219-9c60-49a0-8c88-b28a76426fef.png)





## Results: 
Using bulleted lists and images of DataFrames as support, address the following questions.

-How is the district summary affected?

-How is the school summary affected?

-How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

-How does replacing the ninth-grade scores affect the following:

   **Math and reading scores by grade
  
   **Scores by school spending
  
   **Scores by school size
  
   **Scores by school type

## Summary: 
Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs
