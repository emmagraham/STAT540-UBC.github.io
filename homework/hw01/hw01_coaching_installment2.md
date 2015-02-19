Homework 1 Coaching
========================================================

### Installment 2

First, if you haven't done installment 1, it's not too late! Do a power evening, stay up late, whatever …. and catch up! 

#### Q1: basic characteristics of the data and meta-data

**Q1a**: how many probes? how many samples? should be easy. Use the `r exp(2)` style of inline R code to put this into your report, as opposed to hard-wiring it to actual numbers.

**Q1b**: tabulations. Do basic tabulations with table(). If you want to get fancier, add margins with addmargins(). Even nicer would be to make pretty HTML tables, using e.g. the xtable package. 

**Q1c**: you may want to give this variable a new name and add it to the existing dataframe.

**Q1d**: This is totally like stuff we've done in several seminars, so track down that code and modify it for here. To add the average expression of that probe for all possible combinations of `agent` and `time`, you can revisit seminars 3b, 3c, and 4b. Again, if you feel like getting fancy, report this in a nice looking HTML table. But that is optional and not worth burning tons of time on.

**Get Q1 done!!** Bask in the feeling of accomplishment!!

#### Q2: Assessing data quality

**Q2a**: Form the sample-to-sample correlation matrix. Think about the meaning of this matrix. What should be its dimensions? What data should be used to compute the sample-to-sample correlation? See lect04.

Depict it via a heat map. Just get something working first. Ugly colour scheme, awful sample labels, etc. Just have some success!

Figure out your strategy for sorting the samples and applying the desired sample order to your heat map. The order() function will be helpful.

Remake the heat map.

Read the documentation on whatever function/package you are using carefully. Run the examples. Take full advantage of the arguments and features.

Now is a good time to improve your colour scheme, to improve sample labels, to try to use colour in the margins to convey other info. Greyscale can be beautiful! In any case, avoid a scheme that goes from one extreme to another, like a rainbow. This is an occasion where you want a scheme that goes from one obvious colour to something that fades into the background, probably white.

You may realize you want to revisit your data cleaning and/or create a new variable to hold super-informative sample labels or grouping information.

**Q2b**: You can use your data aggregation techniques to compute interesting info about correlations and to compare samples.

**Q2c**: Data aggregation again!! get different summary statistics to describe the data!

**Get Q2 done!!** You are now ready to search for gold!!

