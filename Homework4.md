## Installing packages 
 
Im going to install all the packages I need in order to make this visualization 
```{r}
library(tidyverse)
library(readxl)
```


## Reading in the data 

Now we have to set the working directory, and read the data into our environment. 

```{r}
setwd("~/Desktop/R Summer 2020")
covid.data <- read_excel("covid-responses.tab.xlsx")
```

## Choosing my variable

I am investigating the relationship between two variables, the monetary amount of a fine, and the self-selection of a category of health. The 'Fine' variable is presented within the survey as a numeric variable, as respondents are able to select their value on a sliding number bar, with the highest value set as £500

The 'health' variable is an ordinal variable with categorical values, which are set as "Excellent", "Fair", "Good", and "Poor". The participants are asked to self select their own perceived level of health. 

Right now I am unsure about their potential relationship to each other, but I have a hypothesis that individuals with "less health", which includes the designations "Good" and "Poor", will respond with higher average fine amounts than respondents in the "good health" category, or "Excellent", and "Fair".

```{r}
colnames(covid.data)[which(names(covid.data) == "Geldstrafe_1_1")] <- "Fined"
covid.fine<-select(covid.data, 33, 54)
```

## Initial Plotting 

Using a histogram, I plotted an inital visulaization of the relationship between the health status of the participant, and the amount that they support for the fine. 

```{r}
ggplot(covid.fine, aes(Fined, fill = health)) + geom_histogram(binwidth = 30) +
  theme_bw() +
  labs(title = "Amount Fined for A Social Gathering", y = "Number of Respondents", x = "Amount (in Pounds)") +
  facet_wrap(vars(health), scales = "free")
```

This plot indicated that differences may exist between the reponses from participants with one type of health, as opposed to participants with another. 

Now the visualizations shows how much the respondents think the fine for regulation violation is, along with their health status. By looking at this visualization, any connections between health status and the amount the participant supports being levied will become more clearly visible. 

## Seperating the data 

After looking at the facet-wrapped plots, I wanted to more formally separate my data based on health. By doing this I can begin to analyze the data in different contexts. First lets look some tables to get an idea of the frame. 
```{r}
cov<- prop.table(table(covid.fine))
view(cov)

```

Wow! So that table shows each value a respondent inputted on the far left, and the amount of times that value appeared within each heatlh category. I want to take a closer look at this data. Let me divide it more formally! 
```{r}
fine.excellent<- filter(covid.fine, `health` == "Excellent")
fine.fair<- filter(covid.fine, `health` == "Fair")
fine.good <- filter(covid.fine, `health` == "Good")
fine.poor <- filter(covid.fine, `health` == "Poor")
```

These data frames show each value that has been selected by a respondent in each health category. I am interested in looking at the frequency with which each value occurs within each category. To do this I am going to create some new vectors

```{r}
EXL<- table(select(fine.excellent,(Fined)))
prop.table(table(EXL))

FAI<- table(select(fine.fair,(Fined)))
prop.table(table(FAI))

GOO<- table(select(fine.good,(Fined)))
prop.table(table(GOO))

POOR<- table(select(fine.poor,(Fined)))
prop.table(table(POOR))
```
These vectors show me the frequency with which each value has been selected. I can see that £500 is the most popular option by far. When I look at the prop tables, I can see the proportion that all the values selected by the respondents show up in the data. 

Even though this data is really descriptive, its not very easy to interpret, since there are so many individual values. What I really want is a more clear visualization which can place the change in the value over time within the frame.  

```{r}
ggplot(fine.excellent, aes(Fined, health)) + geom_violin()

ggplot(fine.fair, aes(Fined, health)) + geom_violin()

ggplot(fine.good, aes(Fined, health)) + geom_violin()

ggplot(fine.poor, aes(Fined, health)) + geom_violin()

```

These Violin plots show the rapid increase in the respondent selection around the upper values, and by using this plot and the prop tables and frequency vectors generated earlier, I am able to understand how this data is meant to be formatted and interacted with. 
