# Homeworks-1-5
R Markdown script for Homework 1-5, Data Science Fundamentals, 601

## Selecting the Data 
  I selected data pertaining to a survey given to Italians about Covid-19 safety measures and regualtions being utilized by the Government of the United Kingdom. 

## Reading in the Data 
  After selecting my data source, I moved the downloaded xlsx (Excel) file to my desktop, and set the file as my working directory within R. Here is the code 
```{r}
setwd("~/Desktop/R Summer 2020")
```
## Installing packages 
  Before I begin to work on this data, I'm going to download all the packages I will need to manipulate the data the way we will need to. 
  ```{r}
install.packages("tidyverse"
library(tidyverse)
install.packages("readxl")
library(readxl)
```
I could also use 
```{r}
install.packages("readr")
library(readr)
```
I would use this if I was going to read a csv (comma-seperated value) file into my global environment. 

## Reading in the Data 
Now that we have all our packages installed and our working directory set, we are going to read our data set into the global environmnet. 

```{r}
covid.data <- read_excel("covid-responses.tab.xlsx")
```
Doing this same task with a csv file would look similar, 
```{r}
covid.data <-read.delim("~/Desktop/R review summer 2020/covid data .csv", sep = ",", header = T)
```
So now we have the file saved in our environment as "covid.data" 








