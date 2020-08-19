## Homework 2 
## Selected Data

I selected data pertaining to a survey given to Italians about Covid-19 safety measures.

Reading in the data
After selecting my data source, I moved the downloaded csv (comma-seperated values) file to my desktop, and set the file as my working directory within R.

Here's the code
```{r}
setwd("~/Desktop/R review summer 2020")
```
After setting my working directory, I need to read my data into my global environment.

Here is the code
```{r}
covid.data <-read.delim("~/Desktop/R review summer 2020/covid data .csv", sep = ",", header = T)
```
## Lets view the data
First lets get a look at the dimensions of the data by using the function dim()
```{r}
dim(covid.data)
```
## [1] 3460   80
Now we see that this data set has 80 Column names and 3460 Rows. Since a single row represents a single observation, finding the dimensions of the data frame means that we now know that there are 3460 individual responses to the survey within the data set.

While a row is a single observation within a data frame, a column represents a variable. According to R, this dataframe includes 80 seperate variables! Lets look at what those variables are.

## Column Names
Lets use R to find the names of all the variables accounted for in the survey,
```{r}
colnames(covid.data)
```
##  [1] "StartDate"              "EndDate"                "Status"                
##  [4] "Progress"               "Duration..in.seconds."  "Finished"              
##  [7] "RecordedDate"           "ResponseId"             "RecipientLastName"     
## [10] "RecipientEmail"         "ExternalReference"      "LocationLatitude"      
## [13] "LocationLongitude"      "DistributionChannel"    "UserLanguage"          
## [16] "Q1"                     "SelfReported_Behavio_1" "SelfReported_Behavio_2"
## [19] "SelfReported_Behavio_3" "SelfReported_Behavio_4" "SelfReported_Behavio_5"
## [22] "Reflection"             "T2"                     "social"                
## [25] "handshake"              "stores"                 "curfew"                
## [28] "SOB_1"                  "SOB_2"                  "SOB_3"                 
## [31] "SOB_4"                  "financialpunishment"    "Geldstrafe_1_1"        
## [34] "Geldstrafe_2_1"         "perceivedreaction"      "Q36"                   
## [37] "Q37"                    "Q23"                    "perceivedeffectivnes"  
## [40] "anxiety_1"              "anxiety_2"              "anxiety_3"             
## [43] "anxiety_4"              "anxiety_5"              "Q24"                   
## [46] "Q25"                    "Q25_13_TEXT"            "Q26"                   
## [49] "Q26_11_TEXT"            "age"                    "gender"                
## [52] "gender_3_TEXT"          "zipcode"                "health"                
## [55] "health_conditions"      "personality_1"          "personality_2"         
## [58] "personality_3"          "personality_4"          "personality_5"         
## [61] "personality_6"          "personality_7"          "personality_8"         
## [64] "personality_9"          "personality_10"         "Q27_5"                 
## [67] "Q35"                    "Q62_5"                  "Q62_6"                 
## [70] "Q62_7"                  "Q62_8"                  "Q62_9"                 
## [73] "Q62_11"                 "Q62_12"                 "Q62_13"                
## [76] "Q62_14"                 "Q62_15"                 "rid"                   
## [79] "treatment"              "finish"
Looking at these column names, its easier to get a better understanding of the intent of the survey and see which questions relate to each other. By looking at a data frame in this way it becomes easier to plan for future analysis.
