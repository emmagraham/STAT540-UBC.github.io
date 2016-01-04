# Syllabus





### Prerequisites and useful skills

Officially none BUT here in reality ...

**Statistics**: You should have already taken university level introductory statistics course.

**Biology**: 

- No requirements, but you are expected to learn things like the difference between a DNA and RNA and a gene and a genome
- See [Seminar-1c](sm01c_biology-intro.pdf) 

**R**: 

- No experience required but be prepared to do a lot of self-guided learning if you haven't taken other courses on R. 
- Start now by installing R and the HIGHLY RECOMMENDED "integrated development environment" (IDE) RStudio! 
- Best set-up: be able to run R on your own computer and bring your own laptop to each seminar.
- If you are new to R, check out [this blog post on getting started with R](http://santina.me/r/2015/12/15/Get-started-with-R.html). 

**Others:** 

- You'll need to know how to use [Git](https://stat545-ubc.github.io/git01_git-install.html) and GitHub. 
- We'll soon learn about [using Rmarkdown](https://stat540-ubc.github.io/sm02a_rMarkdown.html) to generate reports, and you'll be using that a lot in this course. 

### Evaluation

**Homework**: 

- One assignment worth 30 points. (see calendar below).
- Involve detailed analysis of real data using R 
- Due two weeks after the assignment is posted (coming soon!)


**Group project**: 

- A data analysis group project that will allow you to apply the techniques covered in class
- Important dates: 
    - Now - January 22: Pitch your ideas, find an idea, form a 4-5 people group 
    - January 29: Finish the initial project proposal
    - February 12: Receive feedback on the project proposal 
    - February 12: Finalize the proposal 
    - April 6: Poster session 
- Grading and deliverable 
    - Primary deliverable is a poster. Each student also produces a short report 
    - Planning + project + poster session - 50 points 
    - Peer evaluation - 10 points 
- Tip: try to form a group of diverse talents

**Paper critiques**

- Summarize and critique 2 papers - 5 points each 
- Select, read, summarize and critique a recent paper from the âomics literature â write one page max
- Instruction on the paper critiques will be posted shortly 

<!-- unholy hack to make following two tables less wide and the same wide -->
<style type="text/css">
table {
   max-width: 70%;
}
</style>

### Class mettings

**Time** : Mon Wed 9:30 - 11am

**Location** : ESB 4192

**Calendar**


date         notes                                                                                                                 instructor 
-----------  --------------------------------------------------------------------------------------------------------------------  -----------
Jan-04 Mon   <a href="lect01_course-intro.pdf">lecture-1</a>: Intro to course                                                      PP         
Jan-06 Wed   <a href="lect02_introToStatInf-probBasics.pdf">lecture-2</a>: Review of probability & inference                       SM         
Jan-11 Mon   <a href="lect03_introToStatInf-endProbBasics-genInfReview.pdf">lecture-3</a>: Review of probability & inference       SM         
Jan-13 Wed   <a href="lect04_exploration.pdf">lecture-4</a>: Exploratory data analysis                                             PP         
Jan-18 Mon   <a href="lect05_dataCleaning-qualityControl.pdf">lecture-5</a>: Data QC and preprocessing                             SM         
Jan-20 Wed   <a href="lect06_two-groups.pdf">lecture-6</a>: Statistical inferene: two group comparisons                            SM         
Jan-22 Fri   Project groups should be formed                                                                                       NA         
Jan-25 Mon   <a href="lect07_beyondTwoGroups.pdf">lecture-7</a>: Statistical inferene: more than two groups                        SM         
Jan-27 Wed   <a href="lect08_moreThanOneCatCovariate-linModGreatestHits.pdf">lecture-8</a>: Statistical inference: linear models   SM         
Jan-29 Fri   Project proposals due                                                                                                 NA         
Feb-01 Mon   <a href="lect09_quantCovariate-manyLineModAtOnce.pdf">lecture-9</a>: Statistical inference: linear models             SM         
Feb-03 Wed   <a href="lect10_limma.pdf">lecture-10</a>: Statistical inference: large scale, limma, empirical bayes                 SM         
Feb-05 Fri   HW1 posted                                                                                                            NA         
Feb-08 Mon   No class; Family Day                                                                                                  NA         
Feb-10 Wed   <a href="lect11_multipleTesting.pdf">lecture-11</a>: Statistical inference: multiple testing                          SM         
Feb-12 Fri   Initial feedback on project proposals                                                                                 NA         
Feb-15 Mon   Winter break                                                                                                          NA         
Feb-17 Wed   Winter break                                                                                                          NA         
Feb-22 Mon   <a href="lect12_RNAseqI.pdf">lecture-12</a>: RNA-Seq data analysis I                                                  PP         
Feb-24 Wed   <a href="lect13_RNAseqII.pdf">lecture-13</a>: RNA-Seq data analysis II                                                PP         
Feb-29 Mon   <a href="lect14_Methylation_Presentation_2015.pdf">lecture-14</a>: Epigenetic data                                    TBA        
Feb-29 Mon   HW1 due                                                                                                               NA         
Mar-02 Wed   <a href="lect15_PCA.pdf">lecture-15</a>: PCA                                                                          PP         
Mar-04 Fri   HW2 posted + Final project proposals due                                                                              NA         
Mar-08 Mon   <a href="lect16_clustering.pdf">lecture-16</a>: Clustering                                                            SM         
Mar-09 Wed   <a href="lect17_supervised-learning.pdf">lecture-17</a>: Classification                                               SM         
Mar-14 Mon   <a href="lect18_supervised-learning-II.pdf">lecture-18</a>: Cross validation                                          SM         
Mar-16 Wed   <a href="lect19_regularization.pdf">lecture-19</a>: Regularization                                                    SM         
Mar-21 Mon   <a href="lect20_function1.pdf">lecture-20</a>: Resampling and bootstrap                                               SM         
Mar-23 Wed   <a href="lect21_function2.pdf">lecture-21</a>: Analysis of gene function I                                            PP         
Mar-25 Fri   HW2 due                                                                                                               NA         
Mar-28 Mon   No class; Easter Monday                                                                                               NA         
Mar-30 Wed   <a href="lect22b_resampling.pdf">lecture-22</a>: Analysis of gene function II                                         PP         
Apr-04 Mon   lecture-23: Guest lecture                                                                                             TBA        
Apr-06 Wed   Poster session                                                                                                        NA         

### Seminars

**Time**: Wed 12pm - 1pm (but welcome to come after class around 11am)

**Location**: ESB 1042 and 1046

**Calendar**


date         lect                                                                                raw_notes                                                                   instructor 
-----------  ----------------------------------------------------------------------------------  --------------------------------------------------------------------------  -----------
Jan-06 Wed   <a href="https://stat545-ubc.github.io/git01_git-install.html">seminar-1a</a>       11am-12pm: Getting ready to use GitHub in STAT540, borrowed from STAT545A   TBA        
Jan-06 Wed   <a href="sm01b_gitIntro-basic-data-exploration.html">seminar-1b</a>                 11am-12pm: Git(hub) Intro & Exploring a small gene expression dataset       TBA        
Jan-06 Wed   <a href="sm01c_biology-intro.pdf">seminar-1c</a>                                    12pm-1pm: Molecular biology/genetics 101                                    TBA        
Jan-13 Wed   <a href="https://stat540-ubc.github.io/sm02a_rMarkdown.html">seminar-2a</a>         Markdown                                                                    TBA        
Jan-13 Wed   <a href="https://stat540-ubc.github.io/sm02b_introProbCltLln.html">seminar-2b</a>   Probability and simulations (part I)                                        TBA        
Jan-13 Wed   <a href="sm02c_playing-with-probability.html">seminar-2c</a>                        Probability and simulations (part II)                                       TBA        
Jan-20 Wed   seminar-3                                                                           R graphics AND knitr, R markdown, and git(hub)                              TBA        
Jan-27 Wed   seminar-4                                                                           Two group testing and data aggregation                                      TBA        
Feb-03 Wed   <a href="sm05_lowDimLinMod.html">seminar-5</a>                                      Fitting and interpretting linear models (low volume)                        TBA        
Feb-10 Wed   <a href="sm06_highVolumeLinearModelling.html">seminar-6</a>                         Fitting and interpretting linear models (high volume), limma package        TBA        
Feb-24 Wed   <a href="sm07_RNA-seq-bam.html">seminar-7</a>                                       RNA-Seq analysis                                                            TBA        
Feb-24 Wed   <a href="sm07_RNA-seq.html">seminar-7</a>                                           RNA-Seq analysis                                                            TBA        
Mar-02 Wed   <a href="sm08_methylation.html">seminar-8</a>                                       Methylation analysis                                                        TBA        
Mar-09 Wed   <a href="sm09_clustering-pca.html">seminar-9</a>                                    Clustering and PCA                                                          TBA        
Mar-16 Wed   <a href="sm10_classification.html">seminar-10</a>                                   Supervised learning, cross validation, variable selection                   TBA        
Mar-23 Wed   seminar-11                                                                          TA office hours during seminar time ... group project work                  TBA        
Mar-30 Wed   seminar-12                                                                          TA office hours during seminar time ... group project work                  TBA        
