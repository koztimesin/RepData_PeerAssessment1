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

# Imputing missing values
## 1.Calculate and report the total number of missing values in the dataset
`NATotal <- sum(!complete.cases(data))`
`NATotal `
## Total Number of Missing values are 2304

## 2.Using Mean for the day compute missing values
`StepsAverage <- aggregate(steps ~ interval, data = data, FUN = mean)`
`fillNA <- numeric()`
`for (i in 1:nrow(data)) {`
   ` obs <- data[i, ]`
   ` if (is.na(obs$steps)) {`
       ` steps <- subset(StepsAverage, interval == obs$interval)$steps`
 `   } else {`
      `  steps <- obs$steps`
  `  }`
  `  fillNA <- c(fillNA, steps)`
`}`

## 3. Create a new dataset including the imputed missing values
`new_activity <- data
new_activity$steps <- fillNA`

## 4. Make a histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day.
`StepsTotalUnion <- aggregate(steps ~ date, data = new_activity, sum, na.rm = TRUE)
hist(StepsTotalUnion$steps, main = paste("Total Steps Each Day"), col="orchid3", xlab="Number of Steps")`
## Create Histogram to show difference.
`hist(steps_by_day$steps, main = paste("Total Steps Each Day"), col="steelblue3", xlab="Number of Steps", add=T)
legend("topright", c("Imputed", "Non-imputed"), col=c("orchid3", "steelblue3"), lwd=10)`


![image3](https://github.com/koztimesin/RepData_PeerAssessment1/blob/master/figure/plot3.png)




## Calculate Mean 
`rmeantotal <- mean(StepsTotalUnion$steps)
rmeantotal`

## Calculate Median
`rmediantotal <- median(StepsTotalUnion$steps)
rmediantotal`

## Do these values differ from the estimates from the first part of the assignment?
`rmediandiff <- rmediantotal - rmedian
rmediandiff`

`rmeandiff <- rmeantotal - rmean
rmeandiff`


