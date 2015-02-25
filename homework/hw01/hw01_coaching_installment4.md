Homework 1 Coaching
========================================================

### Installment 4

Recap of where we are:

* By now, you should have a good idea of how the data looks like
* In Q3 you've explored the significance of `treatment` in gene expression data using `limma`

**Note**: In all your solutions to the HW questions, it is important to interpret and explain the results! It is not enough to write the correct code and get the correct output.

### Q4: Assess differential expression with respect to `time`

Now we tackle question 4, the second differential expression analysis. In Q4 we look at a single quantitative covariate `time`. Just like Q3, we first ask if this model is clearly favoured over an intercept-only model. This is accomplished with limma::topTable(), using the `coef =` argument, again. Finding the number of probesets with q-value less than a threshold should be easy using the topTable() function and its output. In terms of models, the main different between the current model and that in Q3 is that `time` is a continuous covariate, instead of a categorical variable. Think if this affects the way you analyze the data and how you interpret the results.

### Q5: Full model: `treatment` and `time`

To enhance the scientific validity and the strength of the results, we now fit a model with *both* relevant variables as covariates. Note that Q5a does not ask you to test if the full model is equally relevant than the intercept-only model. We want to address whether `treatment` seems to matter once we include `time` in the model. Now you need to be careful asking topTable() to give you the p-values you need! Again, you can specify different parameters via `coef =`. Similarly, question Q5b asks for the relevance of the interaction term. 

Of course the answer to these question will vary from probeset to probeset. But it's also nice to zoom out a bit and try to do something global. One way of doing this is to compare the distribution of p-values from different tests (see Q5a).

Once you finish this, you are technically done. But stay tuned for a final coaching instalment. For those who have the time to revisit their work, we'll review some typical, "nice to do" polishing tasks.
