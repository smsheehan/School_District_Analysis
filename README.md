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
Key questions and answers:

- How is the district summary affected?  The district summary is essentially the same between the two analyses.  The average math score has changed by 1 tenth of a percent while the average reading score is identical.  In the final formatted dataframes, the module formats the % passing columns with no decimal places, while in the challenge we formated with one decimal place.  If the challenge was formatted in the same manner as the original analysis, the values would be identical.  Going back in the module code prior to formatting we can see the % passing categories are different by about .1%, which for the purposes of our district level analysis is essentially the same.  It is important to note that both data frames show the original student count of 39,170 students.  In my opinion, we should have added an additional column for "number of students included in grading analysis".
    
    Original district summary:
    
![image](https://user-images.githubusercontent.com/90977689/137188082-1d93e29a-be51-4045-aa05-4e844ecfc48e.png)

New district summary with THS 9th grade scores removed:
    
![image](https://user-images.githubusercontent.com/90977689/137188257-31847deb-c0a2-4dbb-869e-0a9067d74e5f.png)


    
- How is the school summary affected?  	Original school summary sorted by percent overall passing:

    ![image](https://user-images.githubusercontent.com/90977689/137196711-d3f6cc08-8ce5-487c-be59-740e1b91ec80.png)
    
    Updated school summary with THS 9th grade scores removed, again sorted by percent overall passing:
    
    ![image](https://user-images.githubusercontent.com/90977689/137197000-884e4264-b929-4ae9-bc03-56f616f5e198.png)

    

- How does replacing the ninth graders??? math and reading scores affect Thomas High School???s performance relative to the other schools?  While the changes did not alter, THS's rank when based on percent overall passing, there are some changes in the ranking when sorting by other categories.  In rank by average math score, THS originally ranked #4 however with the new analysis THS falls to #6.  Another difference is that in the original analysis, THS's rank in percent passing reading was #1, however with the new analysis THS falls to #3

- How does replacing the ninth-grade scores affect the following:

   ** Math and reading scores by grade:
   
   Removal of the ninth-grade scores for THS does not affect any of the other schools grades in any way.  It also does not affect the 10th, 11th, or 12th grade scores for THS.  However, removal of the THS 9th grade scores does affect the district 9th grade averages.  District 9th grade reading average goes from 82.51 to 82.43 and district 9th grade math average goes from 80.35 to 80.12.
  
   ** Scores by school spending:  Unaffected
   
original scores by school spending
   
   ![image](https://user-images.githubusercontent.com/90977689/137202317-22649a53-1c54-49b8-9ad4-4d9573090184.png)
   
updated scores by school spending: 

![image](https://user-images.githubusercontent.com/90977689/137202457-20410635-a2e0-4296-a2e8-fcf27fdcd47f.png)


  
   ** Scores by school size:  Unaffected
  
original scores by school size:
  
  ![image](https://user-images.githubusercontent.com/90977689/137201694-d64c7c3a-3a52-4b48-87f6-2379090e1493.png)

updated scores by school size:

![image](https://user-images.githubusercontent.com/90977689/137201785-b0ef534b-0d61-490f-9521-3f5ebc685c74.png)



   ** Scores by school type:  Unaffected
   
original scores by school type

![image](https://user-images.githubusercontent.com/90977689/137201946-936ea081-23b8-4813-af92-d41a6e4e0129.png)

updated scores by school type:

![image](https://user-images.githubusercontent.com/90977689/137202040-6d645e60-6d1f-49b5-8540-e3edf4a2c88a.png)


## Summary: 
Four changes are worthy of note in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.  The impact of these changes on your interpretation of the data depends on how important one thinks the differences in tenths and hundredths of a percent are.  A statistical analysis would need to be done in order to avoid over interpretation of this data.  Such an analysis was not performed for this exercise.  While the summarized data all rounds out to be about equivalent, it is in the granular rankings analysis where the effects of the change can be seen.  In several of the categories, the data between schools is quite close and for ranking purposes it is not unreasonable to look to decimal level information to provide the differentiation.
    1.)  For school rank by average math score, THS originally ranked #4 however with the new analysis THS falls to #6.  The rank for THS by average reading score did not change.
    2.)  For school rank by percent passing reading, THS was #1, however, with the new analysis THS falls to #3.  The rank for THS by percent passing math did not change.
    3.)  For school rank by grade, obviously THS is not able to be ranked due to not having a score.  This would place them at the bottom of the ranking.  Prior to this change, THS 9th grade math ranked # 3 and THS 9th grade reading ranked #7.
    4.)  The fourth change is the obvious effect on THS's average scores.  The average reading score was 83.848930 (83.85 when rounded to 2 decimal places) in the original analysis and when the 9th grade scores were dropped, the average reading score changed to 83.896082 (83.90 rounded).  The average math score was 83.418349 (83.42 rounded) in the original analysis and when the 9th grade scores were dropped the math score changed to 83.350937 (83.35 rounded).	
