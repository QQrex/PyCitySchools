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

With the new student count, we can now calculate the new passing math, reading and overall scores.

![passingMR](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/pass%20math%2C%20reading%20over%20avg.PNG)
Cell 1, line 3 - Counting all student IDs with math scores greater than or equal to 70.

Cell 1, line 5 - Counting all student IDs with reading scores greater than or equal to 70.

Cell 1, line 11 - Calculating passing math %.

Cells 1, line 12 - Calculating passing reading %.

Cell 2, line 2,3 - Counting all students IDs with math and reading scores greater than or equal to 70.

Cell 2, line 7 -  Calculating passing both math and reading %.

With all the datapoints we need for our district DataFrame, all that is left is to construct the DataFrame.

![Dsum](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/district%20summary.PNG)

Similar to how we set up the district DataFrame, we are going to calculate the datapoints for the school data frame with the schools as indexes

![SchoolCode](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/school%20summary%20code.PNG)
>Line 2 - Set index by school name and find type of school.
>
>Line 5 - Count total students per school.
>
>Line 8 - Calculate total budget per school.
>
>Line 10 - Calculate total spent per student at each school.
>
>Line 13, 14 - Calculate average math and reading score per school.
>
>Line 17, 18 - Create Dataframe of students that pass math or reading.
>
>Line 21, 22 - Count students that past math and reading per school.
>
>Line 25, 26 - Calculate % passing math and reading scores per school.
>
>Lin 29,30 - Creating Dataframe of student that past both math and reading.
>
>Line 33 - Counting students that past both math and reading per school.
>
>Line 36 - Caculate % passing both math and reading scores per school.

Next, we will assemble all the data into a DataFrame for each school, add some formating and check the results of the DataFrame.

![perschoolsum](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/per%20school%20summary%20df.PNG)

Upon inspection of the per school summary DataFrame, we notice the THS is not accurate because we only removed the math and reading scores for THS 9th graders. The total student count at THS still contains THS 9th graders. In order to complete our per school summary DataFrame, we ned to recount the THS students.

![THSnewCount](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/THS%20new%20student%20count.PNG)
>Line 3 - Count total total students at THS
>
>Line 7 to 9 - Count THS 9th graders
>
>Line 11 - Calculate new total student count at THS

Next we will need to find all THS 10th to 12th graders with passing math, reading and overall grades.

![THSdf](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/THS%20passing%20math%2C%20reading%20overall%20%25.PNG)
Cell 1 - Create DataFrame of THS 10th to 12th graders with passing math scores.

Cell 2- Creat DataFrame of THS 10th to 12th graders with passing reading scores.

Cell 3 - Create DataFrame of THS 10th to 12th graders that passing math and reading scores.

With the new student count of THS and THS students with passing grades, we can recaculate passing math, reading and overall % at THS.

![THS%](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/pass%20percent%2C%20math%2C%20read%2C%20both.PNG)
>Cell 1 - Count passing math scores at THS and caculate passing %.
>
>Cell 2 - Count passing reading scores at THS and caculate passing %.
>
>Cell 3 - Count passing overall scores at THS and caculate passing%.

With the correct data for THS we need to place the data in the per school summary DataFrame. We will accompish this by using the .loc method similar to how we replace the THS 9th grader math and reading scores

![replace](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/replace%20per_school%20percentages.PNG)
>Cell 1 - Replacing THS math % with .loc method by using 'THS' as index for row and '% passing math' as column
>Cell 2 - Replacing THS reading % with .loc method by using 'THS' as index for row and '% passing reading' as column
>Cell 3 - Replacing THS overall % with .loc method by using THS as index for row and '% passing overall' as column

Finally, we check our per school summary DataFrame.

![newschoolDF](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/check%20per%20school%20df%20after%20replace%20THS%20percent.PNG)

Now that our summary DataFrames looks clean, we can start compiling some metrics. We can sort our per school summary Dataframe by % overall passing to show the top 5 and bottom schools.

