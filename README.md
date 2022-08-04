# analysis_of_penguin_species
Data science task on penguin species
---
title: "Penguins Project README"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


The original data for this project comes from the `palmerpengunis` package and 
has records of three species of penguin (Adelie, Gentoo, and Chinstrap) from the 
years 2007 to 2009. The island that the record was taken on is noted along with 
the sex of the penguin and the following individual measurements: bill length, 
bill depth, and flipper length (all 3 in millimeters), as well as the body mass 
in grams. 

### Libraries required

* `library(tidyverse)`
* `library(palmerpenguins)`
* `library(ggplot)`
* `library(e1071)`
* `library(infer)`
* `library(GGally)`

### This project's folder layout is as follows: 

`PDA_penguins_mahri`

* `documentation_and_analysis`

  * `statistics_and_hypothesis_testing_penguins_mahri.Rmd`
  * `correlation_matrix_mahri.Rmd`
  * `wip_penguins_part_1_mahri.Rmd`
  
* `homework_tasks`

  * `penguins_part_1.html`
  * `penguins_part_2.html`
  
* `readme_penguins_project.Rmd`

  
## Exploration and Analysis of the Data

The `palmerpenguins` package was read into Rstudio. As we were initially 
interested in comparing bill length among species, any 'NA's in the column 
'bill_length_mm' were dropped before the data was grouped by penguin species and
a total count of each species taken. There were 151 Adelie penguins, 68 Chinstrap,
and 123 Gentoo. 	

A comparison of the differences in each species mean bill length was calculated 
and then visualised on a bar chart using `ggplot2`. However, to better understand 
each species, boxplots were created to show a comparison of bill lengths between 
species, and a histogram showing the total number of penguins in each species with 
each bill length was also created. 

Summary statistics were calculated to show measures of centrality (mean and 
median), spread (standard deviation), and skewness for each species. Remembering 
that there are far fewer Chinstrap penguins, a hypothesis test with a chosen 
significance level of 0.05 was devised to test whether the mean bill length of 
Gentoo is significantly longer than the mean bill length of Adelie. A one-tailed, 
independent samples test was conducted with the following hypotheses:

* H0: The mean bill length of the Gentoo penguin is not significantly longer 
than that of the Adelie penguin. 
* H1: The mean bill length of the Gentoo penguin is significantly longer than the 
mean bill length of the Adeli penguin.

To see if there is an implication of species upon bill length or whether the 
difference is down to sampling variation (chance), a null distribution by 
permutation, calculating the difference in the means, was generated. Using 
permutation, the 'species' variable labels were shuffled (i.e. detaching the labels 
from rows and then randomly assigning them back to rows) so that any relationship 
between species and bill length was lost. In this case, this was repeated 5000 
times to account for sampling variability and so generates a distribution of 5000 
samples. 

The null distribution was then visualised having calculated the observed
statistic. From the visualisation, it could be seen that the observed statistic 
was far to the right of the null distribution and therefore there is a very small
probability of getting a more extreme value than the observed statistic. To be 
sure, the p-value was calculated and found to be very close to 0, allowing the
null hypothesis to be rejected in favour of the alternative hypothesis.

Finally, a correlation matrix was created using Pearson's correlation coefficient
and the original data set. It shows the correlations between bill length, bill 
depth, flipper length, and body mass across species. 

