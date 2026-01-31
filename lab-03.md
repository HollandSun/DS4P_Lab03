Lab 03 - Nobel laureates
================
Insert your name here
Insert date here

### Load packages and data

``` r
library(tidyverse) 
```

``` r
nobel <- read_csv("data/nobel.csv")
```

## Exercises 1

The dataset contains 935 observations and 26 variables. Each row
represents a single Nobel Prize award received in a given year and
category.

``` r
nobel_living <- nobel %>%
  filter(
    is.na(died_date),
    !is.na(country),
    gender != "org")
```

After applying these filters, the resulting dataset contains 228
observations.

### Exercise 2

``` r
nobel_living <- nobel_living %>%
  mutate(
    country_us = if_else(country == "USA", "USA", "Other")
  )
```

``` r
nobel_living_science <- nobel_living %>%
  filter(category %in% c("Physics", "Medicine", "Chemistry", "Economics"))
```

``` r
nobel_living_science %>%
  ggplot(aes(x = country_us, fill = country_us)) +
  geom_bar() +
  facet_wrap(~ category) +
  coord_flip() +
  labs(
    x = "Country",
    y = "Number of laureates",
    title = "Living Nobel laureates: USA vs. Other"
  ) + 
     scale_fill_manual(values = c("Other" = "#6baed6", "USA" = "#fc8d62")) + 
  theme_minimal()
```

![](lab-03_files/figure-gfm/plot-us-based-by-category-1.png)<!-- -->
Make it more colorful \### Exercise 3

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 4

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…
