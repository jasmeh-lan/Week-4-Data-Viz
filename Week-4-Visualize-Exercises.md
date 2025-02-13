# Visualize Data
Jasmine Lantaca

## Your Turn 0

Add a setup chunk that loads the tidyverse packages.

``` r
mpg
```

    # A tibble: 234 × 11
       manufacturer model      displ  year   cyl trans drv     cty   hwy fl    class
       <chr>        <chr>      <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
     1 audi         a4           1.8  1999     4 auto… f        18    29 p     comp…
     2 audi         a4           1.8  1999     4 manu… f        21    29 p     comp…
     3 audi         a4           2    2008     4 manu… f        20    31 p     comp…
     4 audi         a4           2    2008     4 auto… f        21    30 p     comp…
     5 audi         a4           2.8  1999     6 auto… f        16    26 p     comp…
     6 audi         a4           2.8  1999     6 manu… f        18    26 p     comp…
     7 audi         a4           3.1  2008     6 auto… f        18    27 p     comp…
     8 audi         a4 quattro   1.8  1999     4 manu… 4        18    26 p     comp…
     9 audi         a4 quattro   1.8  1999     4 auto… 4        16    25 p     comp…
    10 audi         a4 quattro   2    2008     4 manu… 4        20    28 p     comp…
    # ℹ 224 more rows

``` r
head(mpg)
```

    # A tibble: 6 × 11
      manufacturer model displ  year   cyl trans      drv     cty   hwy fl    class 
      <chr>        <chr> <dbl> <int> <int> <chr>      <chr> <int> <int> <chr> <chr> 
    1 audi         a4      1.8  1999     4 auto(l5)   f        18    29 p     compa…
    2 audi         a4      1.8  1999     4 manual(m5) f        21    29 p     compa…
    3 audi         a4      2    2008     4 manual(m6) f        20    31 p     compa…
    4 audi         a4      2    2008     4 auto(av)   f        21    30 p     compa…
    5 audi         a4      2.8  1999     6 auto(l5)   f        16    26 p     compa…
    6 audi         a4      2.8  1999     6 manual(m5) f        18    26 p     compa…

## Your Turn 1

Run the code on the slide to make a graph. Pay strict attention to
spelling, capitalization, and parentheses!

``` r
ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ, y = hwy))
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/making%20graph-1.png)

## Your Turn 2

Replace this scatterplot with one that draws boxplots. Use the
cheatsheet. Try your best guess.

``` r
ggplot(data = mpg) +
  geom_boxplot(mapping = aes(x = class, y = hwy))
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/making%20a%20boxplot-1.png)

## Your Turn 3

Make a histogram of the `hwy` variable from `mpg`. Hint: do not supply a
y variable.

``` r
ggplot(data = mpg) +
  geom_histogram(mapping = aes(x = hwy))
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Week-4-Visualize-Exercises_files/figure-commonmark/making%20histogram-1.png)

## Your Turn 4

Use the help page for `geom_histogram` to make the bins 2 units wide.

``` r
ggplot(data = mpg) +
  geom_histogram(aes(x = hwy), 
                 binwidth = 2)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/binwidth%20added-1.png)

## Your Turn 5

Add `color`, `size`, `alpha`, and `shape` aesthetics to your graph.
Experiment.

``` r
ggplot(data = mpg) +
  geom_point(aes(x = displ, 
                 y = hwy,
                 color = class)) +
  labs(x = "Engine Size Displacement",
       y = "Highway Mileage (mpg)",
       color = "Class of Vehicle",
       title = "The Bigger the engine, the less mileage we get on the highway") +
  theme_light()
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/adding%20more%20aesthetics-1.png)

## Help Me

What do `facet_grid()` and `facet_wrap()` do? (run the code, interpret,
convince your group)

``` r
# Makes a plot that the commands below will modify
q <- ggplot(mpg) + geom_point(aes(x = displ, y = hwy))

q + facet_grid(. ~ cyl)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/facets-1.png)

``` r
# Creates four column through cyl with one row through a dot

q + facet_grid(drv ~ .)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/facets-2.png)

``` r
# Creates three rows through drv with one column through a dot

q + facet_grid(drv ~ cyl)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/facets-3.png)

``` r
# Creates three rows using drv combined with four columns with cy1

q + facet_wrap(~ class)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/facets-4.png)

``` r
# Makes a graph for each class
```

## Your Turn 6

Make a bar chart `class` colored by `class`. Use the help page for
`geom_bar` to choose a “color” aesthetic for class.

``` r
ggplot(mpg) + 
  geom_bar(aes(x = class,
               fill = class)) +
  guides(fill = "none") +
  labs(x = " Class of Vehicle",
       y = "Number of Vehicles in Sample") +
  theme_bw()
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/bargraph-1.png)

## Quiz

What will this code do?

``` r
ggplot(mpg, aes(x = displ, y = hwy)) + 
  geom_point(aes(color = class)) +
  geom_smooth(color = "#49b9de",
              se = FALSE,
              method = "lm") 
```

    `geom_smooth()` using formula = 'y ~ x'

![](Week-4-Visualize-Exercises_files/figure-commonmark/JPG%20of%20Graph-1.png)

``` r
# It will create a graph that is a scatter plot with a line, basically adding two geometries. 

  #ggsave("example.jpg", width = 6,height = 4)
# Saving an image in the folder. Basically, creates a image, especially a jpg image, of the given graph.
```

------------------------------------------------------------------------

# Take aways

You can use this code template to make thousands of graphs with
**ggplot2**.

``` r
ggplot(data = <DATA>) +
  <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))
```
