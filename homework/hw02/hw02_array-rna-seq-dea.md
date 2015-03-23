Homework 02
======================================================================

In this assignment you will work with data originally published in "A comprehensive comparison of RNA-Seq-based transcriptome analysis from reads to differential gene expression and cross-comparison with microarrays: a case study in _Saccharomyces cerevisiae_." by Nookaew et al (Nucleic Acids Res. 2012 Nov 1;40(20):10084-97. PMID 22965124). The article is available here: [doi: 10.1093/nar/gks804](http://dx.doi.org/10.1093%2Fnar%2Fgks804).

The authors used two different platforms -- microarrays and RNA-Seq -- to obtain gene expression data for yeast grown in two conditions: batch medium and chemostat. They then compared the results of differential expression analysis (DEA) across platforms and under various combinations of aligners and methods for identifying differential expression. We will do the same. Some of the DEA methods covered in this class were included in their analysis, `edgeR` and `DESeq`, while others were not, such as `limma` and, in particular, the `voom` function.

We will work with their data obtained from the NCBI SRA and GEO repositories. Because of some differences in pre-processing your results will differ from theirs.

## Evaluation

The assignment has 25 points and represents 25% of your overall course grade. Overall presentation and mechanics is worth 5 points, with full points awarded if it's exceptional. Peer review is worth other 5 points. The remaining 15 points are spread among the specific questions, as detailed below. We will try to give partial credit when/if we can figure out what you're trying to do.

Same game as hw01. Each student must submit their own work: no group efforts. It's fine to talk to fellow students and have discussions. If someone is really helpful, give them some credit. You have definitely crossed the line if there's any copying and pasting of wording, interpretations and all the analysis.

## Late policy

**Due date**: March 30th, 11:59pm

**Soft deadline** for HW2: since this assignment came out later than planned, some students requested a potential extension of its deadline. Since you need time to work on your project, I will not change the actual deadline of HW2. However, the late-submission penalty will start running on April 4th at 12am. I strongly recommend you to finish by March 30th to have time to work on other tasks.

Late submission will cost 2 points per day or fraction thereof
for five days, after which zero marks will be awarded.

If you expect that you will be late on the deadline, contact us before missing it, and submit whatever partial work you have. 


## How to submit the work

See the [homework submission instructions](http://STAT540-UBC.github.io/assignments.html).

## Your mission

### Q1) Microarray Analysis

The six samples in this study, 3 replicates for each of the two conditions, were analysed on the Affymetrix Yeast Genome Array 2.0 platform. We have already downloaded the raw CEL files from GEO and normalised them. The normalized data is saved in the file [`GSE37599-data.tsv`](https://raw.githubusercontent.com/STAT540-UBC/STAT540-UBC.github.io/master/examples/yeastPlatforms/data/GSE37599-data.tsv)

#### Q1a) **(0 points)** Load Microarray Data

Load the normalized data.   
  
What are dimensions of the dataset? In addition to reporting number of rows and columns, make it clear what rows and columns represent and how you're interpreting column names.


#### Q1b) **(1 point)** Identify Sample Swap

The labels on two of the samples have been swapped, that is one of the batch samples has been labelled as chemostat and vice-versa. Produce the plots described below and explain how they allow you to identify the swapped samples.
  
i. (High volume) scatter plot matrix. 

ii. A heatmap of the first 100 genes (you can try more but it gets slow).

iii. Compute the Pearson correlation of the samples and plot the results using a heatmap.

iv. Scatterplot the six data samples with respect to the first two principal components and label the samples.


#### Q1c) **(2 points)** Microarray Differential Expression

Fix the label swap identified in question 1b. We want to swap b1 <--> c2. Revisit one or more elements of question 1b to sanity check before proceeding. 

Now use this data to do a differential expression analysis with `limma`.

Package these results in a data frame with six columns:

* probe.id - The array probe id.

* gene.id - The id of the gene which the probe overlaps (see below).

* p.value - The raw p-value for the probe.

* q.value - The BH corrected p-value, aka the q-value.

* log.fc - The log fold change which is the column called "logFC" in the limma results table.

* test.stat - The test statistics which for limma is the moderated t statistic. This is the column called "t" in the limma results table.

>  The gene id can be retrieved using the `yeast2.db` package from Bioconductor (i.e., you need to use `biocLite()` function to load it). In particular, the `yeast2ORF` object available after loading `yeast2.db` contains the mapping between probe IDs and yeast gene ids. Assuming you have a character vector of probes called `probe.ids`, the gene IDs can be retrieved using `gene.ids <- unlist(mget(probe.ids, yeast2ORF))`.

Remove any rows with probes which don't map to genes. You'll be able to find these because they will have `NA` as their gene id. Work with this data.frame to answer the questions below.

i. How many probes did we start with and how many remain after removing probes without gene ids?

ii. Illustrate the differential expression between the batch and the chemostat samples for the top hit (i.e., probe with the lowest p- or q-value).

iii. How many probes are identified as differentially expressed at a false discovery rate (FDR) of 1e-5 (note: this is a FDR cutoff used in the original paper)?

iv. Save your results for later with `write.table()`.

> When using write.table to save the data, you need to pass the arguments `row.names = TRUE, col.names = NA` to make sure the headers are written correctly.

### Q2) RNA-Seq Analysis

We have aligned the RNA-Seq library using the [Stampy](http://www.well.ox.ac.uk/project-stampy) aligner and generated count data. This particular RNA-Seq dataset was sequenced to quite a high depth. The data file is available as [stampy.deep.counts.tsv](https://raw.githubusercontent.com/STAT540-UBC/STAT540-UBC.github.io/master/examples/yeastPlatforms/data/stampy.deep.counts.tsv). In this question you will use this data to do a differential expression analysis using different packages from Bioconductor.

#### Q2a) **(1 point)** Load RNA Count Data and Sanity Check

Load the count data using `read.table`; you will need to pass the arguments `header=TRUE` and `row.names=1`. 

i) What are dimensions of the dataset? In addition to reporting number of rows and columns, make it clear what rows and columns represent. What is the difference between the rows of this dataset versus rows of the array data in question 1a?

ii) Do a sanity check to make sure there is no sample swap by plotting a heatmap of the sample correlations.


#### Q2b) (2 points) `voom` Differential Expression Analysis

Use `voom+limma` to identify differentially expressed genes between the batch medium vs. chemostat conditions.

i)  `voom` normalizes the counts before it converts counts to log2-cpm. Use `calcNormFactors` to normalize counts.


ii)  Use `voom` to convert count data into logged CPM data and then use `limma` to identify differentially expressed genes between conditions. 

