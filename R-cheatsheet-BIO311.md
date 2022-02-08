R cheatsheet
================
Created by: Emily Harders and Andrew Kraemer
Last edited: 8 February 2022

# READING IN DATA

### read.csv()

The `read.csv` function takes a csv file from your computer and uploads
it into R

``` r
bumpusdata<-read.csv("BIO311_data_bumpus.csv")
```

### rm(list=ls())

`rm(list=ls())` clears R’s memory, clearing anything you have named, or
any other code you have run.

### getwd()

The `getwd()` function will tell you what working directory is running
in R. Great for trouble-shooting

### setwd()

On a Mac, I prefer to use command+D to set the working directory, but
this code works if your computer is being stubborn or you need to change
your working directory for a specific section

``` r
setwd("~/Desktop/Biostats/Files")
```

# MATRIX MANIPULATION

### matrix(c( )nrow= )

The `matrix(c( ), nrow= )` function is used to create a matrix within
the c() function list the numbers down the columns of the matrix

``` r
a<-matrix(c(1,2,3,4,5,6,7,8,9,10,11,12,13,14), nrow=2)
a
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6] [,7]
    ## [1,]    1    3    5    7    9   11   13
    ## [2,]    2    4    6    8   10   12   14

### t()

The `t()` function transposes the matrix, so column 1 -> row 1, column 2
-> row 2, column 3 -> row 3, etc. in the transposed matrix.

Before transpose

``` r
b<-matrix(c(2,4,6,8,10,12,14,16,18,20,22,24,26,28), nrow=2)
b
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6] [,7]
    ## [1,]    2    6   10   14   18   22   26
    ## [2,]    4    8   12   16   20   24   28

After transpose

``` r
tb<-t(b) 
tb
```

    ##      [,1] [,2]
    ## [1,]    2    4
    ## [2,]    6    8
    ## [3,]   10   12
    ## [4,]   14   16
    ## [5,]   18   20
    ## [6,]   22   24
    ## [7,]   26   28

### cbind()

The function `cbind()` allows you to add two matrices together by the
columns (pushing matrices together side-by-side)

``` r
cbind(a,b)
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12] [,13] [,14]
    ## [1,]    1    3    5    7    9   11   13    2    6    10    14    18    22    26
    ## [2,]    2    4    6    8   10   12   14    4    8    12    16    20    24    28

### rbind()

The function `rbind()` allows you to add two matrices together by the
rows. (stacking matrices on top of each other)

``` r
rbind(a,b)
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6] [,7]
    ## [1,]    1    3    5    7    9   11   13
    ## [2,]    2    4    6    8   10   12   14
    ## [3,]    2    6   10   14   18   22   26
    ## [4,]    4    8   12   16   20   24   28

### is.matrix

`is.matrix` function “asks” R if it is understanding an object/list as a
matrix.

-   An output of TRUE means that the object is being read as a matrix
-   An output of FALSE means that the object is being NOT read as a
    matrix

``` r
is.matrix(a)
```

    ## [1] TRUE

### as.matrix

`as.matrix` function “commands” R to understanding an object/list as a
matrix, even if it is not supposed to be a matrix.

Originally, “not_M” is not being read as a matrix

``` r
not_M<-c(1,2,3,4,5,6,7,8,9,1,0,11,12)
is.matrix(not_M)
```

    ## [1] FALSE

…but after using as.matrix, not_M is being read as a matrix.

``` r
new_not_M<-as.matrix(not_M)
is.matrix(new_not_M)
```

    ## [1] TRUE

### %\*%

The `%*%` function multiplies two matrices together

``` r
a%*%tb
```

    ##      [,1] [,2]
    ## [1,]  910 1008
    ## [2,] 1008 1120

# MANIPULATING DATA

### $

The `$` isn’t a function, but it is very useful because it allows you to
isolate a column from a matrix.

