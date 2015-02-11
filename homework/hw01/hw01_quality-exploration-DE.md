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

*Due date*: February 28th, 2015.

Late submission will cost 2 points per day or fraction thereof
for five days, after which zero marks will be awarded.

If you expect that you will be late on a deadline (in this course, and
in life), contact us before missing the deadline, and submit whatever
partial work you have. Letting a deadline fly past with no
communication is neither conscientious nor polite.

## How to submit the work

See the [homework submission instructions](http://htmlpreview.github.io/?https://raw.github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/assignments.html). 


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



