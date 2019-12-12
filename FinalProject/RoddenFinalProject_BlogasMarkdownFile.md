
# Diane Rodden
## BIOS 512
## Final Project
## "Patterns in Data Science Salaries by State"
### Project Description and Final Visualizations

Since I will eventually be graduating and looking for a job, I started to wonder about different career paths where I can apply my education. Data science is a rapidly growing field (https://datascience.berkeley.edu/about/what-is-data-science/), so I chose to explore data science salaries by US state to see which states are best for data science careers.

I started out by obtaining data on data science salaries by state from the career website ZipRecruiter. According their website, the data is from December 2019.  I did a copy and paste into a MS Excel file and saved in csv format.

But, that doesn't tell the whole picture, because a high salary in a high cost of living state might leave someone with little extra income. So, I decided to obtain a measure of cost of living that would allow me to adjust the salaries. I used the Regional Price Parities(RPP) 2017 dataset from the US Bureau of Economic Analysis.

I wanted to explore the hypothesis that that data science salaries have a coorelation with salaries of other jobs. I was running short on time, so I used a readily available dataset of Median Household Income as a proxy for average salary for other jobs. This dataset was obtained from 2017 American Community Survey Median Household Income (in 2017 Inflation-Adjusted Dollars) dataset from the U.S. Census Bureau. 

Next, I wanted to see if there were any states where data science is an especially good career, in comparison to other careers. For instance, if the average data science salary in three states (named A, B, C)  is \\$110,000  but the average salary for other jobs in those three states is \\$70,000 (state A), \\$160,000 (state B) and \\$110,000 (state C), then data science would be considered a good career field in state A, a bad career field in state B and an average or typical career field in state C. Again, I used the dataset of edian Household Income as a proxy for average salary for other jobs. This dataset was obtained from 2017 American Community Survey Median Household Income (in 2017 Inflation-Adjusted Dollars) dataset from the U.S. Census Bureau.

After looking at all of this salary information, it might be easy to get caught up in picking the state with the data science highest salary (raw, after adjustments for cost of living or in relation to other jobs), but one also has to consider data science job availability by state.  Due to time constraints, I had to use a dataset that is not a good of validity as I would have liked. It is from a Data Science Weekly article where the author tallied data science job postings by city and state from the first five pages of data science jobs listing from a job search site in 2014.  I had to copy and paste the data from the website into MS Excel and then save as csv. Since the author's data was by city and state, I collapsed into state manually. For instance, where the author had listed Redwood City, CA (qty. 1 job posting),  San Bruno, CA (qty. 1 job posting)  and San Diego, CA (qty. 1 posting),  I collapsed into CA (qty. 3 job postings).

By and large, the csv files were then ready to import in Jupyter Notebooks (running R). But, before importing, I had to remove footnotes, header notes and column headers from some of the files because they spanned multiple columns and/or rows. I didn't know how easily R would handle these non-standard csv components when reading in the files.

Once the csv files were read into R, I did extensive data wrangling, such as deleting columns, renaming columns and merging the four dataframes with joins. I added columns such as flags used to group data, ratio of data science salaries to median household income and data science salaries adjusted for cost of living(using the RPP dataset). Some of the files had rows for the overall US average or for Puerto Rico and/or for District of Columbia.  Since, not all of the files had observations for each of these geographical locations, I removed these rows using R to make a common set of states for analysis. 

My visualizations are below. Although not all of the datasets were of the best validity, if better datasets were located, I could use the same processes in R to easily update my visualizations.

<img src="https://github.com/GitHubUNCStudent/BIOS512-assignments/blob/master/FinalProject/Image_p_dssal.png">                                                                                                             

<img src="https://github.com/GitHubUNCStudent/BIOS512-assignments/blob/master/FinalProject/Image_p5.png">

<img src="https://github.com/GitHubUNCStudent/BIOS512-assignments/blob/master/FinalProject/Image_p10.png">                                                                                                              

<img src="https://github.com/GitHubUNCStudent/BIOS512-assignments/blob/master/FinalProject/Image_p20.png">                                                                                                          

<img src="https://github.com/GitHubUNCStudent/BIOS512-assignments/blob/master/FinalProject/Image_p30.png">                                                                                                             

<img src="https://github.com/GitHubUNCStudent/BIOS512-assignments/blob/master/FinalProject/Image_p50.png"> 

Interesting observations:

*  What is up with North Carolina? Why does ZipRecruiter show such a low salary for data science? 
<br><p>
*  North Carolina also has a low data science salary when adjusted for cost of living using the RPP.
<br><p>
*  Maryland, Hawaii, Connecticut and California are in the Top 15 states for raw data science salaries, but when the salaries are adjusted for cost of living, they fall to the bottom 10 states for data science salaries.
<br><p>
*  As the scatterplot illustrates, data science salaries have a fairly linear relationship with average salaries overall.
<br><p>
*  In New York, New Hampshire and Massachusetts, average jobs pay well and data science jobs pay better than the regression line would predict.
<br><p>
* After data science salaries are adjusted for cost of living by the RPP, West Virginia, Arkansas, Kentucky, Idaho, Montana and South Carolina are in the Top 10 states for high data science salaries. These states also show data science having a high salary compared to other jobs.
<br><p>
* West Virginia, North Dakota and Arkansas have high data science salaries after cost of living adjustment, but the jobs Data Science Weekly author didn't find any jobs in those states, although it is possible that the search results had some results for those states, but they were past the cutoff pages. 
<br><p>
* In states with data science job availability, the three highest data science salaries after cost of living adjustments are in Tennessee, Kansas and Massachusetts.



<b>Notes about my files</b>

My raw data files are on Github in the final project folder. They are named:

* headers ACS_17_1YR_R1901.US01PRF_with_ann.csv 	
* headers RPP download summary only.csv 	
* headers blog job counts.csv 	
* headers zip recruiter.csv 

I also posted two other files:
<br><p>
alldatajoined.csv      which is the dataframe after I finished joining all of the four raw files together

beforevisualize.csv   which is the dataframe after I finished all of the data wrangling and what is used to make the visualizations



<b>Sources for data sets</b>

Data Science Salaries:  https://www.ziprecruiter.com/Salaries/What-Is-the-Average-Data-Scientist-Salary-by-State



Regional Price Parities:
https://www.bea.gov/news/2019/real-personal-income-states-and-metropolitan-areas-2017



Median Household Income (2017 American Community Survey 1-Year Estimates):
https://factfinder.census.gov/faces/tableservices/jsf/pages/productview.xhtml?src=bkmk
 


Data Science Job Availability:
https://www.datascienceweekly.org/articles/where-are-data-science-jobs-located


```R

```
