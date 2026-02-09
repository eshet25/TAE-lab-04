Lab 04 - La Quinta is Spanish for next to Denny’s, Pt. 1
================
Tsion
02-08-2026

### Load packages and data

``` r
library(tidyverse) 
library(dsbox) 
```

\*Install dsbox first

``` r
#manually downloaded and opened the two datasets.
```

``` r
states <- read_csv("data/states.csv")
```

``` r
dn <- dennys
lq <- laquinta
```

### Exercise 1

``` r
nrow(dn)
```

    ## [1] 1643

``` r
ncol(dn)
```

    ## [1] 6

The Dennys dataset contains 1643 and 6 columns. The rows represent a
Denny’s restaurant the data contains. The variables are address, city,
state, zip (code), longitude, and latitude.

### Exercise 2

``` r
nrow(lq)
```

    ## [1] 909

``` r
ncol(lq)
```

    ## [1] 6

The Laquinta dataset contains 909 and 6 columns. The rows represent a
Laquinta hotel the data contains. The variables are address, city,
state, zip (code), longitude, and latitude (same as the dennys’
dataset).

### Exercise 3

…

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…

Add exercise headings as needed.
