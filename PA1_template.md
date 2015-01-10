# Reproducible Research: Peer Assessment 1


### Loading and preprocessing the data


```r
unzip("activity.zip")
data <- read.csv("activity.csv")
dim(data)
```

```
## [1] 17568     3
```

```r
str(data)
```

```
## 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
```

**Next we will explore the data with a series of questions:**  
1. What is the mean total number of steps taken per day?  
2. What is the average daily activity pattern?  
3. Imputing missing values  
4. Are there differences in activity patterns between weekdays and weekends?  

### 1: What is mean total number of steps taken per day?


```r
mean(data['steps'][ !is.na(data['steps'])])
```

```
## [1] 37.3826
```

I'm not sure why ```mean(data['steps'], na.rm=TRUE)``` wouldn't work, but it gave me the following output:
```
[1] NA
Warning message:
In mean.default(data["steps"], na.rm = TRUE) :
  argument is not numeric or logical: returning NA
```

### 2: What is the average daily activity pattern?


### 3: Imputing missing values


### 4: Are there differences in activity patterns between weekdays and weekends?
