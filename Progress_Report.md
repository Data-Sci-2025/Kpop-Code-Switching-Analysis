---
format: gfm
---

#Project Progress Reports
##Nicole Giles

###Entry 1: October 7th, 2025

I have refined my research questions and widened my data pool to include all of the songs on the four albums I chose to analyze. This will make for a hopefully more rich data pool and just generally provide more to look at. I also found some packages I can try out to help me identify the Korean versus English words in the lyrics;  __textcat__ package or the __cldr__ package. I am not sure which works best for my purposes but plan to look into the exact functions on each as I start the actual coding process.

I set up the repository and provided a more detailed plan of my project. I only really had one idea for a project, so I didn't have to spend time on choosing a direction. The 'license' and 'read me' files are established and can be added to later. 

###Progress Report 1

I have managed to compile all of the lyrics for each song onto its own sheets which were then downloaded as separate csv files. I read all of these csv files into R using tidyverse functions. These csv files were then compiled into a bigger dataframe so that I can hopefully view data all in one place. 

**Next Steps**

The combined dataframe is really messed up currently. I need to fix it so that the rows of lyrics show up for each file because currently R is not showing every row for some reason. With a fixed combined dataframe I should be able to then clean up the names of the columns so that they only include the names of the songs. I also plan to use a lot of tidy text functions so that each lyric can be its own item instead of having the lyrics split line by line as the website I pulled them from had them.



