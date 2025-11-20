
## Reading in the Data

The code below shows the code I used to read in the data, where each
song is its own csv file. I then created columns for the metadata
associated with each song.

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
library(tidytext)
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
lyrics$album_year_20XX = str_extract(lyrics$file, "15|20|23|24")
# Can't quite get the song title to work right now
#lyrics$song_title = str_extract(lyrics$file, "")
lyrics
```

    # A tibble: 1,582 × 4
       file                    Lyrics                     track_type album_year_20XX
       <chr>                   <chr>                      <chr>      <chr>          
     1 Nontitle_Ah_Yeah_15.csv 아 예 아 예 근데 뭐라구요? Nontitle   15             
     2 Nontitle_Ah_Yeah_15.csv Yo $. Coup$, Here’s the b… Nontitle   15             
     3 Nontitle_Ah_Yeah_15.csv 등장과 동시에 들러리들 바닥에서…… Nontitle   15             
     4 Nontitle_Ah_Yeah_15.csv 침 흘리며 기절 그 위에서 수영해요…… Nontitle   15             
     5 Nontitle_Ah_Yeah_15.csv WOAH 옆구리 지방튜브 끼고 못 뜬…… Nontitle   15             
     6 Nontitle_Ah_Yeah_15.csv 애들이 알리 있나           Nontitle   15             
     7 Nontitle_Ah_Yeah_15.csv 못 뜬 이유 절대 모름 (Don’t know)… Nontitle   15             
     8 Nontitle_Ah_Yeah_15.csv 맞출 생각 없어             Nontitle   15             
     9 Nontitle_Ah_Yeah_15.csv 니 식견에 날 맞추지 말길   Nontitle   15             
    10 Nontitle_Ah_Yeah_15.csv 막 귀들 방구석 박혀 밖에 나오질 않지…… Nontitle   15             
    # ℹ 1,572 more rows

## Cleaning up the Data

I used functions from tidy text to make it so that each word is its own
row.

``` r
lyrics |>
 unnest_tokens(word, "Lyrics") |> arrange(desc(album_year_20XX)) -> withlang
print(withlang)
```

    # A tibble: 6,707 × 4
       file                  track_type album_year_20XX word    
       <chr>                 <chr>      <chr>           <chr>   
     1 Nontitle_Candy_24.csv Nontitle   24              우리    
     2 Nontitle_Candy_24.csv Nontitle   24              사탕    
     3 Nontitle_Candy_24.csv Nontitle   24              같은    
     4 Nontitle_Candy_24.csv Nontitle   24              사랑해요
     5 Nontitle_Candy_24.csv Nontitle   24              자그만  
     6 Nontitle_Candy_24.csv Nontitle   24              말      
     7 Nontitle_Candy_24.csv Nontitle   24              하나에도
     8 Nontitle_Candy_24.csv Nontitle   24              기분이  
     9 Nontitle_Candy_24.csv Nontitle   24              좋아질  
    10 Nontitle_Candy_24.csv Nontitle   24              수      
    # ℹ 6,697 more rows

``` r
#creating vector with only the lyrics in single-word rows
select(withlang, "word") -> withlang
print(withlang)
```

    # A tibble: 6,707 × 1
       word    
       <chr>   
     1 우리    
     2 사탕    
     3 같은    
     4 사랑해요
     5 자그만  
     6 말      
     7 하나에도
     8 기분이  
     9 좋아질  
    10 수      
    # ℹ 6,697 more rows

``` r
#mutating withlang to detect language of rows of lyrics
withlang <- withlang %>%
  mutate(
    word   = as.character(word),
    korean  = str_detect(word, "[가-힣]"),
    english = str_detect(word, "[A-Za-z]")
  )

print(withlang)
```

    # A tibble: 6,707 × 3
       word     korean english
       <chr>    <lgl>  <lgl>  
     1 우리     TRUE   FALSE  
     2 사탕     TRUE   FALSE  
     3 같은     TRUE   FALSE  
     4 사랑해요 TRUE   FALSE  
     5 자그만   TRUE   FALSE  
     6 말       TRUE   FALSE  
     7 하나에도 TRUE   FALSE  
     8 기분이   TRUE   FALSE  
     9 좋아질   TRUE   FALSE  
    10 수       TRUE   FALSE  
    # ℹ 6,697 more rows

## Analyzing the Data

I will use language-detecting functions to label the individual words as
English, Korean, or Other.

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
     [1] tidytext_0.4.3  lubridate_1.9.4 forcats_1.0.0   stringr_1.5.1  
     [5] dplyr_1.1.4     purrr_1.1.0     readr_2.1.5     tidyr_1.3.1    
     [9] tibble_3.3.0    ggplot2_3.5.2   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] janeaustenr_1.0.0  utf8_1.2.6         generics_0.1.4     stringi_1.8.7     
     [5] lattice_0.22-7     hms_1.1.3          digest_0.6.37      magrittr_2.0.3    
     [9] evaluate_1.0.5     grid_4.5.1         timechange_0.3.0   RColorBrewer_1.1-3
    [13] fastmap_1.2.0      jsonlite_2.0.0     Matrix_1.7-3       scales_1.4.0      
    [17] cli_3.6.5          rlang_1.1.6        crayon_1.5.3       tokenizers_0.3.0  
    [21] bit64_4.6.0-1      withr_3.0.2        yaml_2.3.10        tools_4.5.1       
    [25] parallel_4.5.1     tzdb_0.5.0         vctrs_0.6.5        R6_2.6.1          
    [29] lifecycle_1.0.4    bit_4.6.0          vroom_1.6.5        pkgconfig_2.0.3   
    [33] pillar_1.11.0      gtable_0.3.6       glue_1.8.0         Rcpp_1.1.0        
    [37] xfun_0.52          tidyselect_1.2.1   rstudioapi_0.17.1  knitr_1.50        
    [41] farver_2.1.2       htmltools_0.5.8.1  SnowballC_0.7.1    rmarkdown_2.30    
    [45] compiler_4.5.1    
