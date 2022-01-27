# PyCitySchools_Analysis
## Purpose

The school board has found evidence of academic dishonesty in reading and math grades for Thomas High School (THS) ninth graders. We are tasked to remove all THS ninth grader's grades and redo the school district metrics.

## Project Overview

1. Replace all THS ninth grader grades with NaN (blank values) in student data DataFrame.
2. Create a new district summary DataFrame.
3. Create a new school summary DataFrame.
4. Top and bottom 5 performing schools based on overall passing rate.
5. Average math and reading scores for each grade level from each school.
6. The score by school spending per student, by school size and school type.

## Analysis

Our first step would be import Pandas library, create path for files to load and clean the dataframes for prefixes/suffixes.

![DependsPathClean](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/Dependencies%2C%20path%2C%20cleaning%20prefixes%20and%20suffixes.PNG)
>Line 2 - Import Pandas library.
>
>Line 5 to 6 - Create path to files to load.
>
>Line 9 to 10 - Create Dataframes from csv files with Pandas.
>
>Line 14 - Creating list of prefixes and suffixes.
>
>Line 17 - Create for loop to loop through list of prefixes and suffixes.
>
>Line 18 - Looking at student_data_df column "student_name we are replacing all values from our prefixes and suffix list with blank.

Now we will remove all grade scores from THS ninth graders in our DataFrame. To accompish this we will will use np.nan.
![numpyNaN](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/import%20numpy%2C%20replace%20THS9%20with%20NaN.PNG)
>Cell 1 - Importing numpy
>
>Cell 2 - Using df.loc method, we are filtering our dataframe for "grade" column is equal to "9th" and "school_name" column for "Thomas High School" and setting all values in "reading_score" column equal to NaN.
>
>Cell 3 - Same as Cell 2 but replacing match scores instead of reading.
>
We will check our student_data_df to make sure we have replace all THS 9th grade scores with NaN.

![CheckNaN](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/Check%20NaN.PNG)

Next, we will merge our DataFrames together into one complete DataFrame and from there we will calculate total student count, total school count and total budget.

![MergeCounts](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/merge%20data%2C%20student%20count%20%2C%20school%20count%2C%20total%20budget.PNG)
>Cell 1 - Using pd.merge to merge or student and school DataFrame with common column "school_name"
>
>Cell 2, line 1 - Count all student IDs in school_data_complete DataFrame to find total student count.
>
>Cell 2, line 3 - Count all unique school values in school_data_complete DataFrame to find total school count.
>
>Cell 2, line 8 - Sum all school budgets in school_data DataFrame to find total budget.

After, we will need to find the average scores for both reading and math.

![Average](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/Average%20clean%20student%20data.PNG)
>Line 2 - Calculate average with .mean() in "reading_score" column.
>
>Line 3 - Calculate average with .mean() in "math_score" column.

Our next step will be to calculate the new student count without the THS 9th graders.

![newSC](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/new%20student%20count.PNG)
>Cell 1 - Counting student IDs by using .loc method to filter out '9th' in 'grade' column and 'Thomas High School' from school data complete DataFrame.
>
>Cell 2 - Subtracting total student count with student count of THS 9th to get new student count.

With the new student count, we can now calculate the new passing math and reading scores.

![passingMR]()
>Line 3 - Count all passing math scores in st
