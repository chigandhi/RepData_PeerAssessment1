# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
workingDirectory <- c("C:\\Users\\Chirag\\chirag personal\\US\\coursera\\RepData\\RepData_PeerAssessment1")
outputDirectory <- c("C:\\Users\\Chirag\\chirag personal\\US\\coursera\\RepData\\RepData_PeerAssessment1\\")

filename <- c("activity.csv")
setwd(workingDirectory)

stepData <- read.csv(file = filename, na.strings="NA")
stepData$interval <- factor(stepData$interval)
```
## What is mean total number of steps taken per day?


```r
tot_steps <- aggregate(steps ~ date, stepData, FUN=sum)

barplot(tot_steps$steps, names=tot_steps$date, col="blue", main="Total Daily Steps",xlab="Date", ylab="Total Steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
#mean_steps <- format(mean(tot_steps$steps, na.rm=TRUE), digits=2, nsmall=2)

#median_steps <- median(tot_steps$steps, na.rm=TRUE)
```
### The Average number of steps taken daily (Mean) = 10766.19  
### The Median number of steps taken daily (Median) = 10765

## What is the average daily activity pattern?

```r
dailyAvg <- aggregate(steps ~ interval, stepData, FUN = mean)
plot(dailyAvg$interval, dailyAvg$steps, type="n", main="Average Daily Activity Pattern",xlab="Interval", ylab="Average Steps")
lines(dailyAvg$interval, dailyAvg$steps, type="l")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

```r
maxAvg <- max.col(dailyAvg$steps)
```

### The Interval containing the maximum average daily steps is 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1   

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
