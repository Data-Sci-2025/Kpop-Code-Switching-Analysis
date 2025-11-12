
## Reading in the Data

``` r
#reading in packages I will need
library(tidyverse)
```

    ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ✔ ggplot2   3.5.2     ✔ tibble    3.3.0
    ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ✔ purrr     1.1.0     
    ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ✖ dplyr::filter() masks stats::filter()
    ✖ dplyr::lag()    masks stats::lag()
    ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
#reading multiple files of data into R and combing them into one list (I can't seem to make a dataframe plz send help)

dfLyrics <- c("Nontitle_Shining_Diamond_15.csv", "Title_Adore_U_15.csv", "Nontitle_Twenty_15.csv", "Nontitle_Ah_Yeah_15.csv",
"Nontitle_Jam_Jam_15.csv",
"Nontitle_Fearless_20.csv",
"Nontitle_Fire_23.csv",
"Nontitle_Candy_24.csv",
"Nontitle_Dust_23.csv",
"Nontitle_Eyes_On_You_24.csv",
"Nontitle_F_ck_My_Life_23.csv",
"Nontitle_Fire_23.csv",
"Nontitle_April_shower_23.csv",
"Nontitle_I_Dont_Understand_But_I_Luv_U_23.csv",
"Nontitle_I_Wish_20.csv",
"Nontitle_Kidult_20.csv",
"Nontitle_My_My_20.csv",
"Nontitle_Rain_24.csv",
"Nontitle_Together_20.csv",
"Nontitle_Water_24.csv",
"Title_Left_and_Right_20.csv",
"Title_Love_Money_Fame_24.csv",
"Title_One_to_Thirteen_24.csv",
"Title_Super_23.csv")



# The code below this doesn't work.
#long_Lyrics <- list_rbind(dfLyrics, names_to = "lyrics")          

#dfLyrics |> 
 # pivot_longer(
  #  cols = starts_with("Title"| "Nontitle"), 
   # names_to = "Song Name", 
    #values_to = "Lyrics")
```

## Cleaning up the Data

One day I will have data to clean. Please slack me if you can help me.

Session Info

``` r
sessionInfo()
```

    R version 4.5.1 (2025-06-13 ucrt)
    Platform: x86_64-w64-mingw32/x64
    Running under: Windows 10 x64 (build 19045)

    Matrix products: default
      LAPACK version 3.12.1

    locale:
    [1] LC_COLLATE=English_United States.utf8 
    [2] LC_CTYPE=English_United States.utf8   
    [3] LC_MONETARY=English_United States.utf8
    [4] LC_NUMERIC=C                          
    [5] LC_TIME=English_United States.utf8    

    time zone: America/New_York
    tzcode source: internal

    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     

    other attached packages:
     [1] lubridate_1.9.4 forcats_1.0.0   stringr_1.5.1   dplyr_1.1.4    
     [5] purrr_1.1.0     readr_2.1.5     tidyr_1.3.1     tibble_3.3.0   
     [9] ggplot2_3.5.2   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] gtable_0.3.6       jsonlite_2.0.0     compiler_4.5.1     tidyselect_1.2.1  
     [5] scales_1.4.0       yaml_2.3.10        fastmap_1.2.0      R6_2.6.1          
     [9] generics_0.1.4     knitr_1.50         pillar_1.11.0      RColorBrewer_1.1-3
    [13] tzdb_0.5.0         rlang_1.1.6        stringi_1.8.7      xfun_0.52         
    [17] timechange_0.3.0   cli_3.6.5          withr_3.0.2        magrittr_2.0.3    
    [21] digest_0.6.37      grid_4.5.1         rstudioapi_0.17.1  hms_1.1.3         
    [25] lifecycle_1.0.4    vctrs_0.6.5        evaluate_1.0.5     glue_1.8.0        
    [29] farver_2.1.2       rmarkdown_2.30     tools_4.5.1        pkgconfig_2.0.3   
    [33] htmltools_0.5.8.1 
