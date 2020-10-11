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

