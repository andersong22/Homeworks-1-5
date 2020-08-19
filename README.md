## Homework 1 
## First I set my working directory to the folder on my desktop. 
## Install needed packages 
library(tidyverse)
library(readr)

## Read in the data from the working directory using 'read.delim' and assigning the data to a dataframe
covid.data <-read.delim("~/Desktop/R review summer 2020/covid data .csv", sep = ",", header = T)
View(covid.data.)

## I created the data frame 'covid.data'
## I used data read in from the working directory using 'read.delim'
## The first value is the path to the data file in my working directory 
## I specify the delimiter in the second value as "sep = ','" which indicates a csv (comma seperated value) file to be read in 
## The third value specifies that there is a header for the variables included in the data; "header = T", where 'T' is TRUE  

## Lets look at the data 
head(covid.data.)
## I use the function head() to look at the first several rows of the data, as well as the column names 





