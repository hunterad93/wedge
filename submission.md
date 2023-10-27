
# Applied Data Analytics

## Wedge Project

I am including a notebook called wedge_assessment_queries.ipynb, I made this after seeing the assessment queries but before seeing the submission.md.  Its a nice quick way to run the assessment queries and compare.

### Task 1

<!--  List of file or files here  --> 

`task1.ipynb`: 
1. Handles nulls (or null placeholders) and normalizes csv format, handling extra quotes and ; delimiters.
2. Ads standard headers if needed.
3. Changes datatypes to those in original dataset.
4. Loads all csvs into GBQ data set.

<!--  Repeat for each file  --> 


### Task 2


`task2.ipynb`: 
1. Queries a list of all owners.
2. Downloads all records for a sample of those owners, 450 owners yielded a ~230mb file.

<!--  Repeat for each file  --> 
	

### Task 3

`task3.ipynb`: 
1. Runs three queries to create the tables described.
2. Uses sql lite to transform these into a sql db.

<!--  Repeat for each file  --> 


## Query Comparison Results

Fill in the following table with the results from the 
queries contained in `gbq_assessment_query.sql`. You only
need to fill in relative difference on the rows where it applies. 
When calculating relative difference, use the formula 
` (your_results - john_results)/john_results)`. 



|  Query  |  Your Results  |  John's Results | Difference | Rel. Diff | 
|---|---|---|---|---|
| Total Rows  | 85760124  | 85760139  | 15  |  1.749064e-07 |
| January 2012 Rows  | 1070907  | 1070907  |  0 |  0 |
| October 2012 Rows  | 1042287  | 1042287  |  0 |  0 |
| Month with Fewest  |  Feb | Feb  | Yes  | NA  |
| Num Rows in Month with Fewest  | 6556769  | 6556770  |  1 | 1.525141e-07  |
| Month with Most  | may  |  may | Yes  | NA  |
| Num Rows in Month with Most  | 7578371  | 7578372  | 1  | 1.319545e-07  |
| Null_TS  | 7123776  |  7123792 |  16 |  0.000002 |
| Null_DT  | 0  |  0 |  0 |  0 |
| Null_Local  | 234839  |  234843 |  4 | 0.000017  |
| Null_CN  | 0  |  0 |  0 |  0 |
| Num 5 on High Volume Cards  | 14987.0  |  14987.0 | Yes  | NA  |
|  Num Rows for Number 5 | 460625 | 460630  | 5  | 1.085470e-05  |
| Num Rows for 18736  |  12153 | 12153  | 0 |  0 |
| Product with Most Rows  | banana organic  | banana organic  | Yes  | NA  |
| Num Rows for that Product  | 908637  | 908639  | 2  | 0.000002  |
| Product with Fourth-Most Rows  | avocado hass organic | avocado hass organic  | Yes/No  | NA  |
| Num Rows for that Product  | 456771  | 456771  | 0  | 0  |
| Num Single Record Products  |  2741 | 2769 | 28  | 0.010112  |
| Year with Highest Portion of Owner Rows  |  2017 | 2017  | Yes  | NA |
| Fraction of Rows from Owners in that Year  |  0.7513 | 0.7513  | 0  |  0 |
| Year with Lowest Portion of Owner Rows  |  2010 |  2010 | Yes  | NA |
| Fraction of Rows from Owners in that Year  | 0.7422  | 0.7422  | 0  | 0  |

## Reflections

I'm really curious why my data wasn't at 100% the same as original data. I ended up getting really close on my first try, then made a change which took a very long time to get working that seemed to get me 0.00000001% closer and decided that continuing to work on it was a little crazy.

I really enjoyed this project I worked on it every chance I got until it was done, data engineering is awesome. The hardest parts were issues with different things trying to infer intended datatype, especially inferring int from x.0 numbers. For some reason it took me a while to find a solution that properly handled nan while also creating floats not ints, partly because i wasn't understanding this was where the problem was.

Also a weird thing happened where even though I was trying to replace tables when uploading, it seemed to try to use the schema of the old table, which compounded the issue of floats vs ints. I think there was a point where I found then gave up on the right solution because GBQ was using the old table's schemas which was throwing the error. Eventually when I realized this and deleted the whole dataset before each retry, it became alot easier.

ChatGPT led me on some wild goose chases but I'm sure it would have taken me 5-10x longer without it. It basically did tasks 2 and 3 with minimal guidance, for task 1 I had to really understand everything and break it down to get it working.