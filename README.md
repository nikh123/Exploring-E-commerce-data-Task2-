# Introduction
Here is the coding I did on E-commercer data a task from google code in. 

# Required
- R
- R studio
- dplyr

# Code description
```
# Exploring-E-commerce-data-Task2

library(dplyr)

ecommerce=read.csv("https://github.com/FahroziFahrozi/Google-Code-In-Task/raw/master/Task%20Dataset.csv",
           header = TRUE)

#how many observation and variables are in the data set?

nrow(ecommerce)
#[1] 1594 observations
ncol(ecommerce)
#[1] 45 variables

#which city had the most visitors and how many? Among Australia cities

subset_Australia=subset(ecommerce,ecommerce$country=="Australia")
subset_Australia %>%
  group_by(city) %>%
  summarise(behavNumVisits=sum(behavNumVisits)) %>% arrange(desc(behavNumVisits))
  
#Brisbane

#Draw a horizontal box plot for the number of site visits.

boxplot(ecommerce$behavNumVisits, horizontal = TRUE)

#Solve the previous problem for the city with the most visitors, using the which.max function

Most_visitors=ecommerce %>%
  group_by(city) %>%
  summarise(behavNumVisits=sum(behavNumVisits))
max_city_visitor=which.max(Most_visitors$behavNumVisits)
Most_visitors[max_city_visitor,]

#city     behavNumVisits
#1 Lakewood            104


#What is the mean-median difference for number of site visits?

mean_visite=mean(ecommerce$behavNumVisits)
median_visite=median(ecommerce$behavNumVisits)
mean_visite-median_visite

#[1] 0.7715003

#What is the mean-median difference for site visits, after excluding the person who had the most visits?

max_index=which.max(ecommerce$behavNumVisits)
ecommerce[max_index,]
ecommerce_exlude=ecommerce[-c(max_index),]
mean_visite=mean(ecommerce_exlude$behavNumVisits)
median_visite=median(ecommerce_exlude$behavNumVisits)
mean_visite-median_visite

#[1] 0.7715003
```

# Screen cast
![](http://g.recordit.co/ZDI8e3jTCe.gif)

# Authors
- Nikhil
