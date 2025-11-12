
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
library(dplyr)
library(stringr)

#reading multiple files of data into R
lyrics <- list.files(pattern=".csv") |>
  read_csv(id = "file")
```

    Rows: 1582 Columns: 2
    ── Column specification ────────────────────────────────────────────────────────
    Delimiter: ","
    chr (1): Lyrics

    ℹ Use `spec()` to retrieve the full column specification for this data.
    ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
# Putting each song's metadata in separate columns
lyrics$track_type = str_extract(lyrics$file, "Title|Nontitle")
lyrics$album_year = str_extract(lyrics$file, "15|20|23|24")
lyrics$song_title = str_extract(lyrics$file, "[Title|Nontitle|15|20|23|24]")
lyrics
```

    # A tibble: 1,582 × 5
       file                    Lyrics               track_type album_year song_title
       <chr>                   <chr>                <chr>      <chr>      <chr>     
     1 Nontitle_Ah_Yeah_15.csv 아 예 아 예 근데 뭐라구요?…… Nontitle   15         N         
     2 Nontitle_Ah_Yeah_15.csv Yo $. Coup$, Here’s… Nontitle   15         N         
     3 Nontitle_Ah_Yeah_15.csv 등장과 동시에 들러리들 바닥에서…… Nontitle   15         N         
     4 Nontitle_Ah_Yeah_15.csv 침 흘리며 기절 그 위에서 수영해요… Nontitle   15         N         
     5 Nontitle_Ah_Yeah_15.csv WOAH 옆구리 지방튜브 끼고 못 … Nontitle   15         N         
     6 Nontitle_Ah_Yeah_15.csv 애들이 알리 있나     Nontitle   15         N         
     7 Nontitle_Ah_Yeah_15.csv 못 뜬 이유 절대 모름 (Don’t… Nontitle   15         N         
     8 Nontitle_Ah_Yeah_15.csv 맞출 생각 없어       Nontitle   15         N         
     9 Nontitle_Ah_Yeah_15.csv 니 식견에 날 맞추지 말길…… Nontitle   15         N         
    10 Nontitle_Ah_Yeah_15.csv 막 귀들 방구석 박혀 밖에 나오질 … Nontitle   15         N         
    # ℹ 1,572 more rows

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
     [1] bit_4.6.0          gtable_0.3.6       jsonlite_2.0.0     crayon_1.5.3      
     [5] compiler_4.5.1     tidyselect_1.2.1   parallel_4.5.1     scales_1.4.0      
     [9] yaml_2.3.10        fastmap_1.2.0      R6_2.6.1           generics_0.1.4    
    [13] knitr_1.50         pillar_1.11.0      RColorBrewer_1.1-3 tzdb_0.5.0        
    [17] rlang_1.1.6        utf8_1.2.6         stringi_1.8.7      xfun_0.52         
    [21] bit64_4.6.0-1      timechange_0.3.0   cli_3.6.5          withr_3.0.2       
    [25] magrittr_2.0.3     digest_0.6.37      grid_4.5.1         vroom_1.6.5       
    [29] rstudioapi_0.17.1  hms_1.1.3          lifecycle_1.0.4    vctrs_0.6.5       
    [33] evaluate_1.0.5     glue_1.8.0         farver_2.1.2       rmarkdown_2.30    
    [37] tools_4.5.1        pkgconfig_2.0.3    htmltools_0.5.8.1 
