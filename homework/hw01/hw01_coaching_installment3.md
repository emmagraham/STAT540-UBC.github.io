Homework 1 Coaching
========================================================

### Installment 3

Recap of where we are:


* You have the Git and GitHub issues sorted out. 
* You've got an outline for the whole homework assignment in an R markdown document. 
* You've done intake, data cleaning, and some exploratory analysis. Your plots in questions 1 and 2 look good with nice labels, colour scheme, etc. 
* You have organized your plots in a way that are easy to compare and interpret. For example, it may be better to have the two histograms of Q2c on the same plot.

**Next task**: Differential expression analysis

Your model in this question should contain only *one* categorical
variable, i.e., `treatment`. Revisit lecture slides with an eye for models we posed for gene expression data with 1 categorical covariate. State the model in English and proper mathematical notation (note: the mathematical notation is not the same as the R-code). Given this formal statement of a model, what parameters would have to be zero for there for be NO differential expression between the two treatments?

Translate your model from English / math notation to an R code. Fit the model to each probe's data, presumably using `limma`. Depending on which design matix you use, you may need to fit a contrast matrix as well. Follow all steps within the `limma` framework.

Use `topTable()` to access probesets with evidence for differential expression. Read the documentation of this function to take control of sorting, thresholding, p-value adjustment, etc. Although in this simple model, you may not find `coef` a relevant argument (why?), in general, you need to tell `topTable` which coefficient you want to test.

Revisit the multiple testing lecture to remind yourself what error rates are controlled by raw p-values vs Benjamini-Hochberg adjusted p-values ("q-values"), so you can properly interpret hit lists arising from thresholding on p-values. Is the list of top-50 probes the same as the list of probes with an estimated FDR below 0.05? What does thresholding mean? 

Revisit some of the underlying data for hits and non-hits, to check that all is well and get a visual understanding of what sort of differential expression you are finding. Throughout this question, remember we're looking only at the effect of `treatment` (on average over `time`). Thus, you can ignore `time` in your plots to illustrate the results of your discovery. 

Are you feeling uncomfortable already because `time` was omitted? You may want to add some additional plots showing now the effect of both `treatment` and `time` in the expression of your selected probes. Depending on which probes you've chosen, the latter set of plots may not show anything new but they may help you to understand the effect of omitting `time` in the model.

**You are more than half way!!!**
