---
layout: post
title:      "Module 2 Final Project Review: Using SQL"
date:       2019-06-07 13:44:48 +0000
permalink:  module_2_final_project_review_using_sql
---


I identified the tables I needed by finding which tables shared keys in order to jump from one table to another for information about quantity. I used sqlite3 for my SQL code, first establishing a connection to the Northwind database, then initializing a cursor, followed by looking up the names o fall the tables, and then using the database map provided to navigate between tables. Obtaining the SQL data and turning it into a DataFrame was fairly straightforward, although I did realize that  I had to create a decoy column for the DF and then delete it after in order to maintain the SQL data’s dimensions.

My methodology was to compare histograms of the samples in question side by side to determine if conditions were met for a student T-test. If conditions were not met, the decision was made to use Welch’s T-Test. I then conducted the appropriate t-test to determine whether there was a significant different in means between the two samples. I then use the Cohen D coefficient as a measure of effect size.

The results for the hypothesis tests were as follows. Discount had a significant, slightly positive effect on quantity. A 25% discount had a more significant and effective positive change on quantity than the other levels of discount. Free shipping resulted in a drastically significant, positive change in quantity purchased. Western Europe had a significant slightly positive effect on quantity. Owner purchases proved insignificant in its relationship to quantity as compared to other employee titles who completed orders.The content of your blog post goes here.
