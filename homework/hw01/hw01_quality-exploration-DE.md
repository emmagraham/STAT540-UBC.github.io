Homework 01
======================================================================

In this assignment you will be analyzing a publicly-available gene expression study of normal human bronchial epithelial (NHBE) cells, run on the Affymetrix GeneChip Human Genome U133 Plus 2.0 Array.

You can read about the study at (http://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE10718)

The motivation is to study how the exposure to cigarette smoke (CS) affects the transcriptome in these NHBE cells. To investigate this goal, the NHBE cells are treated with CS for a duration of 15 mins, and the transcriptome levels are measured subsequently at 1,2,4 and 24 hours post-CS-exposure via high-density oligonucleotide microarrays. This study can contribute to the identification of biomarkers that characterize the genomic effects pertaining to tobacco exposure. From such temporal sequential study, a better understanding of the role that tobacco exposure plays in the etiology or progression of lung cancer can be developed. 

The transcriptome data and the meta-data for the design details can be downloaded here : [data](https://github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/homework/hw01/hw1Data/data.txt.gz?raw=true), [meta-data](https://raw.githubusercontent.com/STAT540-UBC/STAT540-UBC.github.io/master/homework/hw01/hw1Data/design.txt). The data has been preprocessed and it is on a log2 scale. One sample with NA values on all probes is removed from both the data and the meta-data, so overall it’s a little different than the processed data provided via GEO. Our focus here is on quality control, exploration, and differential expression analysis. 

## Evaluation

The assignment has a total of 25 points and represents 25% of your overall course mark. Overall presentation and mechanics is worth 5 points, with full points awarded if it's exceptional. Other 15 points are spread among the specific questions, as detailed below. We will try to give partial credit when/if we can figure out what you're trying to do. The remaining 5 points are for the evaluation of your peer review. We will post guidelines on peer review shortly.

Each student must submit their own work: no group efforts. It's fine to talk to fellow students and have discussion on the Discussion repository. If someone is really helpful, give them some credit. You have definitely crossed the line if there's any copying and pasting of code or wording. 

## Late policy

*Due date*: March 2nd, 2015 at 9:30am

Late submission will cost 2 points per day or fraction thereof
for five days, after which zero marks will be awarded.

If you expect that you will be late on a deadline (in this course, and
in life), contact us before missing the deadline, and submit whatever
partial work you have. Letting a deadline fly past with no
communication is neither conscientious nor polite.

## How to submit the work

See the [homework submission instructions](http://htmlpreview.github.io/?https://raw.github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/assignments.html). 

## Clarification notes

* Note that `agent` and `treatment` refer to the same thing: in the raw data from GEO, the corresponding column in the design file is called "agent", but we converted it to "treatment" in the preprocessed data. 

* In all questions, we are using “probe” and “gene” interchangeably. 

* In questions Q4 and Q5, `time` is considered a quantitative variable.


## Your mission

### Q0 **(0 pts)** Intake

Load the data from [this link](https://github.com/STAT540-UBC/STAT540-UBC.github.io/tree/master/homework/hw01/hw1Data). Smell test it. Fiddle with factor levels and do any other light cleaning you deem necessary. You can set `include = FALSE` for some/all of this code, but DO IT.


### Q1 **(1 points)** What are the basic characteristics of the data and meta-data? 

#### Q1a: How many probes? How many samples (`Bioassay`)?

#### Q1b: What is the breakdown of samples (`Bioassay`) for `agent`, `time`?

For starters, cross-tabulate `agent` and `time`. How do you feel about the experimental design? Hint: `table()` and `addmargins()` will help.

#### Q1c: Create a quantitative (numeric) variable that represents the `time` at which cells were measured. 

Note that the current variable `time` in this dataset is a factor (`time` column of `design.txt`). Create a new variable which is a numeric version of `time`. It should represent a numeric count of hours. You will need this new quantitative variable later in the analysis. Hint: for how to change time to quantitative covariate, refer to lecture 09.


#### Q1d: Create a plot showing the gene expression data for one probe and the averages for all possible combinations of `agent` and `time`.

Use position, panels or facets, and color to convey the `agent`, `time` of the samples. Report the average expression of the selected probe for all possible combinations of `agent` and `time`. Treat `time` like a factor in this question.


### Q2 **(2 points)** Assessing data quality

#### Q2a: Examine the sample-to-sample correlations in a heatmap.

Create the following sample-sample correlation matrices. First, order the samples by `time`; within each time group, sort on the other factor, i.e., `agent` (treatment). Next, order the samples by `agent`; and within each agent group, sort by `time`.  

Interpret your results. What does the sample correlation matrix tell us about the overall impact of time and agent?

#### Q2b: Assess the presence of outlier samples.

First, comment on the potential presence of outliers (if any) based on the sample correlation matrices created in Q2a.

Second, try to go beyond merely “eyeballing”, and make a quantitative statement about presence of an outlier: e.g., quantify for each sample, whether it “sticks out” compared to the other samples.  

Third, if any sample does “stick out” from the previous step, examine it in the context of its experimental group (e.g., given a sample that is least similar to all other samples: does it correlate with samples treated with same agent better than other samples treated with a different agent?)

#### Q2c: Assess the distribution of expression values, separated by agent.

The sample-sample correlation matrix does not capture differences between pairs of samples that are caused by systematic up- or down-regulation of all/most genes.  Can you explain why?

To determine if there is a “shift” in the distribution of expression levels, plot a histogram of expression values for each treatment condition (two histograms should be plotted).  Comment on the two histograms (e.g., similarity in range, mean, and median).

### Q3 **(4 points)** Assess differential expression with respect to `treatment`.

#### Q3a: Fit a linear model, modeling expression level of each probe using `treatment` as a single covariate.

Write out in English and as an equation the model you are using to assess differential expression. In the context of that model, what statistical test are you performing?

#### Q3b: Count your hits, and explore them.

How many hits (probes) are associated with `treatment` at unadjusted p-value 1e-3? How may are associated with `treatment` at FDR 0.05?

Took the top 50 probes as your “hits” and create a heatmap of their expression levels. Sort the hits by p-values and the samples by `treatment`.

What is the (estimated) false discovery rate of this "hits" list? How many of these hits do we expect to be false discoveries?

#### Q3c: Plot the expression levels for a few top (interesting) probes, and a few non-associated (boring) probes. 

Make a scatter plot, plotting the expression levels for each sample on the y-axis and `treatment` indicator on the x-axis.  Display the mean of each group on the same plot.

### Q4 **(4 points)** Assess differential expression with respect to `time`.

**Note**: from now on, `time` is treated as a quantitative covariate (unit: hours). Hint: for how to change it to quantitative (continuous) covariate, refer to lecture 09.

#### Q4a: Fit a linear model, assessing the effect of time on gene expression

Hint: your model should have a single covariate, modeling the effect of time only

How many hits are associated with `time` at unadjusted p-value 1e-3? At FDR 0.05?

#### Q4b: Plot expression levels of a few top probes and a few boring ones:

Make a scatter plot, plotting the expression levels for each sample on the y-axis and `time` on the x-axis. Since you are fitting `time` as a quantitative variable, add the fitted regression line on the same plot. 

Hint: `limma` estimated the slope of this line. This plot should look different from plots in Q1, why?


### Q5 **(4 points)** Perform differential expression analysis using a full model with both `treatment` and `time` as covariates.

**Note**: as in previous question, treat `time` as a quantitative variable.

#### Q5a: Quantify the number of hits for `treatment`.

For how many probes is `treatment` a significant factor at the unadjusted p-value 1e-3, and at FDR 0.05 level?

Is this number different from what you reported in Q3b? Why? Quantify the proportion of overlapping probes among your hits, when using the unadjusted p-value threshold of 1e-3.

Plot the distributions of all the p-values for `treatment` when using both models, i.e., one from the model in Q3 and one from the full model in this question. Compare and comment on the similarity/differences in the shape of the distributions.

#### Q5b: Test the null hypothesis that there is no significant interaction between `time` and `treatment`. 

Explain in English what you are modeling with this interaction term (what does it  represent?). 

For how many probes is the interaction effect significant at the unadjusted p-value 1e-3, and at FDR 0.05 level?

#### Q5c: Plot a few probes where the interaction does and does not matter 

Plot the expression levels for each sample on the y-axis and `time` on the x-axis. Color the points based on `treatment` group. As in Q4b, include the fitted regression lines in your plots.

#### Bonus question: consider the limitations of the model you used in Q5, can you think of an assumption underlying the model that is not consistent with the specification of this data?





