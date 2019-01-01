---
layout: post
title:      "Module 1 Final Project Blog - Scrubbing"
date:       2019-01-01 18:06:51 -0500
permalink:  module_1_final_project_blog_-_scrubbing
---




To my surprise, the most important aspect of this project, at least in my eyes, turned out to be scrubbing. This conclusion is not to say that the lessons leading up to the project failed to emphasize scrubbing; rather, this project served as an affirmation of all the preparation we have done so far. In particular, learning how to deal with non-numeric objects, null values, non-normalized numeric variables, un-binned categories, and multicollinearity issues made up the proved value and the largest portion of the work for this project.

Given the lessons we have learned in this program, it was pretty easy to make some initial column removals. The date of record submission for each entry does not affect pricing, so I could get rid of that column quickly. In addition, even before checking for collinearity, I made the observation that zip code, latitude, and longitude would overcompensate for the effect of geography on housing price. I figured that zipcode would account for both directions of navigation with just one column, so I kept this more efficient category to account for geography.

I then moved on to some more technical scrubbing. The first step was to identify which remaining columns had values that were not integers or floats. Sqft_basement had “?” values, so I replaced these values with the median for the variable. I chose to do so instead of deleting the column because the number of “?” values were relatively quite small as a percentage of all Sqft_basement values. In addition, I chose to use the median because I wanted to preserve the original median value as to not discount the other numeric values.

I then moved on to dealing with null values, which I found creating a DataFrame that returned True for null values and False for non-null values and then counting up the number of True values per variable. The three categories that had such values were waterfront, view, and yr_renovated. Yr_renovated had a huge proportion of null values, so I threw out that column. For waterfront, the non-null values were yes or no, so I figured that the null values could be their own bin for this categorical variable. For view, there were very few null values (63), so I changed them to the median.

It then came time to scrub the numerical variables and the categorical variables independently. I started with the numerical values that remained, which were bathrooms, bedrooms, floors, price, sqft_above, sqft_living, sqft_living 15, and grade. Before doing any transformations, I created a histogram for each of these variables to see if standardization was in fact necessary. Most, if not all, of the histograms had strong skews and high kurtosis, so I decided to proceed with the process to transform the numeric columns. I first performed both a log transformation and standardization, and then I generated another set of histograms for each variable. The second set of graphs showed that the transformation had successfully normalized the graphs for all but bedrooms and floors.

It was then time to deal with the categorical variables. The first step was to bin each of the categorical variables. To create the bins for yr_built and zipcode, I used .describe() to see the percentile values and split up the bins in 5 in the manner instructed in the lessons: 0-value above minimum, value above minimum – 25%, 25-50%, 50 - 75%, 75% -  100%. I chose this approach to binning for these categories because there were too many individual values for each value to be a bin. For the other categorical variables (view, grade, condition, and waterfront), each value was made into its own bin. For all sets of bins, I dropped the last one in order to account for singularity.

With each of the numeric and categorical variables transformed, it was time to figure out which variables sufficiently mattered to the model. In order to do so, I found the r-squared and p-values for each variable in respect to the target variable, price. I then eliminated every column with an r-squared value lower than .01 or p-value greater than .05. In this way, I knew that the remaining columns would serve to usefully explain the results of the final regression model.

The last step in scrubbing was to make sure that each variable’s explanation of the effect on pricing did not redundantly overlap with another category. In order to check for this issue, I conducted two steps of multicollinearity testing. First, I created a heat map to see if any issues stood out immediately just from a visual perspective. From this step, I was able to deduce that view_0 and waterfront_yes had a high degree of multicollinearity. Since I had other view variables for comparison, I decided to keep view_0 and drop waterfront_yes. The second step was to create a DataFrame that held a collinearity matrix and returned True wherever the collinearity was greater than .75. Sqft_living had True values conflicting with three other variables, so I took the simplest route to resolve the issue: I dropped sqft_living. After doing so, the multicollinearity issue had been resolved, and it was time to explore!

The rest of the project ended up being quite straight forward. This experience showed me that although scrubbing can be tedious, it is a crucial step in the data science process.

