# Reproducible Research: Peer Assessment 1

### Setup some defaults


Note, some global defaults for the RMarkdown processing are set, but not shown, to ensure code chunks are always visible for peer review.

### Loading and preprocessing the data


```r
library(data.table)
unzip("activity.zip")
my_data <- read.csv("activity.csv")
my_data$date <- as.Date(my_data['date'][,], format="%Y-%m-%d")
my_data$interval <- as.factor(my_data$interval)
my_data <- data.table(my_data) ##Used for grouping
str(my_data)
```

```
## Classes 'data.table' and 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Date, format: "2012-10-01" "2012-10-01" ...
##  $ interval: Factor w/ 288 levels "0","5","10","15",..: 1 2 3 4 5 6 7 8 9 10 ...
##  - attr(*, ".internal.selfref")=<externalptr>
```

For post-processing dates are converted into a ``Date`` object and the intervals are converted into a ``factor``, and a ``data.table, data.frame`` object is used to facilitate further analysis.

**Next we will explore the data with a series of questions:**  
1. What is the mean total number of steps taken per day?  
2. What is the average daily activity pattern?  
3. Imputing missing values  
4. Are there differences in activity patterns between weekdays and weekends?  

### 1: What is mean total number of steps taken per day?

    For this part of the assignment, you can ignore the missing values in the dataset.  
        1. Make a histogram of the total number of steps taken each day  
        2. Calculate and report the mean and median total number of steps taken per day  

For this section, it was assumed that 'ignoring' ```NA``` values meant accepting the default behavior (e.g. when graphing) or excluding them from the calculations.

1. A histogram of the data is:

```r
hist(tapply(my_data[['steps']], my_data[['date']], sum), breaks=15,
    ylab = "Frequency", xlab="Steps", 
    main = "Total Daily Steps by Frequency")
```

![](figure/unnamed-chunk-2-1.png) 

2a. The mean value for the data is:

```r
mean(my_data[['steps']][ !is.na(my_data[['steps']])])
```

```
## [1] 37.3826
```

An alternative method of calculation would be: ```mean(my_data[['steps']], na.rm=TRUE)``` and also yields the same result: ``37.3825996``

2b. The median value for the data is:

```r
median(my_data[['steps']], na.rm=TRUE)
```

```
## [1] 0
```

### 2: What is the average daily activity pattern?

The average daily activity pattern is calculated by summarizing the average activity per day, and then visualized via a graph, with the overall daily average, rounded to 2 decimal points, represented as a horizontal line.


```r
averages <- my_data[, mean(steps), by=c("date")]
overall_average <- mean(averages[['V1']], na.rm=TRUE)

plot(averages, 
    ylab="Ave. Steps",
    xlab="Date")
title("Average Steps per Day")
abline(h=overall_average, col=2)
```

![](figure/unnamed-chunk-5-1.png) 

The overall average is ``37.3825996``.


### 3: Imputing missing values


### 4: Are there differences in activity patterns between weekdays and weekends?

```
