# Kickstarting with Excel

## Overview of Project
This workbook contains data from various kickstart campaigns such as its name, amount of money for its goal and total money pledged for
the kickstarter, the data it launched and ended, country of origin, type of kickstarter, and if it succeeded, failed, or was canceled.  

### Purpose
To look at USA kickstarter data and break it up into different sections to determine the appropriate amount of pledge and and goal funds
needed in order to have a successful kickstarting campaign.

## Analysis and Challenges
The analysis involved spreading the data into several different tabs so that I could break down which subcategories of kickstarters were
more likely to receive its goal amount of money. The main challenge was condensing the data into different tables that would be legible
and easy to understand for the client so that she could take this into her next meeting for her proposal.

### Analysis of Outcomes Based on Launch Date
To analyze the data, I took the raw data from the Kickstart sheet and converted the Unix Timestamps to readable dates using the code
=(((J2/60)/60)/24)+DATE(1970,1,1). Then to extract the year from this new result, I used the code 
=IF(CELL("format",A1)="D1",TEXT(A1,"dd/mm/yyyy"),A1), which is used from mrexcel.com courtesy of Sunny Kow.
Link: https://www.mrexcel.com/board/threads/no-matter-what-i-do-excel-formula-returns-a-date-as-1905.1037386/
Then, I used this data to create a pivot table. Using the table, I created a line graph by placing the years and parent 
category kickstarters as filters, outcomes for the columns, the launch date months as the row, and the outcomes as values.
I filtered the kickstarters for only theater projects and used all years for the analysis, but broke up the years in rows
by month.
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/46951897/123502341-4e37cd00-d611-11eb-939d-e903f4bf8bcb.png)

### Analysis of Outcomes Based on Goals
For this challenge, I had to create my column headers and rows by which these headers would be analyzed.
The headers began with the Goal where 12 rows were created that incrementally increased by 5000. This was to track the goals of 
kickstarters within intervals of 5000 dollars unless it is less than 1000 dollars or exceeds 50000 dollars. Next, it was a matter of 
creating headers that looked at the total number of successful, failed, canceled, and total kickstarters within the intervals.
The final headers look at the percentage that fell under these different headers.
To fill in the number of successful goals that were under 1000 dollars, I used the code =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D, "<1000", Kickstarter!$Q:$Q, "=plays").
I used similar codes for the rest of the the rows, but these other codes were within a range,
for example, between 1000 and 4900 dollars had the code =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D, ">=1000", Kickstarter!$D:$D, "<=4999", Kickstarter!$Q:$Q, "=plays").
Lastly, if the amount exceeds 50000 dollars, the code is =COUNTIFS(Kickstarter!$F:$F,"=successful",Kickstarter!$D:$D, ">=50000", Kickstarter!$Q:$Q, "=plays").
Similar codes were used for the failed and canceled columns with the first if being changed to reflect the condition.
The Total Project column merely sums the number of successful, failed, and canceled projects.
The percentage successful columns use the code =B2/E2, just the Number Successful divided by the Total Projects.
The rest used the same codes.
Finally, I used this data and created a line graph to examine the data over time.
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/46951897/123502348-57c13500-d611-11eb-93de-ae54f226b9e5.png)

### Challenges and Difficulties Encountered
The main challenge came in trying to find a way to convert Unix Times to a format that I could personally understand,
but thanks to a source, I was able to understand how to convert the times to where I could incorporate into a pivot table
and make it readable for any future clients that may want to use the source. The other challenge was ensuring that my
if statements would be properly conditioned and count the correct data.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
The analysis yielded that it is best to launch a kickstarter during the months of May and June since these have a success rate of
approximately 66%. 
-The worst times to launch a kickstarter are during the fall and winter months since the odds of failing are 
approximately 50%; essentially for every successful kickstarter during these months, there is also a failure.

- What can you conclude about the Outcomes based on Goals?
The conclusion of an analysis on outcomes based on goals yields that the most successful kickstarter goals are the ones that have a goal
of less than 5000 dollars as those kickstarters have an approximate 73%-75% chance of success. The chances of success decrease as the
goal exceeds this amount, except for having a goal between 35000-45000 dollars, as these have a 67% chance of succeeding, but this can
perhaps be attributed to lower sample sizes for these intervals. Regardless, it is best to aim for a modest goal of less than 5000 dollars.

- What are some limitations of this dataset?
The limitations include the small sample size for intervals that exceed 5000 dollars for their goals. The data also doesn't look at
how far goals got in reaching their targeted dollar amount, only if they succeeded or failed.

- What are some other possible tables and/or graphs that we could create?
Additional graphs that can be created are for those that failed, how far away were they from their goal. This is to say, for those
goals that exceeded 5000, how far away were they from attaining their goal. If it's not too far, then the case can be made that aiming high
for a goal that requires little money may still be a success in the long run for the kickstarter theater.
