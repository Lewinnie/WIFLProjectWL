WIFLProject
================
05 May, 2017

<!-- README.md is generated from README.Rmd. Please edit that file -->
My goal for this project is to learn the functions of R and use it to manipulate and analyze the WIFL dataset.

``` r
library(readr)
WIFL_Metadata <- read_csv("~/Desktop/WIFLProject/WIFL_Metadata.csv")
#> Parsed with column specification:
#> cols(
#>   Field_Number = col_character(),
#>   `SNP Plate Number` = col_integer(),
#>   `SNP Well Position` = col_character(),
#>   Near_Town = col_character(),
#>   Extraction_Location = col_character(),
#>   Collector = col_character(),
#>   Country = col_character(),
#>   State = col_character(),
#>   Lat = col_double(),
#>   Long = col_double(),
#>   Group = col_character(),
#>   Stage = col_character(),
#>   `Stage (notes)` = col_character(),
#>   Year = col_integer(),
#>   Month = col_integer(),
#>   Day = col_integer(),
#>   `RAD?` = col_character()
#> )
panel1 <- read_delim("~/Desktop/WIFLProject/panel1.csv", 
    "\t", escape_double = FALSE, trim_ws = TRUE)
#> Warning: Duplicated column names deduplicated: 'ada_brew_1' =>
#> 'ada_brew_1_1' [3], 'ada_brew_17' => 'ada_brew_17_1' [5], 'ada_brew_4'
#> => 'ada_brew_4_1' [7], 'ada_ext_11' => 'ada_ext_11_1' [9], 'ada_ext_4'
#> => 'ada_ext_4_1' [11], 'ada_Kern_3' => 'ada_Kern_3_1' [13], 'Ada_NS_7'
#> => 'Ada_NS_7_1' [15], 'ada_tra_6' => 'ada_tra_6_1' [17], 'brew_ext_10' =>
#> 'brew_ext_10_1' [19], 'brew_ext_3' => 'brew_ext_3_1' [21], 'brew_Kern_3' =>
#> 'brew_Kern_3_1' [23], 'brew_NS_7' => 'brew_NS_7_1' [25], 'ada_brew_10' =>
#> 'ada_brew_10_1' [27], 'ada_brew_18' => 'ada_brew_18_1' [29], 'ada_brew_5'
#> => 'ada_brew_5_1' [31], 'ada_ext_12' => 'ada_ext_12_1' [33], 'ada_ext_5'
#> => 'ada_ext_5_1' [35], 'ada_Kern_4' => 'ada_Kern_4_1' [37], 'Ada_NS_8'
#> => 'Ada_NS_8_1' [39], 'ada_WM_1' => 'ada_WM_1_1' [41], 'brew_ext_11' =>
#> 'brew_ext_11_1' [43], 'brew_ext_4' => 'brew_ext_4_1' [45], 'brew_Kern_4' =>
#> 'brew_Kern_4_1' [47], 'brew_NS_8' => 'brew_NS_8_1' [49], 'ada_brew_11' =>
#> 'ada_brew_11_1' [51], 'ada_brew_19' => 'ada_brew_19_1' [53], 'ada_brew_6'
#> => 'ada_brew_6_1' [55], 'ada_ext_13' => 'ada_ext_13_1' [57], 'ada_ext_6'
#> => 'ada_ext_6_1' [59], 'Ada_NS_10' => 'Ada_NS_10_1' [61], 'Ada_NS_9'
#> => 'Ada_NS_9_1' [63], 'ada_WM_2' => 'ada_WM_2_1' [65], 'brew_ext_12' =>
#> 'brew_ext_12_1' [67], 'brew_ext_5' => 'brew_ext_5_1' [69], 'brew_NS_1' =>
#> 'brew_NS_1_1' [71], 'brew_NS_9' => 'brew_NS_9_1' [73], 'ada_brew_12' =>
#> 'ada_brew_12_1' [75], 'ada_brew_2' => 'ada_brew_2_1' [77], 'ada_brew_7'
#> => 'ada_brew_7_1' [79], 'ada_ext_15' => 'ada_ext_15_1' [81], 'ada_ext_7'
#> => 'ada_ext_7_1' [83], 'Ada_NS_2' => 'Ada_NS_2_1' [85], 'ada_tra_1' =>
#> 'ada_tra_1_1' [87], 'ada_WM_3' => 'ada_WM_3_1' [89], 'brew_ext_13' =>
#> 'brew_ext_13_1' [91], 'brew_ext_6' => 'brew_ext_6_1' [93], 'brew_NS_2' =>
#> 'brew_NS_2_1' [95], 'brew_tra_1' => 'brew_tra_1_1' [97], 'ada_brew_13' =>
#> 'ada_brew_13_1' [99], 'ada_brew_20' => 'ada_brew_20_1' [101], 'ada_brew_8'
#> => 'ada_brew_8_1' [103], 'ada_ext_16' => 'ada_ext_16_1' [105], 'ada_ext_8'
#> => 'ada_ext_8_1' [107], 'Ada_NS_3' => 'Ada_NS_3_1' [109], 'ada_tra_2' =>
#> 'ada_tra_2_1' [111], 'ada_WM_4' => 'ada_WM_4_1' [113], 'brew_ext_14' =>
#> 'brew_ext_14_1' [115], 'brew_ext_7' => 'brew_ext_7_1' [117], 'brew_NS_3'
#> => 'brew_NS_3_1' [119], 'brew_tra_10' => 'brew_tra_10_1' [121],
#> 'ada_brew_14' => 'ada_brew_14_1' [123], 'ada_brew_21' =>
#> 'ada_brew_21_1' [125], 'ada_brew_9' => 'ada_brew_9_1' [127], 'ada_ext_17'
#> => 'ada_ext_17_1' [129], 'ada_ext_9' => 'ada_ext_9_1' [131], 'Ada_NS_4'
#> => 'Ada_NS_4_1' [133], 'ada_tra_3' => 'ada_tra_3_1' [135], 'ada_WM_5' =>
#> 'ada_WM_5_1' [137], 'brew_ext_15' => 'brew_ext_15_1' [139], 'brew_ext_9'
#> => 'brew_ext_9_1' [141], 'brew_NS_4' => 'brew_NS_4_1' [143], 'brew_tra_11'
#> => 'brew_tra_11_1' [145], 'ada_brew_15' => 'ada_brew_15_1' [147],
#> 'ada_brew_22' => 'ada_brew_22_1' [149], 'ada_ext_1' => 'ada_ext_1_1' [151],
#> 'ada_ext_2' => 'ada_ext_2_1' [153], 'ada_Kern_1' => 'ada_Kern_1_1' [155],
#> 'Ada_NS_5' => 'Ada_NS_5_1' [157], 'ada_tra_4' => 'ada_tra_4_1' [159],
#> 'ada_WM_6' => 'ada_WM_6_1' [161], 'brew_ext_16' => 'brew_ext_16_1' [163],
#> 'brew_Kern_1' => 'brew_Kern_1_1' [165], 'brew_NS_5' => 'brew_NS_5_1' [167],
#> 'brew_tra_12' => 'brew_tra_12_1' [169], 'ada_brew_16' =>
#> 'ada_brew_16_1' [171], 'ada_brew_3' => 'ada_brew_3_1' [173], 'ada_ext_10'
#> => 'ada_ext_10_1' [175], 'ada_ext_3' => 'ada_ext_3_1' [177], 'ada_Kern_2'
#> => 'ada_Kern_2_1' [179], 'Ada_NS_6' => 'Ada_NS_6_1' [181], 'ada_tra_5' =>
#> 'ada_tra_5_1' [183], 'brew_ext_1' => 'brew_ext_1_1' [185], 'brew_ext_2' =>
#> 'brew_ext_2_1' [187], 'brew_Kern_2' => 'brew_Kern_2_1' [189], 'brew_NS_6'
#> => 'brew_NS_6_1' [191], 'brew_tra_13' => 'brew_tra_13_1' [193]
#> Parsed with column specification:
#> cols(
#>   .default = col_integer(),
#>   Field_Number = col_character()
#> )
#> See spec(...) for full column specifications.
library(tidyverse)
#> Loading tidyverse: ggplot2
#> Loading tidyverse: tibble
#> Loading tidyverse: tidyr
#> Loading tidyverse: purrr
#> Loading tidyverse: dplyr
#> Conflicts with tidy packages ----------------------------------------------
#> filter(): dplyr, stats
#> lag():    dplyr, stats
WIFLPanel1 <- WIFL_Metadata %>% left_join(panel1, by = "Field_Number")
library(readr)
panel2 <- read_delim("~/Desktop/WIFLProject/panel2.csv", 
    "\t", escape_double = FALSE, trim_ws = TRUE)
#> Warning: Duplicated column names deduplicated: 'brew_tra_14' =>
#> 'brew_tra_14_1' [3], 'brew_tra_7' => 'brew_tra_7_1' [5], 'climate_08'
#> => 'climate_08_1' [7], 'climate_16' => 'climate_16_1' [9], 'climate_24'
#> => 'climate_24_1' [11], 'ext_pure_Kern_8' => 'ext_pure_Kern_8_1' [13],
#> 'ext_tra_10' => 'ext_tra_10_1' [15], 'ext_tra_3' => 'ext_tra_3_1' [17],
#> 'Kern_SD_2' => 'Kern_SD_2_1' [19], 'tra_EW_4' => 'tra_EW_4_1' [21],
#> 'WM_ext_3' => 'WM_ext_3_1' [23], 'WM_Kern_5' => 'WM_Kern_5_1' [25],
#> 'brew_tra_15' => 'brew_tra_15_1' [27], 'brew_tra_8' => 'brew_tra_8_1' [29],
#> 'climate_09' => 'climate_09_1' [31], 'climate_17' => 'climate_17_1' [33],
#> 'ext_pure_Kern_1' => 'ext_pure_Kern_1_1' [35], 'ext_pure_Kern_9' =>
#> 'ext_pure_Kern_9_1' [37], 'ext_tra_11' => 'ext_tra_11_1' [39], 'ext_tra_4'
#> => 'ext_tra_4_1' [41], 'Kern_SD_3' => 'Kern_SD_3_1' [43], 'tra_EW_5'
#> => 'tra_EW_5_1' [45], 'WM_ext_4' => 'WM_ext_4_1' [47], 'WM_Kern_6' =>
#> 'WM_Kern_6_1' [49], 'brew_tra_16' => 'brew_tra_16_1' [51], 'brew_tra_9'
#> => 'brew_tra_9_1' [53], 'climate_10' => 'climate_10_1' [55], 'climate_18'
#> => 'climate_18_1' [57], 'ext_pure_Kern_2' => 'ext_pure_Kern_2_1' [59],
#> 'ext_pure_SD_1' => 'ext_pure_SD_1_1' [61], 'ext_tra_12' =>
#> 'ext_tra_12_1' [63], 'ext_tra_5' => 'ext_tra_5_1' [65], 'Kern_SD_4'
#> => 'Kern_SD_4_1' [67], 'tra_EW_6' => 'tra_EW_6_1' [69], 'WM_ext_5' =>
#> 'WM_ext_5_1' [71], 'WM_Kern_7' => 'WM_Kern_7_1' [73], 'brew_tra_2' =>
#> 'brew_tra_2_1' [75], 'climate_01' => 'climate_01_1' [77], 'climate_11' =>
#> 'climate_11_1' [79], 'climate_19' => 'climate_19_1' [81], 'ext_pure_Kern_3'
#> => 'ext_pure_Kern_3_1' [83], 'ext_pure_SD_2' => 'ext_pure_SD_2_1' [85],
#> 'ext_tra_13' => 'ext_tra_13_1' [87], 'ext_tra_6' => 'ext_tra_6_1' [89],
#> 'Kern_SD_5' => 'Kern_SD_5_1' [91], 'tra_EW_7' => 'tra_EW_7_1' [93],
#> 'WM_ext_6' => 'WM_ext_6_1' [95], 'WM_SD_1' => 'WM_SD_1_1' [97],
#> 'brew_tra_3' => 'brew_tra_3_1' [99], 'climate_02' => 'climate_02_1' [101],
#> 'climate_12' => 'climate_12_1' [103], 'climate_20' => 'climate_20_1' [105],
#> 'ext_pure_Kern_4' => 'ext_pure_Kern_4_1' [107], 'ext_pure_SD_3' =>
#> 'ext_pure_SD_3_1' [109], 'ext_tra_14' => 'ext_tra_14_1' [111], 'ext_tra_7'
#> => 'ext_tra_7_1' [113], 'Kern_SD_7' => 'Kern_SD_7_1' [115], 'tra_EW_8'
#> => 'tra_EW_8_1' [117], 'WM_Kern_1' => 'WM_Kern_1_1' [119], 'WM_SD_2' =>
#> 'WM_SD_2_1' [121], 'brew_tra_4' => 'brew_tra_4_1' [123], 'climate_03' =>
#> 'climate_03_1' [125], 'climate_13' => 'climate_13_1' [127], 'climate_21'
#> => 'climate_21_1' [129], 'ext_pure_Kern_5' => 'ext_pure_Kern_5_1' [131],
#> 'ext_pure_SD_4' => 'ext_pure_SD_4_1' [133], 'ext_tra_15' =>
#> 'ext_tra_15_1' [135], 'ext_tra_8' => 'ext_tra_8_1' [137], 'tra_EW_1'
#> => 'tra_EW_1_1' [139], 'tra_EW_9' => 'tra_EW_9_1' [141], 'WM_Kern_2'
#> => 'WM_Kern_2_1' [143], 'WM_SD_3' => 'WM_SD_3_1' [145], 'brew_tra_5' =>
#> 'brew_tra_5_1' [147], 'climate_04' => 'climate_04_1' [149], 'climate_14'
#> => 'climate_14_1' [151], 'climate_22' => 'climate_22_1' [153],
#> 'ext_pure_Kern_6' => 'ext_pure_Kern_6_1' [155], 'ext_pure_SD_5' =>
#> 'ext_pure_SD_5_1' [157], 'ext_tra_16' => 'ext_tra_16_1' [159], 'ext_tra_9'
#> => 'ext_tra_9_1' [161], 'tra_EW_2' => 'tra_EW_2_1' [163], 'WM_ext_1'
#> => 'WM_ext_1_1' [165], 'WM_Kern_3' => 'WM_Kern_3_1' [167], 'WM_SD_4' =>
#> 'WM_SD_4_1' [169], 'brew_tra_6' => 'brew_tra_6_1' [171], 'climate_06' =>
#> 'climate_06_1' [173], 'climate_15' => 'climate_15_1' [175], 'climate_23'
#> => 'climate_23_1' [177], 'ext_pure_Kern_7' => 'ext_pure_Kern_7_1' [179],
#> 'ext_tra_1' => 'ext_tra_1_1' [181], 'ext_tra_2' => 'ext_tra_2_1' [183],
#> 'Kern_SD_1' => 'Kern_SD_1_1' [185], 'tra_EW_3' => 'tra_EW_3_1' [187],
#> 'WM_ext_2' => 'WM_ext_2_1' [189], 'WM_Kern_4' => 'WM_Kern_4_1' [191],
#> 'WM_SD_5' => 'WM_SD_5_1' [193]
#> Parsed with column specification:
#> cols(
#>   .default = col_integer(),
#>   Field_Number = col_character()
#> )
#> See spec(...) for full column specifications.
WIFLPanel1_2 <- WIFLPanel1 %>% left_join(panel2, by = "Field_Number")
```
