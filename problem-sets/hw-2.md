hw_2
================
2023-02-14

## data

The first step in completing this problem set requires me to reformat
the provided data file, `hw02_ltdb_2010.dta`, into a csv that capable of
being read and mutated in RStudio.

To accomplish this, we’ll need to load a few packages.

``` r
library(haven)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.4 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(dplyr)
```

Now, we can load the data into our environment:

``` r
hw02_ltdb_2010 <- read_dta("~/Downloads/hw02_ltdb_2010.dta")
```

## q1

The first question requires us to select one of the 100 largest CBSAs
given in the dataset, which is provided by the cbsasamp1 variable.

I chose the Milwaukee-Waukesha-West Allis, WI CBSA. Based on this
decision, let’s go ahead and mutate the dataframe that all rows
containing data outside this CBSA are removed.

``` r
milwaukee_cbsa <- hw02_ltdb_2010 %>% filter(cbsaname == "Milwaukee-Waukesha-West Allis, WI CBSA")
```

Now, we have to generate three tables describing this CBSA: one to
summarize the population characteristics, one to summarize relevant
neighborhood attributes, and one to quantify the levels of neighborhood
segregation.

### Table 1

``` r
pop_characteristics <- read_csv("/Users/kenjinchang/github/pam6950/pop_characteristics.csv")
```

    ## Rows: 1 Columns: 17
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## dbl (17): num_persons, prop_asian, prop_black, prop_hisp, prop_white, num_as...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
