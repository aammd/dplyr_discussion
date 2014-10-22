Using dplyr in ecology
========================================================
author: Andrew MacDonald
date: 2014-10-22

What is dplyr?
========================================================
Updated version of `plyr` that focusses on dataframes.

Fast, easy and readable way to manipulate your data.

based on the [Split-Apply-Combine](http://www.jstatsoft.org/v40/i01/paper) appproach to analysis.

Install dplyr
========================================================


```r
## install if you do not already have

## from CRAN:
## install.packages('dplyr')

## from GitHub using devtools (which you also might need to install!):
devtools::install_github("hadley/lazyeval")
devtools::install_github("hadley/dplyr")
```

Ceci c'est le pipe
========================================================
![pipe](pipe.jpeg)

`dplyr` imports the pipe from the [`magrittr`](https://github.com/smbache/magrittr) package

How to pipe
========================================================

The pipe operator is common in many programming languages.

It simply moves the left-hand side to the right-hand side.

This lets you do things one after another:


```r
library(magrittr)

mean(exp(seq(1, 20)))
```

```
[1] 38376002
```

```r
seq(1, 20) %>% exp %>% mean
```

```
[1] 38376002
```

The Five Verbs
========================================================

`dplyr` gives us five verbs that together express most of the things a scientist would do:

* `arrange`
* `select`
* `filter`
* `mutate`
* `summarize`

Examples
========================================================

```r
library(dplyr)
library(lubridate)
library(tidyr)

spp <- read.table("cardoso_2008_speciesname_clean.txt")
site <- read.table("cardoso_2008_sites.txt", header = TRUE, sep = "\t")
```

arrange
========================================================


```r
spp %>%
  arrange(name) %>%
  head
```

```
           name realm Brom.3 Brom.46 Brom.95 Brom.102 Brom.16 Brom.48
1 Coleoptera.34     a      4      22      37        0       0      55
2 Coleoptera.35     a      0       0       0       13      41       0
3    Diptera.10     a      0       0       0        0       0       0
4   Diptera.130     a      0       1       0        0       0       1
5   Diptera.131     a      0       0       1        0       0       0
6   Diptera.137     a     14       0       1        0       0       0
  Brom.85 Brom.64 Brom.82 Brom.77 Brom.7 Brom.1 Brom.4 Brom.53 Brom.40
1       7      90       0      13      4     63     69       9      39
2       0       2       0       0      0     17      6       0       0
3       0       0       0       0      0      0      0       0       0
4       0       0       0       0      0      1      0       1       1
5       0       0       0       0      0      0      0       0       0
6       0       0       0       0      0      0      0       0       0
  Brom.79 Brom.A Brom.B Brom.C Brom.D Brom.E Brom.F Brom.G Brom.H Brom.I
1      65     17      1      6      1      0      0      0      0      0
2       0      0      0      0      0      0      0      0      0      0
3       1      0      0      0      0      0      0      0      0      0
4       5      1      0      0      0      0      0      0      0      0
5       0      0      0      1      0      1      1      0      0      0
6       0      0      3      9      1      0      4      0      0      0
```