``` r
bumpusdata$sex
```

    ##   [1] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##   [9] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [17] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [25] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [33] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [41] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [49] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [57] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [65] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [73] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "male"  
    ##  [81] "male"   "male"   "male"   "male"   "male"   "male"   "male"   "female"
    ##  [89] "female" "female" "female" "female" "female" "female" "female" "female"
    ##  [97] "female" "female" "female" "female" "female" "female" "female" "female"
    ## [105] "female" "female" "female" "female" "female" "female" "female" "female"
    ## [113] "female" "female" "female" "female" "female" "female" "female" "female"
    ## [121] "female" "female" "female" "female" "female" "female" "female" "female"
    ## [129] "female" "female" "female" "female" "female" "female" "female" "female"

``` r
bumpusdata$wgt
```

    ##   [1] 24.5 26.9 26.9 24.3 24.1 26.5 24.6 24.2 23.6 26.2 26.2 24.8 25.4 23.7 25.7
    ##  [16] 25.7 26.5 26.7 23.9 24.7 28.0 27.9 25.9 25.7 26.6 23.2 25.7 26.3 24.3 26.7
    ##  [31] 24.9 23.8 25.6 27.0 24.7 26.5 26.1 25.6 25.9 25.5 27.6 25.8 24.9 26.0 26.5
    ##  [46] 26.0 27.1 25.1 26.0 25.6 25.0 24.6 25.0 26.0 28.3 24.6 27.5 31.0 28.3 24.6
    ##  [61] 25.5 24.8 26.3 24.4 23.3 26.7 26.4 26.9 24.3 27.0 26.8 24.9 26.1 26.6 23.3
    ##  [76] 24.2 26.8 23.5 26.9 28.6 24.7 27.3 25.7 29.0 25.0 27.5 26.0 25.3 22.6 25.1
    ##  [91] 23.2 24.4 25.1 24.6 24.0 24.2 24.9 24.1 24.0 26.0 24.9 25.5 23.4 25.9 24.2
    ## [106] 24.2 27.4 24.0 26.3 25.8 26.0 23.2 26.5 24.2 26.9 27.7 23.9 26.1 24.6 23.6
    ## [121] 26.0 25.0 24.8 22.8 24.8 24.6 30.5 24.8 23.9 24.7 26.9 22.6 26.1 24.8 26.2
    ## [136] 26.1

### subset()

The `subset()` function allows you to create a more specific matrix from
a larger one, based on one variable. For example, the “males” subset
below, sifts through “bumpusdata” and picks out all the individuals
whose sex is male.

``` r
males<-subset(bumpusdata, bumpusdata$sex=="male")
```

### head()

The `head()` function lets you see the title of each column and the
first 6 rows of the datasheet

``` r
head(males)
```

    ##    sex  surv totlen wingext  wgt head humer femur tibio skull stern ln.totlen.
    ## 1 male alive    154     241 24.5 31.2 0.687 0.668 1.022 0.587 0.830   5.036953
    ## 2 male alive    160     252 26.9 30.8 0.736 0.709 1.180 0.602 0.841   5.075174
    ## 3 male alive    155     243 26.9 30.6 0.733 0.704 1.151 0.602 0.846   5.043425
    ## 4 male alive    154     245 24.3 31.7 0.741 0.688 1.146 0.584 0.839   5.036953
    ## 5 male alive    156     247 24.1 31.5 0.715 0.706 1.129 0.575 0.821   5.049856
    ## 6 male alive    161     253 26.5 31.8 0.780 0.743 1.144 0.607 0.893   5.081404
    ##   ln.wingext.  ln.wgt. ln.head.  ln.humer.  ln.femur.  ln.tibio.  ln.skull.
    ## 1    5.484797 1.066224 3.440418 -0.3754210 -0.4034671 0.02176149 -0.5327305
    ## 2    5.529429 1.097375 3.427515 -0.3065252 -0.3438998 0.16551444 -0.5074978
    ## 3    5.493061 1.097375 3.421000 -0.3106096 -0.3509769 0.14063113 -0.5074978
    ## 4    5.501258 1.063492 3.456317 -0.2997547 -0.3739664 0.13627762 -0.5378543
    ## 5    5.509388 1.060737 3.449988 -0.3354727 -0.3481400 0.12133229 -0.5533852
    ## 6    5.533389 1.092382 3.459466 -0.2484614 -0.2970592 0.13453089 -0.4992265
    ##    ln.stern.
    ## 1 -0.1863296
    ## 2 -0.1731636
    ## 3 -0.1672359
    ## 4 -0.1755446
    ## 5 -0.1972322
    ## 6 -0.1131687

