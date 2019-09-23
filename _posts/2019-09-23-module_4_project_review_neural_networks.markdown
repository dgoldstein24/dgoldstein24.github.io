---
layout: post
title:      "Module 4 Project Review: Neural Networks"
date:       2019-09-23 18:46:18 +0000
permalink:  module_4_project_review_neural_networks
---


I found the necessary data by using the share as CSV feature on basketball-reference.com for seasons 2000-2019. I copy and posted the values into Excel, used the text to data function and uploaded the CSV to Jupyter Notebook. I also added a column for All-NBA honors: the baseline value was no selection and I looked up historic All-NBA selections and changed the default value for those players who received this honor. I turned the data into a DataFrame and filled null values with zeroes. I considered using median values, doing so did not end up making sense based on the stats being considered and my desire to standardize the values.

I then explored the collinearity amongst the features. My intuition that per 36 minutes statistics would be better to use than totals was confirmed when the multicollinearity heat map with totals was full of high values. After adjusting to per 36, I removed features with collinearity values of over .75. I then ran simple ML models, ML models with grid search tuning, and several variations of CNN models to find the best accuracy for a classifier of All-NBA selection based on current year statistics. Most of the models proved highly accurate, although the CNN models tended to do so by simply guessing that all players did not make All-NBA teams.

Because of these over-generalized results, I decided to give my data and research question a narrower focus: I would create a predictive model for All-NBA selection for the following year given current stats with players who had played over 3000 minutes. Doing so increased the proportion of selected players within the dataset and also removed variance in selection due to injuries as opposed to performance. In the end, a tuned Random Forest ML model yielded the best accuracy (about 80%) and identified a few breakout seasons before they happened. This result shows that further work on this model could lead to the development of a useful tool for future performance predictions, which would be useful to NBA GM’s.


