---
title: "Assignments"
output:
  html_document:
    includes:
      before_body: ../include/nav.html
      after_body: ../include/nothing.html
    toc: 3
---

## Homework 
- Will be posted on the week of February 12 
- Due date: March 18
- For help on your homework mechanics, please see this list of [assignment tips](../assignment_tips.html) 

### STAT 540 Homework Submission Instructions

**GitHub**
You all have a private repository in STAT540-UBC organization account, i.e., the repo `lastname-firstnmae_STAT540_2016` . We assume that 

* You've already installed Git and (probably) a Git client.
* You can use command line Git and/or your Git client and perhaps even RStudio to push, pull, etc. to/from GitHub. 
* All your work is nicely organized in *this* repository. Your repository needs to include a clear top-level `README.md` that contains links to your work. This is the presentation of your repository and it helps others to find your work and contributions!

**IMPORTANT NOTE**: use the repository within the organization assigned to you to submit all your course work (i.e., the repo `lastname-firstnmae_STAT540_2016`). Do not use branches or other repositories.
  

**Set-up your private GitHub repo for homework**

  * We're talking about the repo `zz_lastname-firstnmae_STAT540_2016` now.
  * Make a top-level directory for your assignment, e.g. `Homework`
    - We truly mean a [directory or "folder"](http://en.wikipedia.org/wiki/Directory_(computing)) -- NOT a [Git branch](http://git-scm.com/book/en/Git-Branching) or anything fancy like that! On your local computer, go to the directory where this Git repository lives. Make the 2 directories here.    
  * It is also nice to include a `README.md` inside each of the assignment and seminar directories. 
    - GitHub automatically renders all Markdown files into (pseudo-)HTML when you visit them in a browser. Whenever a *directory* in a repo is visited, if it contains a Markdown file called `README.md`, it will automatically be rendered, effectively serving as a landing or home page.

**R Markdown**

  * Write your homework in R Markdown. The file extension should be `.rmd`.
  * Recommendation: Create a skeleton of your report by starting with the Markdown file that creates the assignment itself! You can take some things away (unnecessary detail) and add others (R chunks) to morph this into your homework solution.
    - [Source for 2016 homework assignment 1](https://github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/homework/homework.md)
    - You'll have these files if you are using Git(Hub) to keep a current copy of the whole course repository. Or, from the links above, click on "Raw" to get raw Markdown and save to a local file.
    
**HTML**

  * Compile your homework to Markdown (file extension should be `.md`) and then to HTML (file extension should be `.html`).
    - RStudio's "Knit HTML" button will do this
    - Alternatively, use `knit2html()` from the `knitr` package in the R Console or in an R script.
    - To run from the shell or in a Makefile, use something like `Rscript -e "knitr::knit2html('hw01_lastname-firstnmae.rmd')"`
  * Notice that, by default, any figures created are placed into a `figures/` subdirectory. The intermediate Markdown file links to these and, therefore, requires them to present your full report. By default, the figures are base64 encoded and *embedded* into the HTML, which, therefore, is self-contained.

**What to put (or not put) into your Git(Hub) repository**

> This is rather specific to STAT 540 and may not necessarily reflect your workflow in the future and in other contexts.

  * Commit the main R markdown (`.rmd`) file that constitutes your solution. Commit early, commit often!
  * Do not commit the input data to your repository.
    - Locally, you are of course encouraged to keep the file in some logical place within the homework assignment's directory. But list the names of such data files in your top-level [`.gitignore` file](http://git-scm.com/docs/gitignore), so that Git ignores it. We do this so that TAs don't end up with 50 copies of the input data when they mark your work.
  * Commit the intermediate Markdown (`.md`) file and the figures stored in the `figures/` subdirectory.
    - Some purists would say intermediate and downstream products do NOT belong in the repo. After all, you can always recreate them from source, right? But here in reality, it turns out to be incredibly handy to have this in the repo.
  * Commit the end product HTML (`.html`) file.
    - See above comment re: version control purists vs. pragmatists.
  * Push closer to the submission date.
  * __Never ever__ edit the Markdown or HTML "by hand". Only edit the R Markdown source and then regenerate the downstream products from that.

**How to "turn in" your homework**

  * Make sure you have 
    - Saved all the files associated with your solution locally.
    - Committed those files to your local Git repository.
    - Pushed the current state of your local repo to GitHub.
  * Open an issue, link to the latest commit, tag us
    - Visit your private GitHub repository in a web browser
    - Just above the file list, look for the text "latest commit" followed by ten numbers and letters (called the revision SHA) and a clipboard icon
     - Click on the clipboard icon to copy the revision SHA to your clipboard
    - Click on "Issues", then on "New Issue". Name the issue "Mark hw0x of *your repository name*", where *x* is, e.g. 1 or 2.
    - In the description of the issue, tag Sara and both TAs by including the text `@saramostafavi`, `@marjanfarahbod`, `@santina`, and paste the revision SHA. Include a link to exactly where you want a reviewer to go! 
     - Click "Submit new issue". You're done! Congratulations!

> If you're concerned that something hasn't gone right with the submission, send Marjan and Santina (marjan.farahbod@gmail.com, santina424@gmail.com) an e-mail with your assignment attached. **Note**: this is *only* an emergency back-up plan. We will pester and work with you until you eventually get it submitted via GitHub.


## Paper review 
Each student should find two papers in the field of Bioinformatics and submit about one page (450 - 650 words) of summary/report for each of the papers. The summary should include: 

1. A brief review of the goal, findings and conclusion of the paper written by the student. 
2. A list (or mentioning) of the related datasets/databases and data types used in the study. In the case of datasets, provide some details of the data matrix and meta data.
3. A brief review of the analytical steps in the paper with more details on some selected parts which are relevant to the course materials. *You don't need to understand all of the analysis, but should be able to identify the key analysis/method used to answer the question the paper is intended to answer*
4. Some comments and critics about the analytical steps, alternative suggestions or improvements. 

We have provided [**this**](http://stat540-ubc.github.io/homework/paper\_critique/PRguideline.html) document as a brief guideline for this task. The material in the review **should not** be limited to merely answering the questions in the guideline, but rather using them to provide the required items listed above. Example paper reviews are also provided. 

**Important:** Students should submit the initial information about their selected papers in respond to the [**issue Paper Review - 01**](https://github.com/STAT540-UBC/Discussion/issues/110) (there will be another issue for paper review 02) in Github and make sure no one else has already picked it by checking the other student's respond to the same issue. Yup... first come first served! But no worries, there are plenty of interesting papers! 

* Due date for the first paper review: <font color="red">Feb 22nd</font>
* Due date for the second paper review: <font color="red">April 1st</font>

**Delivery:** You should put your paper review files in your individual course repository in .md format (notice that you don't need to write it in .Rmd since you are not going to have any R code in it). You could edit .md files directly from github and therefore can write your full report there, but can also write it in your RStudio and then push it to your repository. Your paper review file should be named _paperreview01_ for the first one and _paperreview02_ for the second one and each file should have the following the beginning:

1. The name of the paper with link to pubmed or the journal 
2. The month and year it was published 

[example paper review 01](https://github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/homework/paper_critique/paperReviewMarjan.md)

[example paper review 02](https://github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/homework/paper_critique/paperReviewSantina.md)

## Final group project

### General principles

Identify a biological question of interest and a relevant dataset. Develop and apply a statistical approach that allows you to use the dataset to answer the question.

We assume the biological question and data fall in the general area of high-throughput, large-scale biological investigations *targetted by the course*. Beyond that it is wide open: methylation, SNPs, miRNAs, CNVs, RNA-Seq, CHiP-Seq, gene networks, ... it's fair game. Avoid a dataset that doesn't have any/much quantitative data, i.e. contains only sequence or discrete data.

Note that definitive answers are not necessarily expected. Rather, aim to provide a critical appraisal of the data, the analytical approach, and the results. You will have to handle the competing pressures to "get it right" and "get it done". Shortcomings of the data, misfits between the data or the biological question and the statistical model, etc. are inevitable. Your goal is to identify such issues and discuss them critically, without becoming paralyzed. Demonstrate understanding of the statistical concepts and methods that are the foundation of your analytical approach.

We assume the analytical and computing task will have a substantial statistical component, probably enacted via R. So beware of a major analytical or computational undertaking that is, nonetheless, not statistical (example: constructing a database). Creating useful data visualizations can be absolutely vital and is arguably statistical, but your analysis should go beyond merely creating pretty pictures (but please do include some!). Key concepts, at least some of which should come up in your analysis:

 * the (hypothesized, probably artificial) data-generating model

 * background variation, variance, signal to noise ratio, estimates and their associated standard error

 * relationship between biological factors and experimental factors, apparent relative importance in terms of "explaining" observed data

 * attention to large-scale inference, e.g. control of family-wise error rate or false discovery rate

### Group makeup

Groups should have 4 to 6 members. We strongly encourage that groups be diverse in terms of backgrounds. In practice, this probably means the students should registered in a mix of programs/departments. All groups and group projects must be approved by the instructors.

### Initial deliverables

**Due January 22 (but submit earlier if you are ready)**

 * List of group members. In addition to names, include relevant info on grad program, lab, interests/expertise. 

**Due January 29**
 * Initial project proposal describing basic idea of project. Think: a paragraph.

Each group will submit their work by responding to the Issue called "Group project: initial information" in the Discussion repository. Please, post only one proposal per group.

This information will be used to create a private repository for each group to host all work related to the project.

**Due Friday February 15**
  
  * One page proposal should probably be part of the `README.md` for the repo, or should be linked in the `README.md`. Incorporate all comments given by professors/TAs. This proposal needs to outline:
    - a clear motivation of the problem/question we will investigate
    - general goals of the project 
    - general description of the data 
    - specific questions you will address with division of labour
    - the methodology you will use to address these questions

  * Include the nice table re: group membership in the `README.md`
    - add students' degree program, i.e. MSc vs PhD vs other
  
  * Nail down data sources
    - bring the data into the repo, if small enough.
    - alternatively, distribute data to necessary group members some other way and document in the repo, e.g. link to where data came from
    - a `data` subdirectory is a good default place to document the datasets. add `README.md` file in the subdirectory to describe your data in more detail, e.g., how many rows, how many columns, experimental design, HTML-ified code showing basic import and smell-testing, etc.
    
### Final deliverables

* **Poster**: to be hosted and exhibited in our poster session on Wed Apr 6 from 9:30 am to 12 pm in the Atrium of the ESB. Group-level deliverable. 

    - Ideally, you will print your poster in the usual conference format (48''x36''). I know it is a non-trivial cost but not impossible if divided up. Sometimes supervisors will help, esp. if the poster can be displayed or used elsewhere. Prices at the village and the Sub tend to be resonable.
    
    - a rubric for poster evaluation can be found [here](https://github.com/STAT540-UBC/STAT540-UBC.github.io/blob/master/posterRubric2012.pdf)


* **Project progress report:** <font color="red">Due March 4th</font> 

    The project report should include the following information:

    1. What is changed based on the initial proposal:
    
      - If you have decided to do different analysis and why
      
      - If your task assignment has changed and team members are doing different things now
      
      - If you have changed your data or the datasets you use and why.
  
  
    2. What is the progress on the tasks and analysis mentioned in your proposal:
    
      - What analysis are finished (if any) and what are totally untouched
      
      - How much have you progressed in the rest of the tasks
   Mention if you have decided which plots you want to use (volcano, heatmap, etc.)
   

* **Project GitHub repository**: This should contain the materials (or associated live links) an instructor would need to evaluate your work and that a group member would need to reproduce/reuse/extend the work. Group-level deliverable. Content should include (but is not limited to!):

    - revised README.md file containing a summary of your work. This file should summarize the project content, your analysis, and main results. You don't need to tell us all the story of your analysis here. Keep it brief. You can include a flow chart if you find it useful. Add links as needed

    - a PDF of the poster

    - important files, such as "inputs" (e.g. the dataset(s) you analyzed) and "outputs" (e.g. plain text files of your key statistical results or PDFs of your main figures); if you started with a publicly available file, you can link to it

    - R Markdown that host the R code for the analysis. Compile this R Markdown source to Markdown, commit and push both. This file can include more than you present in the poster. It is your technical report. Add brief comments and text throughout explaining the aim and conclusions of each part

    - a link-y version of your bibliography (for example, live Pubmed or DOI links).


* **Short individual report (1 page)**: 
Individual deliverable. Include:
    - concise summary of main role / contribution of each group member 
    - more detailed description and reflections on your specific role / contribution
    - scientific reflections. E.g., what worked well / poorly? what seems worth following up vs. a dead end? what was most difficult or most rewarding?

    Submit this individual report via your private GitHub repository, the one you used for homework. Create a new directory called project and, within it, store your report as README.md. Open an issue and tag the TAs as you did for homework submission.