![highlow](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/high%20and%20low%20performers.PNG)
>Cell 1 - Sort per school summary Dataframe by '% over all passing' for top schools
>Cell 2 - Sort per school summary Dataframe by '% over all passing' for bottom schools

We can also create a DataFrame of average reading and math scores per school base on school grades. We first need to create a DataFrame for each grade level.
![gradeDFs](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/Dataframes%20for%20grade%20levels.PNG)

Next we find the average math and reading scores score for each grades level DataFrame. We can use groupby school to create a Series of averages scores per school.
![groupby](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/average%20group%20by%20grade.PNG)

After we find all the average scores per school, by grade level. We will need to put them into a DataFrame.
![AverageDF](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/create%20average%20data%20frame%2C%20format.PNG)
>Cell 1 and 2 - We concatenate our average grade Series and add the grade level column headers.
>
>Cell 3 - Format dataframe

Our final average DataFrame looks like:

![mathdf](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/math%20score%20avg%20df.PNG)
![readingdf](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/reading%20score%20avg%20df.PNG)

Our next metric would be to create spending summary DataFrame with categories based on spending per student and average scores/% passing for each category.

![spendingbins](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/scholl%20spending%20average%2C%20spending%20bins%2C%20group%20name.PNG)
>Cell 1 - Get description of per school capita series.
>Cell 2 - Create spending bins and names for spending bins.

Next, we will create a new column with our spending bins with pd.cut method.
![cutspendingbins](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/cut%20spending%20in%20per%20school%20summary%2C%20avg%20scores%2C%20passing.PNG)
>Cell 1 - With pd.cut, we are declaring a new column in per school summary DataFrame named "Spending Ranges (Per Student)" and fill the column with our per school capita series again. However, we are also placing the "Per Student Budget" into spending bins/group names.
>
>Cell 2 - Using groupby to group spending bins and find the average math, reading and overall scores.

Next we can create our DataFrame for spending summary and add some formating to the DataFrame.

![createspendindf](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/spending%20df%2C%20format.PNG)

Our final spending summary DataFrame:

![spendingDF](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/spending%20df%20check.PNG)

Next, we want to create a size summary DataFrame based on school size categories and average score/% passing for each category.

![sizeBCA](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/size%20bin%2C%20cut%2C%20avg.PNG)
>Cell 1 - Create size bin and group name
>
>Cell 2 - Similar to when we cut spending bins, we are declaring new column in school summary DataFrame name "School Size" and fill column with total student count placed in bins.
>
>Cell 3 - Using groupby to group size bin the average math, reading and overall scores.

With our data group in size bins we can create our DataFrame.

![createsize](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/size%20df%2C%20format.PNG)

Our final school size summary DataFrame:
![sizedf](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/size%20df%20check.PNG)

Our last metric DataFrame is to look at the scores by school type. Since our per school summary DataFrame already has a column of school type, we can just use .groupby to group the school types and find average and % passing scores. Then create a Dataframe with school type as Index.

![type](https://github.com/QQrex/School_District_Analysis/blob/main/Resources/type.PNG)

## Results

After performing our analysis after removing the scores for Thomas High School 9th graders we saw:

- District Summary - A decrease in % passing math by 0.1%, reading by 0.3% and overall by 0.1%
- School Summary - The only school affected in the school summary was THS which saw a <0.3% decrease in math, reading and overall passing %
- Top and Bottom Performing schools - We saw no change in the top and bottom school rankings
- Average math and reading scores per grade level - Saw no changes in scores, except for for NaN results for THS 9th graders
- School spending summary - No changes
- School size summary- No changes
- Type summary summary- No changes

## Summary

Upon reviewing the new metrics from our school district analysis, we saw no signifcant changes to the overall metrics after removing Thomas High School 9th graders. This is due to the fact that THS overall math and reading scores average and passing % did not change much after THS 9th grader's scores were removed.
