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

Laquinta hotels have locations in the following places outisde of US:

North America: Canada, Mexico

Asia: China

Australia & the Pacific Rim: New Zealnd

Europe: Georgia, Turkiye

Middle East: UAE (Abu Dhabi, Dubai)

South America: Colomibia, Ecuador

For Denny’s, the link only shows the U.S locations. It lists “View U.S
Locations (1257)” in the website. But our dataset contains 1643
observations so I suspected there might be locations outisde the U.s
that we just can’t access through the website. I did a general search on
google, and wikipedia says, “It operates over 1,400 restaurants in the
United States, Canada, México, Puerto Rico, and several other
international locations.” (<https://en.wikipedia.org/wiki/Denny%27s>)

However, I wasn’t able to find a specific link that shows the different
Denny’s locations outside the U.S.

### Exercise 4

### Exercise 5

### Exercise 6

Add exercise headings as needed.
