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

No post-processing currently seems necessary as items seem to be in appropropate formats.

One potential alternation would be to converte date from a factor to a date format via:
```as.Date(data['date'][,], format="%Y-%m-%d")```

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

An alternative method of calculation would be: ```mean(data['steps'][,], na.rm=TRUE)``` and also yields the same result: ``37.3825996``

### 2: What is the average daily activity pattern?


### 3: Imputing missing values


### 4: Are there differences in activity patterns between weekdays and weekends?
