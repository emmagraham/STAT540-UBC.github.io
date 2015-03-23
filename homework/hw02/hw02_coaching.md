Homework 2 coaching
======================================================================

Contributor: Gabriela Cohen Freue

## Question 1: Microarray Analysis

Nothing new here, just a simple limma analysis of microarray data! This is very similar to what you have done in HW1.

### Q1a) Load the data
Throughout the homework, you will need to load and use different data sets and data frames with results. 
- Choose good names for your objects. For example, I call these data `array.dat`.
- Pass the arguments `header=TRUE` and `row.names=1` to `read.table`.

### Q1b) Identify Sample Swap
Data exploration and quality control! This should always be the first step of your analysis (even when nobody tells you to do it). You have done this many times in previous seminars and homework. 
- Although you can `plot` to draw a scatter plot matrix, this is slow and hides some detail. Check Seminar 3 for better graphic alternatives.

### Q1c) Microarray Differential Expression
You want to swap b1 <--> c2. Yes, this is what you have to prove in question 1b. But if something went wrong there, you can start fresh here. Question 3 depends on getting this part correct. So: 
- make sure you fix the column names before doing a differential expression analysis (DEA)
- you may want to reorder the columns in the data so that you have all batch samples together and all the chemostat together. This is not really needed. Just be careful about the order of the samples if you write the design matrix by hand
- check that things are ok now (redo some of the plots from Q1b) 
- we did not ask for this, but it is good practice to write the fixed version of the data to file for future use. If you don't do this then you would need to run the code to fix the swap everytime you work with the data

The DEA is a standard two group comparison with `limma`:
- Create a factor that reflects the change in labels made in Q1b-c. Use it to create the design matrix for this analysis. 
- Run the DEA *before* filtering probes with non-matching gene names, i.e., call `topTable()` before filtering. Your statistical tests should not be affected by the annotation of genes in a database.
- However, since the aim of this HW is to compare results from different platforms, after performing all statistical tests, we are going to focus only in those probes matching to a gene ID. Thus, you will *fileter* the results obtained in your `limma` analysis and use the *filtered* set to respond to questions Q1cii-iv  and Q3.
- Follow the hint given in the HW to identify the gene matching to each probe (i.e., unlist(mget(probe.ids, yeast2ORF))). It is important to use unlist here instead of as.character, in terms of preserving NAs as proper NAs not the string 'NA'.
- Since these results are needed to respond Q3, we ask you to save them to file using `write.table`. This way, you won't need to re-run your analysis to answer to other questions. Specify `col.names=NA` in order to get the column headers to line up correctly in the file. 

## Question 2: RNA-Seq Analysis

### Q2b) Voom+LIMMA

This is covered in Seminar 7. Use good names to store your results. Avoid calling your results `results`. Instead, you can use `voom.deep.results` for example. Use consistent naming scheme.

Note that the example in Seminar 7 is testing the hypothesis that both the intercept and the treatment effect coefficients are zero. If you are looking for DE genes, and you are using a "reference + treatment effects" parametrization, you want to test if the "treatment effect" coefficient is equal to zero. Thus, within `limma`, you explicitly need to specify which coefficient you want to test using the `topTable` function and the argument `coef`. 


## Question 3: Compare RNA-Seq with array DEA
Here you will compare the RNA-Seq DEA with the array DEA results. You should have two dataframes containing the results from these analyses. If these are not in the memory of your R session, you can load the results that you saved in previous questions. 

### Q3a) Density plots
There are many ways to answer this question. One option is to use the function `merge` passing the argument `by="gene.id"` (gene.id are in both data frames). If you use this function, note that most of the columns in these data frames have the same name. Thus, it will also be helpful to add a *suffix* to the column names from each data frame. For example if you had the results stored in data frames called "array.results" and "voom.deep.results", the merge command would be `merge(array.results, voom.deep.results, by="gene.id", suffixes=c(".array", ".rnaseq"))`. Also, note that the RNASeq data contain more genes than those analyzed in the array data. The argument `all=TRUE` controls which genes are kept in the resulting data frame.

Why are we asking for two plots in this questions? From the previous analysis, you’ve noted that each platform measured different number of genes. Thus, it is interesting to look at two sets of genes: those genes shared by both platforms (plot 1), and all studied genes (i.e., by at least one platform) (plot 2). Both plots illustrate 2 density curves, one for array's q-values and one for RNA-Seq's q-values.

### Q3b) Individual genes
In this question we want you to plot the expression and counts of 5 genes. You may find the function `intersect()` useful. This function can be used to find elements presents in two vectors. 

Once you select the genes based on your previous analyses, the most difficult part is to create a dataframe with expression and logged counts to be passed to your plot function.

## Q4: Deep vs low sequencing
The only new component in this question is the edgeR analysis (covered in Seminar 7) and the comparison of results using Venn diagrams (see hint in hw description). 

