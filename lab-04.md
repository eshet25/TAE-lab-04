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
observations so I suspected there might be locations outside the U.S
that we just can’t access through the website. But I am also not sure
why the numbers in our dataset are higher since it looks like it’s
listing the (US) states and zip codes there too.

I did a general google search, and wikipedia says, “It operates over
1,400 restaurants in the United States, Canada, México, Puerto Rico, and
several other international locations.”
(<https://en.wikipedia.org/wiki/Denny%27s>)

However, I wasn’t able to find a specific link that shows the different
Denny’s locations outside the U.S.

### Exercise 4

The first idea I had was to look at the latitude and longitude data and
filter out the places that would be outside of the U.S. But then, I took
a brief look at the dennys dataset, and it looks like most of the
abbreviations under the column “state” were US states. So, I thought
maybe looking at what distinct states are included in the data will let
me know whether we have stores outside the US (at least in the context
of our data).

So, I would use a function to list all the unique values that are
included in the “state” column of our data, and also maybe see the
counts of the distinct values as well. If the output shows all states
that are US states, I would think the data only contans US locations.

### Exercise 5

``` r
dn %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

``` r
#Filter for states that are not in states$abbreviation
```

As I suspected, there are no US locations for Denny’s in this dataset.

### Exercise 6

``` r
dn %>%
  mutate(country = "United States")
```

    ## # A tibble: 1,643 × 7
    ##    address                        city    state zip   longitude latitude country
    ##    <chr>                          <chr>   <chr> <chr>     <dbl>    <dbl> <chr>  
    ##  1 2900 Denali                    Anchor… AK    99503    -150.      61.2 United…
    ##  2 3850 Debarr Road               Anchor… AK    99508    -150.      61.2 United…
    ##  3 1929 Airport Way               Fairba… AK    99701    -148.      64.8 United…
    ##  4 230 Connector Dr               Auburn  AL    36849     -85.5     32.6 United…
    ##  5 224 Daniel Payne Drive N       Birmin… AL    35207     -86.8     33.6 United…
    ##  6 900 16th St S, Commons on Gree Birmin… AL    35294     -86.8     33.5 United…
    ##  7 5931 Alabama Highway, #157     Cullman AL    35056     -86.9     34.2 United…
    ##  8 2190 Ross Clark Circle         Dothan  AL    36301     -85.4     31.2 United…
    ##  9 900 Tyson Rd                   Hope H… AL    36043     -86.4     32.2 United…
    ## 10 4874 University Drive          Huntsv… AL    35816     -86.7     34.7 United…
    ## # ℹ 1,633 more rows

``` r
#Mutate for new variable and set all observations equal to "United States".
#We don’t need to tell R how many times to repeat the character string “United States” to fill in the data for all observations, R takes care of that automatically.
```

``` r
dn <- dn %>%
  mutate(country = "United States")
```

### Exercise 7

``` r
lq %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 14 × 6
    ##    address                                  city  state zip   longitude latitude
    ##    <chr>                                    <chr> <chr> <chr>     <dbl>    <dbl>
    ##  1 Carretera Panamericana Sur KM 12         "\nA… AG    20345    -102.     21.8 
    ##  2 Av. Tulum Mza. 14 S.M. 4 Lote 2          "\nC… QR    77500     -86.8    21.2 
    ##  3 Ejercito Nacional 8211                   "Col… CH    32528    -106.     31.7 
    ##  4 Blvd. Aeropuerto 4001                    "Par… NL    66600    -100.     25.8 
    ##  5 Carrera 38 # 26-13 Avenida las Palmas c… "\nM… ANT   0500…     -75.6     6.22
    ##  6 AV. PINO SUAREZ No. 1001                 "Col… NL    64000    -100.     25.7 
    ##  7 Av. Fidel Velazquez #3000 Col. Central   "\nM… NL    64190    -100.     25.7 
    ##  8 63 King Street East                      "\nO… ON    L1H1…     -78.9    43.9 
    ##  9 Calle Las Torres-1 Colonia Reforma       "\nP… VE    93210     -97.4    20.6 
    ## 10 Blvd. Audi N. 3 Ciudad Modelo            "\nS… PU    75010     -97.8    19.2 
    ## 11 Ave. Zeta del Cochero No 407             "Col… PU    72810     -98.2    19.0 
    ## 12 Av. Benito Juarez 1230 B (Carretera 57)… "\nS… SL    78399    -101.     22.1 
    ## 13 Blvd. Fuerza Armadas                     "con… FM    11101     -87.2    14.1 
    ## 14 8640 Alexandra Rd                        "\nR… BC    V6X1…    -123.     49.2

There are 14 locations of Laquinta outside of the US in this dataset.
After searching up the abbreviations,here are the locations:

Mexico: AG (Aguascalientes), QR (Quintana Roo), CH (Chihuahua), NL
(Nuevo León), VE (Veracruz), PU (Puebla) & SL (San Luis Potosí).

Colombia: ANT (Antioquia)

Canada: ON (Ontario), BC (British Columbia).

Honduras: FM (Francisco Morazán).

### Exercise 8

``` r
lq <- lq %>%
  mutate(country = case_when(
    state %in% state.abb ~ "United States",
    state %in% c("ON", "BC") ~ "Canada",
    state == "ANT" ~ "Colombia",
    state == "FM" ~ "Honduras",
    state %in% c("AG", "QR", "CH", "NL", "VE", "PU", "SL") ~ "Mexico"
  ))
```

``` r
lq <- lq %>%
  filter(country == "United States")
```

The lq dataset now has 895 rows after filtering only US locations.