### length()

The `length()` function finds the length of a vector. Uou have to
specify a column, because if you include an entire matrix (with rows
**and** columns) within the argument R will only count the number of
columns.

-   You have to pair males, with survival (or any other column in
    bumpusdata), otherwise R will count horizontally (the number of
    coumns), instead of counting the number of rows.
    -   There are 87 males

``` r
length(males$surv)
```

    ## [1] 87

### summary()

The `summary()`function allows you to view descritive statistics from
your dataset.

``` r
summary(males$wgt)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    23.2    24.7    25.8    25.8    26.7    31.0

### c()

The `c()` function allows you to link together a string of individual
(numbers, colors, labels, etc.) to create a vector

-   When creating a vector with words, you need to put each word into
    quotations.

``` r
age<-c(11,14,12,9,11,16,8,10,13,6,5)
names<-c("Sally","Mark","Jeff", "Bill", "Sarah", "Sam", "Karen", "Krista", "Amy", "Mathew", "Caroline")
```

``` r
age
```

    ##  [1] 11 14 12  9 11 16  8 10 13  6  5

``` r
names
```

    ##  [1] "Sally"    "Mark"     "Jeff"     "Bill"     "Sarah"    "Sam"     
    ##  [7] "Karen"    "Krista"   "Amy"      "Mathew"   "Caroline"

### paste()

The `paste()` function takes two identifying factors of an individual,
and combines them together into one identifying factor.

``` r
class<-paste(age,names)
class
```

    ##  [1] "11 Sally"   "14 Mark"    "12 Jeff"    "9 Bill"     "11 Sarah"  
    ##  [6] "16 Sam"     "8 Karen"    "10 Krista"  "13 Amy"     "6 Mathew"  
    ## [11] "5 Caroline"

### rep()

The `rep()` function repeats a specific number or word as a vector a
specific number of times.

-   This function repeats the word “RED”, “BLUE”, and “YELLOW” 25 times
    each.

``` r
c(rep("RED",25), rep("BLUE",25), rep("YELLOW", 25))
```

    ##  [1] "RED"    "RED"    "RED"    "RED"    "RED"    "RED"    "RED"    "RED"   
    ##  [9] "RED"    "RED"    "RED"    "RED"    "RED"    "RED"    "RED"    "RED"   
    ## [17] "RED"    "RED"    "RED"    "RED"    "RED"    "RED"    "RED"    "RED"   
    ## [25] "RED"    "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"  
    ## [33] "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"  
    ## [41] "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"   "BLUE"  
    ## [49] "BLUE"   "BLUE"   "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW"
    ## [57] "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW"
    ## [65] "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW" "YELLOW"
    ## [73] "YELLOW" "YELLOW" "YELLOW"

### which()

The `which()` function will tell you the position of numbers in a vector
that satisfy a certain condition

-   Say we have 9 children in a single file line. The first child is 12
    years old, the second is 11 years old, etc. Each child has a
    specific spot in relation to the other children. Using the which()
    function I can find the position of children over the age of 10.
    There are 6 children that are over the age of 10

`which(vector,condition,value)`

``` r
children<-c(12,11,13,18,9,11,7,5,15)
which(children>=10)
```

    ## [1] 1 2 3 4 6 9

By combining the which() and length() functions I can find the total
number of children that are over (or under using \<=) the age of 10.

``` r
length(which(children>=10))
```

    ## [1] 6

### set.seed() and rnorm()

`set.seed` is R’s random number generator, this is useful for creating
simulations or random objects that can be **reproduced** `rnorm()`
generates a vector of normally distributed random numbers.

-   by combining set.seed() and rnorm(), you can create unique set of
    normally distrubued numbers.
    -   The semicolon allows you to perform two “lines of code” on a
        single line. It is important not to overuse this function, it is
        much easier to stay organized in R when using seperate lines for
        seperate functions.

Below is simulated data showing the ages of residents in two retirement
homes

``` r
set.seed(12345); retire1_data<-rnorm(n=1000,mean=90, sd=3.3)
set.seed(54321); retire2_data<-rnorm(n=1000,mean=86, sd=5.1)
```

### tapply()

Using the `tapply()` function requires continuous data,the categories
and the calculation you want to do. tapply(continuous, categories,
function)

Using the simulated data for ages of residents in two retirement homes,
we can find the mean of the two goups using the tapply function

-   It is important to notice how retirement_ages and groups are the
    same length (meaning they both have 1000 individuals)

``` r
retirement_ages<-c(retire1_data, retire2_data)
groups<-c(rep("retire1",1000), rep("retire2",1000))
tapply(retirement_ages, groups, mean)
```

    ##  retire1  retire2 
    ## 90.15245 85.69500

### sample()

the `sample()` function can take a sample from a data set. In this case
we have a bowl with 15 red marbles and 20 blue marbles

sample(dataset, number of individuals in each sample)

``` r
bowl<-c(rep("RED", 15), rep("BLUE", 20))
sample(bowl, 5)
```

    ## [1] "BLUE" "BLUE" "BLUE" "RED"  "BLUE"

### loops

Here is the general “formula” for loops

**output\<-NULL**  
**n\<- #number of times the loop runs**  
**for(i in 1:n){**  
**#tasks…enter code you want to run repeatedly**  
**output\<-c(output, task result) #this line puts the outputs in a
list**  
**}**

For example, say I have a bowl of 500 seeds with an average mass of 50
mg. What is the probability that if I sample 2 seeds from the bowl, the
average will be greater than 50?

``` r
set.seed(2); seeds<-rnorm(n=500,mean=50,sd=10)
safe<-NULL
n<-100
for(i in 1:n){
  two_seeds<-sample(seeds, 2)
  avg.seed.wgt<-mean(two_seeds)
  safe<-c(safe, avg.seed.wgt)
}

