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

I then had to individually insert the new percentages into the dataframe using loc.  It is super important to note that unlike the previous cases where I was using loc on columns, here I needed to use loc on the Index, which is a little different.  It actually turns out to be a little simpler.  I could use the format of selecting THS directly (rather than referencing both the dataframe and column), then indicating which column cell needed to be replaced and set it equal to the new values using the variable names created in the code discussed above).  

![image](https://user-images.githubusercontent.com/90977689/137182511-253ebf63-3760-42db-bbe5-f7cffd9c30fb.png)

This produced the following dataframe:

![image](https://user-images.githubusercontent.com/90977689/137182737-21c99b6e-a313-40dd-9a93-e6f75e7ba396.png)

The rest of the code for this challenge was straightforward adoption of code developed in the original module case study.



## Results: 
Using bulleted lists and images of DataFrames as support, address the following questions.

- How is the district summary affected?  The district summary is essentially the same between the two analyses.  The average math score has changed by 1 tenth of a percent while the average reading score is identical.  In the final formatted dataframes, the module formats the % passing columns with no decimal places, while in the challenge we formated with one decimal place.  If the challenge was formatted in the same manner as the original analysis, the values would be identical.  Going back in the module code prior to formatting we can see the % passing categories are different by about .1%, which for the purposes of our analysis is essentially the same.  It is important to note that both data frames show the original student count of 39,170 students.  In my opinion, we should have added an additional column for "number of students included in grading analysis".
    
    Original district summary:
    
![image](https://user-images.githubusercontent.com/90977689/137188082-1d93e29a-be51-4045-aa05-4e844ecfc48e.png)

    New district summary with THS 9th grade scores removed:
    
![image](https://user-images.githubusercontent.com/90977689/137188257-31847deb-c0a2-4dbb-869e-0a9067d74e5f.png)


    
- How is the school summary affected?  Original school summary sorted by percent overall passing:

    ![image](https://user-images.githubusercontent.com/90977689/137196711-d3f6cc08-8ce5-487c-be59-740e1b91ec80.png)
    
    Updated school summary with THS 9th grade scores removed, again sorted by percent overall passing:
    
    ![image](https://user-images.githubusercontent.com/90977689/137197000-884e4264-b929-4ae9-bc03-56f616f5e198.png)

    

- How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?  While the changes did not alter, THS's rank when based on percent overall passing, there are some changes in the ranking when sorting by other categories.  In rank by average math score, THS originally ranked #4 however with the new analysis THS falls to #6.  Another difference is that in the original analysis, THS's rank in percent passing reading was #1, however with the new analysis THS falls to #3

- How does replacing the ninth-grade scores affect the following:

   ** Math and reading scores by grade
  
   ** Scores by school spending
  
   ** Scores by school size
  
   ** Scores by school type

## Summary: 
Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs
