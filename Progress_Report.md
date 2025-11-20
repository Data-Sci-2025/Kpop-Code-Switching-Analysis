---
format: gfm
---

# Project Progress Reports 

## Nicole Giles  

### Entry 1: October 7th, 2025

I have refined my research questions and widened my data pool to include all of the songs on the four albums I chose to analyze. This will make for a hopefully more rich data pool and just generally provide more to look at. I also found some packages I can try out to help me identify the Korean versus English words in the lyrics;  __textcat__ package or the __cldr__ package. I am not sure which works best for my purposes but plan to look into the exact functions on each as I start the actual coding process.

I set up the repository and provided a more detailed plan of my project. I only really had one idea for a project, so I didn't have to spend time on choosing a direction. The 'license' and 'read me' files are established and can be added to later. 

### Progress Report 1

I have managed to compile all of the lyrics for each song onto its own sheets which were then downloaded as separate csv files. I read all of these csv files into R using tidyverse functions. These csv files were then compiled into a bigger dataframe so that I can hopefully view data all in one place. 

**Next Steps**

The combined dataframe is really messed up currently. I need to fix it so that the rows of lyrics show up for each file because currently R is not showing every row for some reason. With a fixed combined dataframe I should be able to then clean up the names of the columns so that they only include the names of the songs. I also plan to use a lot of tidy text functions so that each lyric can be its own item instead of having the lyrics split line by line as the website I pulled them from had them.



### Progress Report 2

I have not finished compiling my data and am not ready for analysis in time for this report. 

Here is what I have accomplished since the last check in:
- I have attempted to use web-scraping as a way to obtain the data, but found that the most I could manage was a list of links that led to each individual webpage for each song I wanted to analyze. Some of the code was created using our textbook as a reference, but some was created with the help of AI (ChatGPT). Since I don't have permalinks to my chat with the system and do not remember how much of my limited progress was from which aid. Thus, this attempt at wrangling/organizing the data was abandoned. 

-I went back to my (many) csv files that I organized from the information provided on colorcodedlyrics.com and read them all into R using read_csv(). I can't get the files to open and show everything inside because my code can only produce a list, not a vector. 

Here is what I hope to accomplish by the next report:
- I want to have my data actually visible and tidied.


### Progress Report 3

I have still not finished organizing my data, but here is what I accomplished since the last check-in:  
- I abandoned the attempt at web-scraping after discovering it would not be necessary for this project. 
- I managed to successfully create columns for all of the metadata that was contained in the csv file names of the songs I am analyzing.
- I put the lyrics of the songs into one long list and used tidytext to put each word in its own column, really putting the data in its longest form. From there I was able to detect the language of each word using stringr. Right now, the question which language each word is is in columns called "English" and "Korean" with TRUE or FALSE statements in each row. 
- I fixed my license file to more accurately match my intentions with this project's further use. 

My working code is in the Quarto document titled 'data_processing'. This document has been added to and edited as I progressed in tidying my data. 

My immediate next steps include:  
- Finally analyzing the data I've tidied so that I can understand the ratio of Korean to English lyrics over all four albums as well as per album. My goal is to see whether there is an increase in the use of English over time, i.e. after clear success with the album from 2023. 
- I hope to also be able to say something about what kind of language is used in English instead of Korean (though this may have to more of a qualitative step instead of a quantitative one at this point). 

Overall, I know that I am not reaching the goals of each progress report as they are due. However, I find confidence in the fact that I am still reaching the intended goals later (which is better than never). My skills as a linguist are stronger than my skills as a programmer/data scientist, and can carry overall analysis of the data I belatedly tidied up.  





