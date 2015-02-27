Homework 1 Coaching
========================================================

### Installment 5

At this point, you have technically completed this assignment. But here are some minor tweaks that can make a big difference in how awesome your product is. This is a summary of what was posted before in the "Assignments" tab.

**Make it easy for people to access your work**

Create a `README.md` in the homework's subdirectory to serve as the landing page for your submission. Include links to relevant documents, such as:
  * Your main R markdown document.
  * The intermediate Markdown product that comes from knitting your main R markdown document. Remember the figures in `figures/` need to be available in the repo in order appear here.
  * The final pretty HTML report. Read instructions below on how access the pretty, not the ugly source.

**Linking to HTML files in the repo**

Simply visiting an HTML file in a GitHub repo just shows ugly HTML source. To see a pretty HTML:

  * Navigate to the HTML file on GitHub. Click on "Raw" to get the raw version; the URL should look something like this: `https://raw.github.com/stat540-2014-bryan-jennifer-hw/hw01/stat540-2014-bryan-jennifer-hw01.html`. Copy that URL!
  * Create a link to that in the usual Markdown way BUT prepend `http://htmlpreview.github.io/?` to the URL. So the URL in your link should look something like this: `http://htmlpreview.github.io/?https://raw.github.com/stat540-2014-bryan-jennifer-hw/hw01/stat540-2014-bryan-jennifer-hw01.html`. 
  
**Make it easy for others to run your code**

  * In exactly one, very early R chunk, load any necessary packages, so your dependencies are obvious.
  * In exactly one, very early R chunk, import anything coming from an external file. This will make it easy for someone to see which data files are required.
  * Pretend you are someone else. Clone a fresh copy of your own repo from GitHub, fire up a new RStudio session and try to knit your R markdown file. Does it "just work"? It should!
  
**Make pretty tables**

There are a few occasions where, instead of just printing an object with R, you could format the info in an attractive table. Some leads:

  * The `kable()` function from `knitr`.
  * Also look into the packages `xtable`, `pander` for making pretty HTML tables.

**"Turn in" your homework**

You are done!! and ready to submit your work

  * Make sure you have 
    - Saved all the files associated with your solution locally.
    - Committed those files to your local Git repository.
    - Pushed the current state of your local repo to GitHub.
    
  * Open an issue, link to the latest commit, tag us
    - Visit your private GitHub repository in a web browser
    - Just above the file list, look for the text "latest commit" followed by ten numbers and letters (called the revision SHA) and a clipboard icon
     - Click on the clipboard icon to copy the revision SHA to your clipboard
    - Click on "Issues", then on "New Issue". Name the issue "Mark homework 1 of *firstname-lastname*"
    - In the description of the issue, tag Gaby and both TAs by including the text `@gcohenfr`, `@wdurno`, `@aliceZhu`, and paste the revision SHA. Include a link to exactly where you want a reviewer to go! 
     - Click "Submit new issue". 
     
**You're done! Congratulations!**

> If you're concerned that something hasn't gone right with the submission, send Alice jingyunalice@gmail.com  and Evan wdurno@gmail.com an e-mail with your assignment attached. **Note**: this is *only* an emergency back-up plan. 
  