---
title: "Assignment Tips"
output:
  html_document:
    includes:
      before_body: ../include/nav.html
      after_body: ../include/nothing.html
    toc: true
---

This is for tips on the assignment, but also useful for seminars and any future project you might have. 

### When working on the assignment  

- *Start early*. Even if you are already fluent with all the seminars materials, it'd still take time to answer all the questions. 

- When you get stuck or when you run into an error, ask yourself these questions: 
	- Am I in the right working directory ? 
	- Is this material covered in one of the seminars?
	- Can I google the information to find how to do this? 
	- Is there an R package that can more efficiently do what I'm attempting now? 
	- Am I using the right parameters for this function?  (hint, type `?function_name()` where function_name is the name of the function, to check if you're using it right) 
	- Your Rmarkdown can't be knitted ? 

- Well-structured dataframes and reusable functions can often lighten your work load. 

- Overall presentation and mechanics refer to the fluency, neatness, easyness to read. For example:
	- Using headings/subheadings to distinguishes different sections/questions
	- Explain what you're doing to show your understanding, ie sandwiching your code and result with some explanations and interpretation. We don't want to see just a graph or some R outputs standing alone in a question. 
	- Use inline R code whenever you refers to the value of a variable in a block of text. 
	- Hide useless messages or warnings (though make sure the warnings are harmless) using code chunk options. But don't hide any code that generates graphs or are critical steps in your analysis, obviously. 
	- Comment your code 
	- You might find [cheatsheets from Rstudio](https://www.rstudio.com/resources/cheatsheets/) useful, in terms of graphing, making an awesome R markdown, etc.

### Make it easy for people to access your work 

Reduce the friction for TAs and profs to get the hard-working source code (the R markdown) __and__ the front-facing report (HTML).

  * Create a `README.md` in the homework's subdirectory to serve as the landing page for your submission. Whenever anyone visits this subdirectory of your repo, this will be automatically rendered nicely! In particular, hyperlinks will work.
  * With this `README.md` file, create annotated links to the documents TAs and profs will need to access. Such as:
    - Your main R markdown document.
    - The intermediate Markdown product that comes from knitting your main R markdown document. Remember GitHub will render this into pseudo-HTML automagically. Remember the figures in `figures/` need to be available in the repo in order appear here.
    - The final pretty HTML report. Read instructions below on how access the pretty, not the ugly source.
    
> You could link to an HTML report on RPubs, but a GitHub-only solution is preferred. RPubs isn't really necessary once your work is hosted on GitHub.Plus it's kinda nice to keep this private.

If you want to see an example of a `README.md` that links to and explains a bunch of files in the same repo + subdirectory, you can look at an example from Prof Jenny Bryan's STAT 545A [here](https://github.com/jennybc/STAT545A_2013/tree/master/hw06_scaffolds/02_rAndMake)

### Linking to HTML files in the repo

Simply visiting an HTML file in a GitHub repo just shows ugly HTML source. You need to do a little extra work to see this rendered as a proper webpage.

  * Navigate to the HTML file on GitHub. Click on "Raw" to get the raw version; the URL should look something like this: `https://raw.github.com/stat540-2014-bryan-jennifer-hw/hw01/stat540-2014-bryan-jennifer-hw01.html`. Copy that URL!
  * Create a link to that in the usual Markdown way BUT prepend `http://htmlpreview.github.io/?` to the URL. So the URL in your link should look something like this: `http://htmlpreview.github.io/?https://raw.github.com/stat540-2014-bryan-jennifer-hw/hw01/stat540-2014-bryan-jennifer-hw01.html`. 
  * This sort of link would be fabulous to include in `README.md`.

### Make it easy for others to run your code

  * In exactly one, very early R chunk, load any necessary packages, so your dependencies are obvious.
  * In exactly one, very early R chunk, import anything coming from an external file. This will make it easy for someone to see which data files are required, edit to reflect their locals paths if necessary, etc. There are situations where you might not keep data in the repo itself.
  * Pretend you are someone else. Clone a fresh copy of your own repo from GitHub, fire up a new RStudio session and try to knit your R markdown file. Does it "just work"? It should!
  
### Make pretty tables 

There are a few occasions where, instead of just printing an object with R, you could format the info in an attractive table. Some leads:

  * The `kable()` function from `knitr` package.
  * Also look into the packages `xtable`, `pander` for making pretty HTML tables.
