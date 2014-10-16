# Reproducible Research: Peer Assessment 1
Gareth Houk  
Thursday, October 16, 2014  
This document is produced using R Markdown for Project 1 of the Reproducible Research course.

The assignment's description of the dataset is as follows.

It is now possible to collect a large amount of data about personal movement using activity monitoring devices such as a Fitbit, Nike Fuelband, or Jawbone Up. These type of devices are part of the "quantified self" movement -- a group of enthusiasts who take measurements about themselves regularly to improve their health, to find patterns in their behavior, or because they are tech geeks. But these data remain under-utilized both because the raw data are hard to obtain and there is a lack of statistical methods and software for processing and interpreting the data.

This assignment makes use of data from a personal activity monitoring device. This device collects data at 5 minute intervals through out the day. The data consists of two months of data from an anonymous individual collected during the months of October and November, 2012 and include the number of steps taken in 5 minute intervals each day.


## Loading and preprocessing the data


```r
        csvfile <- "activity.csv"
        if (!file.exists(csvfile)) {
                zipfile <- "repdata_data_activity.zip"
                if (!file.exists(zipfile)) {
                        stop("Cannot find data files")
                } else {
                        unzip(zipfile)
                        if (!file.exists(csvfile)) {stop("Unzip Error")}
                }
        }
        data <- read.csv(csvfile)
        # Get dates into better format
        min<-as.character(data$interval%%100)
        hr <-as.character(floor(data$interval/100))
        hrmin <- paste(sep=":",hr,min,"00")
        data$min <-min
        data$hr  <-hr
        data$time<-as.POSIXct(paste(as.character(data$date),hrmin))
```

## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