safe
```

    ##   [1] 43.97922 36.90870 44.93668 49.91626 40.96983 55.82035 46.43654 37.94947
    ##   [9] 49.47774 50.22644 47.03734 48.81078 48.14952 47.59182 40.70522 42.03103
    ##  [17] 45.76630 55.70223 45.88820 53.69483 54.12571 57.03809 51.07268 58.68751
    ##  [25] 39.83478 46.19148 51.83130 63.84573 55.51624 49.52302 51.41520 47.70737
    ##  [33] 52.27610 51.52731 43.00705 52.95428 44.34729 40.20665 49.02499 41.93531
    ##  [41] 45.59049 52.39999 43.79383 48.61107 47.78200 50.12925 56.58457 48.65879
    ##  [49] 44.79310 37.00825 49.11025 49.44308 48.82775 56.64500 48.51056 56.35618
    ##  [57] 58.19276 47.47752 44.43717 46.01646 49.68217 45.69071 51.60491 57.60865
    ##  [65] 53.81550 60.15821 52.07288 51.56725 36.49347 60.44048 54.43019 49.77132
    ##  [73] 51.94806 62.16748 46.79578 58.81680 42.65649 54.80501 48.81661 49.65638
    ##  [81] 49.53910 53.70813 55.22174 57.37680 58.64993 37.35117 53.26432 47.25255
    ##  [89] 51.53240 58.14221 45.38624 39.30462 49.33671 53.51132 58.88295 58.40648
    ##  [97] 51.88707 42.09528 44.99873 54.44381

``` r
#Outside the loop, you can figure out the probability of pair of seeds being over 50 milligrams

sum(safe>=50)/n
```

    ## [1] 0.45

From our answer we can see that 53% of the seeds sampled had a mean
greater than the population mean

### table()

The `table()` function builds a contingency table of the counts for each
combination of categorical factors

``` r
bumpustable<-table(bumpusdata$sex, bumpusdata$surv)
bumpustable
```

    ##         
    ##          alive dead
    ##   female    21   28
    ##   male      51   36

# TESTING ASSUMPTIONS

## Normality

### qqnorm()

The `qqrnorm()` is a normality visualization that creates a scatter plot
of your data vector against expected values of data if they were
*normally distributed* about the mean. If the data is normally
distributed, the data will be in a straight linear line.

For example, the male bird weight from the bumpus data. (the “males”
subset was made previously)

``` r
qqnorm(males$wgt)
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-31-1.png)<!-- -->