Package these results in a data.frame called 'voom.limma.deep.results' with five columns:

* gene.id - The id of the gene which reads were aligned to.

* p.value - The raw p-value for the gene.

* q.value - The BH corrected p-value, aka the q-value.

* log.fc - The log fold change which is the column called "logFC" in the `edgeR` results table.

* test.stat - The test statistic, which is the column called "t".

iii) How many genes are differentially expressed between conditions at a false discovery rate (FDR) of 1e-5?

iv) Save your results for later with `write.table()` in file called `stampy.deep.limma.results.tsv`.

### Q3) Compare DEA results between RNA-Seq and array

In question 1, you performed a DEA of array data using `limma`. In question 2, you used `voom+limma` to perform DEA of RNA-Seq data. In this question, you will compare the results of RNA-Seq DEA with those of the array DEA. 

> Remember that you've packaged your results and saved them using `write.table()`. If the data.frames containing the results of these analyses are no longer in your workspace, load them using `read.table()`.

#### Q3a) **(1 point)** Comparing volumes of DE genes 
In this question, you will examine the difference between the q-values from both analyses (i.e., array and `voom+limma`) by overlaying density plots of the q-values from each analysis.

> Hint: to respond to this question, make two plots. One plot that includes the densities of q-values of the genes analyzed by both platforms (i.e., genes shared by both data frames), and another plot that includes the densities of q-values of ALL genes analyzed by at least one of the platforms.
  
Make some observations about the strengths of these two platforms.
  
#### Q3b) **(2 points)** Plots
Plot the gene expression (i.e., from array data) and the logged counts (i.e., from RNA-Seq data) of: two interesting genes identified as DE by both analyses; one DE gene identified as DE only in the array analysis; one DE gene only in the `voom+limma` analysis; one boring gene in both analyses (i.e., 5 genes total measured with 2 platforms)

### Q4: Deep vs low sequencing

Sequencing depth is a major factor in RNA-Seq analysis; as rule of thumb, the deeper you sequence the more power you have. To investigate this claim, we have created a low depth dataset by randomly selecting 1% of the reads and discarding the remaining 99%. This low depth count data was also aligned with Stampy.

