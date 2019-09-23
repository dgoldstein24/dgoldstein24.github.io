---
layout: post
title:      "Capstone Project: Soccer Performance Analysis"
date:       2019-09-23 19:01:18 +0000
permalink:  capstone_project_soccer_performance_analysis
---


The content of your blog postMy task was to identify the best center-backs (CB) in Major League Soccer who would fit within a playing style that focused on possession-retention and tackle-assuredness rather than playmaking from this position. Because open-source MLS data, especially defensive statistics, is extremely hard to come by and the only source I could find did not have a download option, I had to utilize my web scraping skills to create a DataFrame from scratch. I ran a recurring loop to scroll through an interactive table of CB statistics, stored all of the data, and transformed the quantitative data to integers and floats from its original string format. Tuning the scraping loop took much trial and error with Selenium and Beautiful Soup, but, in the end, I created my own working Database!

I then used my expertise in soccer player analysis to select the features that related most directly to the problem of CB evaluation. In order to make the statistical information actionable and easily interpretable, my goal was to create a new metric for overall CB performance and then filter the highest rated players in this metric for the specific playing style discussed in the prompt. I took the relevant features and used a function to find the percentile ranking of each CB within each statistical category. My intuition here was to use percentiles rather than ranking or simple scaling because percentile ranking gives weight to both value and availability of a player trait within the marketplace: a soccer player is a good signing for a team if their skills are both impressive and rare given that there is a fixed allocation of resources.

I created an algorithm to take the percentile rankings of relevant features and output a CB performance score scaled from 0-100. I then found the top 5 CB’s who met minimum criteria for statistics that aligned with the desired playing style. I then created a bar graph to convey the practicality of the overall CB ranking I had developed. I also used code to make radar charts to visually demonstrate how the players selected by model fit with the desired playing style. The numerous honors and news attention given to the positive performance of the players my model selected supported the validity of my model, and I think it is a promising tool for evaluating a complex position in soccer. 