### shapiro.test()

The Shapiro-Wilk tests if a data vector is normally distributed. If the
test is significant, then the data do NOT come from a normally
distributed population. Remember this by thinking that the data is
“significantly different from a normal population”

For example, the male bird weight from the bumpus data.

``` r
shapiro.test(males$wgt)
```

    ## 
    ##  Shapiro-Wilk normality test
    ## 
    ## data:  males$wgt
    ## W = 0.97221, p-value = 0.05782

The male bird weights from the bumpus data is NOT normally distribued
because we got a significant shapiro-wilk test.

## Equal variance

### var.test()

When the data are normal, the F-test compares the variances of 2 groups.
If the test is significant, the variances of the two groups are NOT
equal. Remember this by thinking that the data is “significantly
different from having equal variance.” The F-test can only compare two
groups.

For example, the male and female bird weight from the bumpus data.

``` r
var.test(males$wgt,females$wgt)
```

    ## 
    ##  F test to compare two variances
    ## 
    ## data:  males$wgt and females$wgt
    ## F = 0.95272, num df = 86, denom df = 48, p-value = 0.8306
    ## alternative hypothesis: true ratio of variances is not equal to 1
    ## 95 percent confidence interval:
    ##  0.5649791 1.5491011
    ## sample estimates:
    ## ratio of variances 
    ##           0.952718

The test is NOT signfificant, so the two data sets have equal variance.

### leveneTest()

When the data are NOT normal, the levene test compares the variances
between 2+ groups. If the test is significant, the variances of the
groups are NOT equal

To use the levene test, you have to first, download the package “car”.

``` r
# install.packages('car')
library(car)
```

For example, the male weight (y) and male survival (x) from the bumpus
data.

``` r
leveneTest(males$wgt~males$surv)
```

    ## Warning in leveneTest.default(y = y, group = group, ...): group coerced to
    ## factor.

    ## Levene's Test for Homogeneity of Variance (center = median)
    ##       Df F value Pr(>F)
    ## group  1  0.0591 0.8085
    ##       85

The result from the levene test is not significant so the groups (male
alive and male dead) have equal variances.

# INFERENTIAL STATISTICS

### dbinom()

`dbinom(x, size, prob)` **x= a vector of numbers, size=number of trials,
prob= probability of success for each trial**  
Using a bionomial probability distribution, you can use the dbinom()
function to calculate the probability of exactly one outcome under that
null distribution.

-   Returning to our simulated retirement home data, I want to know if I
    knock on 20 doors in the retirement home, what are the chances that
    exactly 5 95-year-olds will answer their door (The probability of
    success i.e. finding a 95-year-old is 0.055)?

``` r
dbinom(5,20, 0.055)
```

    ## [1] 0.003339907

NOTE: this is NOT a p=value, but a probability of a very specific
outcome (finding exactly 20 95-year-olds out of the 1000 residents)

### binom.test()

`binom.test(number of sucesses, number of trials)`  
p=expected/hypothesized probability of success, alternative=“two.sided”
“greater” or “less”)\*\*

You can use binom.test() function to calculate the probability of
success under a binomial probability distribution. Where dbinom() only
calculates the probability of one specific outcome/sucess, binom.test()
calculates a range of outcomes that are all considered a success.

-   Again returning to the retirement home data, if I knock on 20 doors
    in the retirement home, what are the chances that I will find five
    people who are 95-years-old OR OLDER will answer their door (The
    probability of success i.e. finding a 95-year-old is 0.061)?

``` r
binom.test(5, 20, p=0.061, alternative="greater")
```

    ## 
    ## 
    ## 
    ## data:  5 out of 20
    ## number of successes = 5, number of trials = 20, p-value = 0.006041
    ## alternative hypothesis: true probability of success is greater than 0.061
    ## 95 percent confidence interval:
    ##  0.1040808 1.0000000
    ## sample estimates:
    ## probability of success 
    ##                   0.25