In this question you will analyze deep and low depth count data with two different methods, `voom+limma` and `edgeR`. The goal is to examine the effect of sequencing depth in DEA and to see if these methods are equally robust to this effect.

#### Q4a) **(1 point)** `voom+limma` DEA of low sequencing data

In Q2b you analyzed deep count data using `voom+limma`. You will now repeat the analysis on the low sequencing data.

i) Load the low depth count data using `read.table`; you will need to pass the arguments `header=TRUE` and `row.names=1`. The data file is available as [stampy.low.counts.tsv](https://raw.githubusercontent.com/STAT540-UBC/STAT540-UBC.github.io/master/examples/yeastPlatforms/data/stampy.low.counts.tsv).

ii) Repeat Q2b-i and Q2b-ii for this new data.

Package these results in a data.frame called 'voom.limma.low.results' with five columns as you did in Q2b.

#### Q4b) **(2 points)** `edgeR` DEA of deep sequencing data

Now you will use `edgeR` to identify differentially expressed genes between the batch medium vs. chemostat conditions in the deep count datasets loaded in Q2a.

i)  Recall that `edgeR` needs to estimate the dispersion parameter in the negative binomial model using an empirical Bayes method. Estimate the dispersion parameters using `estimateGLMCommonDisp`, `estimateGLMTrendedDisp` and `estimateGLMTagwiseDisp`. 

ii)  Use the glm functionality of `edgeR`, i.e. use the `glmFit` function, to identify differentially expressed genes between conditions. 

iii) How many genes are differentially expressed between conditions at a false discovery rate (FDR) of 1e-5? Compare the results with those obtained in Q2b-iii.

Package these results in a data.frame called 'edger.deep.results' with five columns:

* gene.id - The id of the gene which reads were aligned to.

* p.value - The raw p-value for the gene.

* q.value - The BH corrected p-value, aka the q-value.

* log.fc - The log fold change which is the column called "logFC" in the `edgeR` results table.

* test.stat - The test statistic, which for `edgeR` is a likelihood ratio. This is the column called "LR" in the `edgeR` results table.


#### Q4c) **(1 point)** `edgeR` DEA of low sequencing data

Repeat Q4b-i and Q4b-ii for the low count data. Package these results in a data.frame called 'edger.low.results' with five columns as before.

#### Q4d) **(2 point)** Comparison of DEA
 
Now that we have the results of the differential expression analysis performed by `voom+limma` and `edgeR` methods on both low and deep count data, we are going to compare and illustrate the results.

Create a Venn diagram showing all genes identified as differentially expressed (at FDR of 1e-5) in the four previous RNA-Seq analyses. If the comparison of 4 sets gets very confusing, you can also create different pairs of Venn diagrams of interest.

i) How many genes were identified by `voom+limma` in both low and deep count data? 

ii) How many genes were identified by `edgeR` in both low and deep count data? 

iii) How many genes were identified in all the analyses?

iv) Comment on the effect of sequencing depth on the DEA results. Is one of the methods more robust to this effect than the other. Make any additional observations about your results that you find interesting. 

> The Venn diagram can be drawn using the `VennDiagram` package, the following code should get you started. Also be aware there is an argument called `force.unique`, which defaults to TRUE, that determines how elements that appear more than once in a set are handled when forming the Venn counts. You may also find the function `intersect` useful in your analysis. This function finds the elements common to two sets (vectors).

```r
library(VennDiagram)

# Fake some gene names for 4 different methods.  Note that in this example,
# I'm comparing 4 different sets so that you can see how to handle more
# complex cases.

method1.de.genes <- c("A", "B", "C")

method2.de.genes <- c("A", "B", "D", "E", "F")

method3.de.genes <- c("A", "B", "D", "E")

method4.de.genes <- c("A", "V", "E", "F")

# Put the things you want to plot in a list. The names in the list will be put on the plot.
de.genes <- list(Method1 = method1.de.genes, Method2 = method2.de.genes, Method3 = method3.de.genes,Method4 = method4.de.genes)

# Start a new plot
plot.new()

# Draw the Venn diagram. Note the argument `filename=NULL` tells it to
# create a plot object instead of outputting to file.
venn.plot <- venn.diagram(de.genes, filename = NULL, fill = c("red", "blue", "green", "yellow"))

# Draw the plot on the screen.
grid.draw(venn.plot)
```
