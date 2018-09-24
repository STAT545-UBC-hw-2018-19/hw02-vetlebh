Gapminder dataset Exploration
================
Vetle Birkeland Huglen
24 9 2018

Smell test the data
-------------------

Firstly, we will look at the dataset as a whole, and try to figure out the format of the dataset.

``` r
typeof(gapminder)
```

    ## [1] "list"

``` r
class(gapminder)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
storage.mode(gapminder)
```

    ## [1] "list"

The `typeof()` and `storage.mode()` functions regard the **gapminder** dataset as lists, which can essentially be thought of as simply a collection of elements. The `class()` function reveals that the dataset is also a **data.frame**, which imposes further restrictions on the list, namely that two different variables can't have the same name, all elements are vectors, and all elements have equal length.

``` r
nrow(gapminder)
```

    ## [1] 1704

``` r
ncol(gapminder)
```

    ## [1] 6

``` r
dim(gapminder)
```

    ## [1] 1704    6

``` r
length(gapminder)
```

    ## [1] 6

Above are a few different ways to access the size of the dataframe; `ncols()` and `nrows()` returns the number of columns and rows, `dim()` returns the dimensions as a vector and `length()` also returns the length of the object (in this case the number of columns). One can imagine that one should be careful using `length()` on objects with more than one dimension, as it is not intuitive from the name of the function which dimension it returns. At the same time, it is very convenient to use it on 1d vectors, especially if it is not clear if the vector is transposed.

``` r
str(gapminder)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1704 obs. of  6 variables:
    ##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

The variables `country` and `continent` are factor-variables with a certain amount of levels (one factor per country/continent). `year` and `pop` are integers and `lifeExp` and `gdpPercap` are numeric values.

Explore individual variables
----------------------------
