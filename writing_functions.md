Writing Functions
================
Xiaoni Xu
2024-10-24

``` r
library(tidyverse)
library(rvest)
```

## writing the first function

as an example, htere’s a z-score computation

``` r
x_vec = rnorm(n = 25, mean = 10, sd = 3.5)

(x_vec - mean(x_vec)) / sd(x_vec)
```

    ##  [1] -1.13449162  2.04404997  1.31514326 -1.46300119 -0.41784482  1.07876725
    ##  [7] -0.13180439 -0.38889494 -1.88345595  0.46023804 -0.77220786 -0.11157608
    ## [13]  0.47765161  0.72424005 -0.02958699  1.14218082 -1.23324156 -1.38735469
    ## [19]  0.69886068 -1.25565848  0.47301283  0.08545869  0.64875225  0.58742345
    ## [25]  0.47333964

Now I’ll write a function to do this

``` r
z_scores = function(x) {
  
  if (!is.numeric(x)) {
    stop("x needs to be numeric")
  }
  
  if (length(x) <5 ) {
    stop("you need at least five numbers to compute z score")
  }
  
  z = (x - mean(x)) / sd(x)
  
  return(z)
}

z_scores(x = x_vec)
```

    ##  [1] -1.13449162  2.04404997  1.31514326 -1.46300119 -0.41784482  1.07876725
    ##  [7] -0.13180439 -0.38889494 -1.88345595  0.46023804 -0.77220786 -0.11157608
    ## [13]  0.47765161  0.72424005 -0.02958699  1.14218082 -1.23324156 -1.38735469
    ## [19]  0.69886068 -1.25565848  0.47301283  0.08545869  0.64875225  0.58742345
    ## [25]  0.47333964

Does this always work?

``` r
z_scores(x = 3)
```

    ## Error in z_scores(x = 3): you need at least five numbers to compute z score

``` r
z_scores(x = c("my", "name", "is", "xiaoni"))
```

    ## Error in z_scores(x = c("my", "name", "is", "xiaoni")): x needs to be numeric

``` r
z_scores(x = x_vec)
```

    ##  [1] -1.13449162  2.04404997  1.31514326 -1.46300119 -0.41784482  1.07876725
    ##  [7] -0.13180439 -0.38889494 -1.88345595  0.46023804 -0.77220786 -0.11157608
    ## [13]  0.47765161  0.72424005 -0.02958699  1.14218082 -1.23324156 -1.38735469
    ## [19]  0.69886068 -1.25565848  0.47301283  0.08545869  0.64875225  0.58742345
    ## [25]  0.47333964

## A new function

``` r
mean_and_sd = function(x) {
  
  mean_x = mean(x)
  
  sd_x = sd(x)
  
}
```
