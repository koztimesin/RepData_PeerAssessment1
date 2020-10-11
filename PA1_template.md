# What is mean total number of steps taken per day?
## Calculation of the total number of steps taken per day and create a histogram
`steps_by_day <- aggregate(steps ~ date, data, sum)`
`hist(steps_by_day$steps, main = paste("Total Steps Each Day"), col="steelblue3",xlab="Number of Steps")`

## Calculate the Mean and Median Values
`rmean <- mean(steps_by_day$steps)`
`rmean`

`rmedian <- median(steps_by_day$steps)`
`rmedian`

## The mean is 10766.19 and the median is 10765


![image1](https://github.com/koztimesin/RepData_PeerAssessment1/blob/master/figure/plot1.png)

# What is the average daily activity pattern?
## 1.Calculate average steps for each interval for all days
## 2.Pot the Average Number Steps per Day by Interval
## 3.Find interval with most average steps

`steps_by_interval <- aggregate(steps ~ interval, data, mean)`
`plot(steps_by_interval$interval,steps_by_interval$steps, type="l", xlab="Interval", ylab="Number of Steps",main="Average Number of Steps per Day by Interval")`

`max_interval <- steps_by_interval[which.max(steps_by_interval$steps),1]`
`max_interval`

## The interval with most steps is 835

![image2](https://github.com/koztimesin/RepData_PeerAssessment1/blob/master/figure/plot2.png)