### chisq.test()

`chisq.test(x, p=)` is a chi-squared goodness-of-fit test (where x is
data and p is null probability)

-   An example of this the different amounts of each color of skittle in
    the bag. (blue=103, red=61, green=55, orange=64, yellow=77)

``` r
chisq.test(c(103,61,55,64,77), p=c(0.2,0.2,0.2,0.2,0.2))
```

    ## 
    ##  Chi-squared test for given probabilities
    ## 
    ## data:  c(103, 61, 55, 64, 77)
    ## X-squared = 20.278, df = 4, p-value = 0.0004401

chisq.test(x) is a chi-squared test-of-association (where x is the data)

-   Looking back to the bumpus data, did sex of the bird influence if it
    lived or died? We can answer this using a chi-squared
    test-of-association. (The expected probability is derived from the
    observed data, so thats why its not in the function)

``` r
bumpustable<-table(bumpusdata$sex, bumpusdata$surv)
chisq.test(bumpustable)
```

    ## 
    ##  Pearson's Chi-squared test with Yates' continuity correction
    ## 
    ## data:  bumpustable
    ## X-squared = 2.5257, df = 1, p-value = 0.112

###g.test() Similar to a chi-squared test, but… useful for complicated
experimental design ex: null hypothesis is a particular association Does
not function well with small sample sizes Use the same degrees of
freedom as with chi-squared *You can set your expected frequencies in a
way you can’t with chi-squared G=2(Obs*ln(O-E))

### t.test()

Unsurprisingly, the function, t.test is used to perform a t-test on a
dataset. A t-test can determine if there is a significant difference
between the means of two goups (with continuous data).

There are 3 different types of t-tests:

***One-sample t-test** Also called the “Goodness of Fit t-test.” How the
population mean compares to some hypothesized value. Example: Imagine we
want to compare this years flow of the Nile river compared to the
average flow over the last 20 years (800.53)  
* (The dataset Nile is pre-loaded into R)

    ```r
    Nile_past<-800.53
    t.test(Nile, mu=800.53)
    ```

    ```
    ## 
    ##  One Sample t-test
    ## 
    ## data:  Nile
    ## t = 7.0213, df = 99, p-value = 2.796e-10
    ## alternative hypothesis: true mean is not equal to 800.53
    ## 95 percent confidence interval:
    ##  885.7716 952.9284
    ## sample estimates:
    ## mean of x 
    ##    919.35
    ```

Based on this one-sample t.test, there is a significant difference
between the mean flow of the Nile river this year, to the mean over the
last 20 years.

**Two-sample t-test** How the means of two groups are different. For
example, if we want to see if there is a significant difference in the
weight’s of crickets after feeding them either food-x or food-y

-   (The dataset randu is pre-loaded into R)

``` r
t.test(randu$x,randu$y)
```

    ## 
    ##  Welch Two Sample t-test
    ## 
    ## data:  randu$x and randu$y
    ## t = 1.9731, df = 797.28, p-value = 0.04883
    ## alternative hypothesis: true difference in means is not equal to 0
    ## 95 percent confidence interval:
    ##  0.0002075138 0.0805449562
    ## sample estimates:
    ## mean of x mean of y 
    ## 0.5264293 0.4860531

Based on this two-sample t.test, there is a significant difference
between the weights of the crickets under the two different food groups.

**Paired t-test** Determines whether the mean of two different groups is
0 (null hypothesis) or not (alternative). For example, the number of
pimples before and after a cream is applied from a dermatologiest.

``` r
set.seed(4); before_cream<-rnorm(10, mean=10, sd=6 )
set.seed(4); after_cream<-rnorm(10, mean=9, sd=7)
t.test(before_cream, after_cream, paired=TRUE)
```

    ## 
    ##  Paired t-test
    ## 
    ## data:  before_cream and after_cream
    ## t = 1.3088, df = 9, p-value = 0.223
    ## alternative hypothesis: true difference in means is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.3157605  1.1827019
    ## sample estimates:
    ## mean of the differences 
    ##               0.4334707

