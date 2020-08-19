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
Now that our data has been read into our environment, lets give it a look. 

```{r}
head(covid.data)
```

I can see there are 80 variables, I'm going to focus on 2. 

## Choosing my variable 

I had chosen a data set which includes responses from participants regarding Covid-19 social measures. I wanted to graph a bi-variate plot, in order to include a second variable as well. I chose a question asking about the amount that the participant believes those who violate regulations around social gatherings should be fined. The second variable that I have included is the health of the participant, which was self-selected by the individual. 

I chose this variable because it would allow me to create a visualization which has a large degree of potential answers, and I wanted to show a lot of responses spread out over many values. Once I had identified my variables I isolated them.  
```{r}
colnames(covid.data)[which(names(covid.data) == "Geldstrafe_1_1")] <- "Fined"
covid.fine<-select(covid.data, 33, 54)
```

## Visualizing the Data 

Now that I have a data frame which only contains the 'fined' and 'health' values I can begin to look at the data to find the best visualization. Initially I wanted to use a scatter plot, so that I could track more of the individual values. This plan failed, since r requires that a scatterplot has the y variable to be defined. Within this plot y = the number of respondents, which is set as the default for other types of plots. Addtionally, a scatterplot would not be the best type of graph to demonstrate the connections between two variables which are linked and not seperated. 

```{r eval = FALSE}
ggplot(covid.fine, aes(Fined)) +
  geom_point()
```
This doesn't even give me a plot, so that won't work!

After the scatterplot I tried a bar graph. This result was a little better, but I didn't like how the proportions of the data were split, and I found it too hard to look at specific values and frequency distributions. 

```{r}
ggplot(covid.fine, aes(Fined)) +
  geom_bar()
```

Then I tried to use a histogram, so that I could adjust the proportions more easily and get a better understanding of the distibution of the data. 

```{r}
ggplot(covid.fine, aes(Fined)) +
  geom_histogram()
```

This looks much better! Not as clear as it can be, but closer!

## Adding additional variable

Now I want to add the second variable for health and make my plot look a little nicer.

```{r}
ggplot(covid.fine, aes(Fined, fill = health)) + geom_histogram() +
  theme_bw() +
  labs(title = "Amount Fined for A Social Gathering", y = "Number of Respondents", x = "Amount (in Pounds)")
```

Now the visualizations shows how much the respondents think the fine for regulation violation is, along with their health status. By looking at this visualization, any connections between health status and the amount the participant supports being levied will become more clearly visible. 

## Wrapping the plot 

I've cleaned my visualization up a lot, but to get a even better look at the specific data, lets facet wrap our plots. I'm going to wrap the plots according to the second variable, health, so that any possible connections between the two variables are evident. 

```{r}
ggplot(covid.fine, aes(Fined, fill = health)) + geom_histogram(binwidth = 30) +
  theme_bw() +
  labs(title = "Amount Fined for A Social Gathering", y = "Number of Respondents", x = "Amount (in Pounds)") +
  facet_wrap(vars(health), scales = "free")
```