Based on this paired t.test, there is NO significant difference between
the number of pimples before and after the cream. Maybe time to find a
new dermatologist…

### summary(aov())

The `summary(aov())` function above us used to conduct and ANOVA
(Analysis of Variance) which is a test that uses the difference in
variation to see if the mean between groups are different

-   Unlike the two-sample t.test, you can have more than two groups

-   For example, determing if plants have different CO2 intake based on
    their type (Quebec or Mississippi) AND treatment (chilled or
    nonchilled)

-   **IMPORTANT- ANOVA’s do NOT tell you WHICH of the groups are
    different, only that a difference exists between at least two of the
    groups.**

    -   CO2 is a preloaded dataset in R

``` r
PLANT<-paste(CO2$Type, CO2$Treatment)
summary(aov(CO2$uptake~PLANT))
```

    ##             Df Sum Sq Mean Sq F value   Pr(>F)    
    ## PLANT        3   4579  1526.5   23.82 4.11e-11 ***
    ## Residuals   80   5128    64.1                     
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

### TukeyHSD(aov())

A **Tukey test** must be used to identify the groups that have a
significant difference. The output is a list of p-values of the
differences between each of the pairings.

``` r
TukeyHSD(aov(CO2$uptake~PLANT))
```

    ##   Tukey multiple comparisons of means
    ##     95% family-wise confidence level
    ## 
    ## Fit: aov(formula = CO2$uptake ~ PLANT)
    ## 
    ## $PLANT
    ##                                                 diff        lwr      upr
    ## Mississippi nonchilled-Mississippi chilled 10.138095  3.6553560 16.62083
    ## Quebec chilled-Mississippi chilled         15.938095  9.4553560 22.42083
    ## Quebec nonchilled-Mississippi chilled      19.519048 13.0363083 26.00179
    ## Quebec chilled-Mississippi nonchilled       5.800000 -0.6827393 12.28274
    ## Quebec nonchilled-Mississippi nonchilled    9.380952  2.8982131 15.86369
    ## Quebec nonchilled-Quebec chilled            3.580952 -2.9017869 10.06369
    ##                                                p adj
    ## Mississippi nonchilled-Mississippi chilled 0.0005553
    ## Quebec chilled-Mississippi chilled         0.0000000
    ## Quebec nonchilled-Mississippi chilled      0.0000000
    ## Quebec chilled-Mississippi nonchilled      0.0959830
    ## Quebec nonchilled-Mississippi nonchilled   0.0015893
    ## Quebec nonchilled-Quebec chilled           0.4727714

Focusing on the P values in the reults you can see there is a
significant differene between all of the groups except between Quebec
nonchilled-Quebec chilled (p=0.4727)

# PLOTTING DATA

### hist()

The `hist()` function creates a histogram of the weight of male birds.

``` r
hist(males$wgt)
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-45-1.png)<!-- -->

### boxplot()

Creates a boxplot of bird weight and “male alive” “male dead” “female
alive” “female dead”

-   The generic formula for a boxplot is `boxplot(y~x)`
    -   y= continuous
    -   x= categorical

Notice the paste function!

``` r
y<-bumpusdata$wgt
x<-paste(bumpusdata$surv,bumpusdata$sex)
boxplot(y~x)
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-46-1.png)<!-- -->

### barplot()

Plot with a categorical and continuous variables

``` r
barplot(c(223,251,317,636,766,607,607), main="Pages in Harry Potter books", ylab="Pages", xlab="Books", names=c("PS","CS","PA","GF","OP","HBP","DH"))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-47-1.png)<!-- -->

# PLOT MODIFIERS

### main=

The `main=` modifier titles the plot

``` r
boxplot(y~x, main="Bird weight by sex and survival")
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-48-1.png)<!-- -->

### ylab=

The `ylab` modifier labels the y-axis

``` r
boxplot(y~x, main="Bird weight by sex and survival", ylab="Bird weight")
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-49-1.png)<!-- -->

### xlab=

The `xlab=` modifier labels the x-axis

``` r
boxplot(y~x, main="Bird weight by sex and survival", ylab="Bird weight", xlab="Groups")
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-50-1.png)<!-- -->

### xlim=

The `xlim=` modifier allows you to change the limits of the x-axis

``` r
hist(males$wgt, xlim=c(20,35))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-51-1.png)<!-- -->

### ylim=

The `ylim=` modifier allows you to change the limits of the x-axis. Here
I increased the y-axis to 40

``` r
hist(males$wgt, ylim=c(0 ,40))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-52-1.png)<!-- -->

### col=

The `col=` modifier allows you to color the plot. (Arguably, the best
function within R)

**Color is a tool!** If you are using multiple colors, don’t just
randomly color in boxes, use the color to easily distinguish between
groups.

-   In my plot the females are pink and the males are blue.
    Additionally, the alive individuals are a lighter shade and the dead
    individuals are a darker color.

``` r
boxplot(y~x, main="Bird weight by sex and survival", ylab="Bird weight", xlab="Groups", col=c("palevioletred1","lightskyblue1", "palevioletred4", "lightskyblue4"))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-53-1.png)<!-- -->

### col=rgb()

`col=rgb()` is more specific than the col= modifier Not to be confused
with the notorious RBG, col=rgb() allows you to create custom colors by
changing the proportion of red, blue and green in that color.

-   For example, looking at the bumpus data for male weight, I can
    change the color and transparancy of the graph

-   The values range from 0 to 1, with 1 being the most extreme and 0
    being the least extreme

``` r
hist(males$wgt, col=rgb(0.1,0.5,0.792,1))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-55-1.png)<!-- -->

### add=TRUE

Using the `add=TRUE` you can combine two histogram code lines into one
graph. The add=TRUE is inserted as a modifier into the second hist().
Any modifiers to change graph (ylim, xlim, ylab, xlab, main, etc.) must
be added to first histogram function

This is a great way to use the col=rgb() function and change the
transparancy of the histograms to see where the histograms overlap. In
this example I am using the bumpus dataset to compare male and female
bird weight.

``` r
hist(females$wgt, col=rgb(0.9, 0.2, 0.32, 0.8), ylim=c(0,28), xlab=("bird weight"), main=("Histogram of male and female bird weight"))
hist(males$wgt, add=TRUE, col=rgb(0.1, 0.5, 0.7, 0.55))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-56-1.png)<!-- -->

### segments()

The `segments()` modifier is NOT a modifier, so it requires a new line
of code to work. The function basically works by connecting two points
with a straight line.

-   segments(X<sub>1</sub>, Y<sub>1</sub>, X<sub>2</sub>, Y<sub>2</sub>)
-   You can change the color of segments using either col=() or
    col=rbg()
-   lwd() changes the thickness of the line

While walking long the mall, I notice there is a single male bird, the
exact species that Bumpus used. What a lucky find! I take his mass. I am
interested to see if the bird mass is different now from when Bumpus did
his experiment **The segment line is the mean masse of the male bird I
caught.**

``` r
hist(males$wgt)
segments(27.5,0,27.5,25, col="royalblue3", lwd=5, lty="dotted")
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-57-1.png)<!-- -->

### text()

`text()` modifier adds text to any plot

``` r
hist(males$wgt)
segments(0,10,40,10, col="forestgreen", lwd=5)
text(29,11,"This is a line :)")
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-58-1.png)<!-- -->

### legend()

The `legend()` modifier puts a legend on your graph, telling the reader
what colors are certain variables legend(), like segments() needs its
own line beneath the histogram

-   Continuing with the same graph from above…

``` r
hist(females$wgt, col=rgb(0.9, 0.2, 0.32, 0.8), ylim=c(0,28), xlab=("bird weight"), main=("Histogram of male and female bird weight"))
hist(males$wgt, add=TRUE, col=rgb(0.1, 0.5, 0.792, 0.4))
legend("topright", c("Females", "Males"), fill=c("deeppink2","royalblue3"))
```

![](R-cheatsheet-BIO311_files/figure-gfm/unnamed-chunk-59-1.png)<!-- -->

# THAT’S ALL FOLKS!
