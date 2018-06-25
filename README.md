# MSDS692-Final-Project
Final Project for MSDS692

## Helping Students Achieve Four-year Graduation Rates by Predicting Computer Science (CS) Program Pain Points in CS Course Sequence.

# Project Overview

Higher Education Institutions struggle in general with the problem of how to increase the graduation rates not just by institution but also by program. Graduation rates are actually reported 2 ways, as the percentage of full-time students who graduate in 4 years and as the percentage of students who graduate in 6 years. These measures are used to rank institutions and are important to maintain or increase enrollment and reputation. In this case we are going to look at the Computer Science program at a Colorado University where not all students that enroll with the Major of Computer Science stay and finish. Some students leave the institution but others change majors while progressing through the coursework. 
We would like to have a better understanding on why and when this happens. We believe that if we are able to predict what students are at risk when taking certain classes then they can be proactive and give additional support to these students to help them succeed and prevent attrition or delay in program completion. 
A variety of factors influence the student decision to leave or change major but we think that there may be a strong relationship between grades obtained in certain courses in a course sequence and four-year graduation rates.

We will try to answer the following questions:

*	What students are at risk at the start of a course to make sure we address their needs and provide support proactively?
* Which are the main points of attrition in the CS course sequence conducive to the loss of students from the CS program or University?

### Data Sets

The data used was extracted from the University Database using IBM Cognos as the tool to query the database. Data from 2008 to 2018 was used. Two data sets were created; One with grades for courses in the math and CS sequences all CS students are required to take for graduation, and another set with the dates when these courses were taken. Both data sets also contained variables describing if the students graduated from CS or if they left the program. A variable was included to describe if the students graduated in four years from CS or if they changed major from the major they changed to.

### Observations on the Quality and cleaning of the Data
It was observed in both data sets that to show all the variables needed more than one table from the database was needed. Not all tables resided in the same Cognos packages so further mergers were necessary. Merges were performed utilizing Tableau with the student ID as the item for linking the separate data files. 
Further changes and cleaning were necessary:
* Academic period format had to be changed from year-period to year-month.
* Course names had to be changed to Number of Semester recommended plus course code.
* Double majors had to be cleaned to show just the CS record.
* Several CASE statements in Tableau were used to define depending registration in Spring 18 and Fall 18 if the students were current students or if the students had left the institution.
* CASE statements in Tableau were used to define the student group as CS students if CS had been their original major or their first major.
* Calculations were added in Tableau to define the length between original major date and graduation date. Aditional modifications and preparation of the data sets happend in R. Detailes can be found in all the attached R files.

After modifications the finished data sets consisted of the fallowing variables:  
#### Data Set 1
'data.frame':	536 obs. of  24 variables:  

Year of OriginalMajorDate: int  2014 2008 2008 2011 2008 2008 2008 2008 2008 2008 ...  
GraduationStatus         : Factor w/ 3 levels "CurrentStudent",..: 2 2 3 3 2 2 2 2 3 2 ...  
YearsFromOMD             : num  4 9.84 9.84 6.84 9.84 9.84 9.84 9.84 9.84 9.84 ...  
CsGrad                   : Factor w/ 3 levels "NG","OtherMajor",..: 3 2 1 1 2 3 3 2 1 2 ...  
4YG                      : Factor w/ 2 levels "No","Yes": 2 1 1 1 2 2 2 2 1 2 ...  
5YG                      : Factor w/ 2 levels "No","Yes": 2 2 1 1 2 2 2 2 1 2 ...  
6YG                      : Factor w/ 2 levels "No","Yes": 2 2 1 1 2 2 2 2 1 2 ...  
1_CSCI101                : num  4 NA NA NA NA 4 4 NA NA NA ...  
1_MATH111                : num  3 3 3 3 3 3 4 3 2 3 ...  
2_CSCI261                : num  4 4 4 3.3 4 3 4 3 3 3 ...  
2_MATH112                : num  2 2 2 4 3 3 4 4 2 2 ...  
2_MATH201                : num  3 3 2 NA 3 2 4 NA NA 1 ...  
3_CSCI262                : num  3 NA 1 3 NA 3 4 4 1 NA ...  
3_MATH213                : num  4 3 2 2 3 4 4 4 1 2 ...  
4_CSCI341                : num  2 NA 2 2 NA 3 4 NA 3 3 ...  
4_CSCI358                : num  4 NA 3 2 NA 2 4 NA NA NA ...  
4_MATH225                : num  4 3 1 4 4 3 4 4 NA 1 ...  
5_CSCI306                : num  3 NA NA 3.7 NA 4 4 4 NA NA ...  
5_CSCI403                : num  4 NA NA 3 NA 4 4 NA NA NA ...  
5_MATH332                : num  3 NA 2 3 NA 3 4 NA NA NA ...  
6_CSCI406                : num  2 NA NA 0.3 NA 2 4 NA NA NA ...  
7_CSCI370                : num  3.3 NA NA NA NA 4 4 NA NA NA ...  
8_CSCI400                : num  3.3 NA NA 3.3 NA 3 4 NA NA NA ...  
9_CSCI442                : num  2.3 NA NA NA NA 3 4 NA NA NA ...  

#### Data Set 2

Classes ‘tbl_df’, ‘tbl’ and 'data.frame':	195 obs. of  25 variables:  

UID                      : chr  "12972" "12973" "41647" "98022" ...  
Year of OriginalMajorDate: chr  "2008" "2008" "2011" "2008" ...  
YearsFromOMD             : chr  "9.88" "9.88" "6.88" "9.88" ...  
4YG                      : Factor  "No" "No" "No" "Yes" ...  
5YG                      : Factor  "Yes" "No" "No" "Yes" ...  
6YG                      : Factor  "Yes" "No" "No" "Yes" ...  
GraduationStatus         : chr  "Graduated" "InactiveReg" "InactiveReg" "Graduated" ...  
CsGrad                   : chr  "OtherMajor" "NG" "NG" "OtherMajor" ...  
Nine.CSCI442             : num  NA NA NA NA NA ...  
Eight.CSCI400            : num  NA NA 2017 NA NA ...  
Seven.CSCI370            : num  NA NA NA NA NA ...  
Six.CSCI406              : num  NA NA 2018 NA NA ...  
Five.CSCI403             : num  NA NA 2017 NA NA ...  
Five.MATH332             : num  NA 2011 2015 NA NA ...  
Five.CSCI306             : num  NA NA 2017 NA 2011 ...  
Four.CSCI358             : num  NA 2012 2017 NA NA ...  
Four.CSCI341             : num  NA 2011 2015 NA NA ...  
Four.MATH225             : num  2010 2011 2015 2010 2009 ...  
Three.CSCI262            : num  NA 2010 2015 NA 2010 ...  
Three.MATH213            : num  2010 2010 2013 2009 2009 ...  
Two.CSCI261              : num  2010 2010 2014 2010 2009 ...  
Two.MATH201              : num  2011 2012 NA 2010 NA ...  
Two.MATH112              : num  2009 2010 2013 2009 2009 ...  
One.MATH111              : num  2009 2009 2013 2009 2009 ...  
One.CSCI101              : num  NA NA NA NA NA ...  

### Process for project/Major tools used

This project was completed utilizing:
* IBM Cognos -  to query the University data base and produce seven different csv files from different tables.
* Tableau – to clean, format, and combine csv files into two main files. Data was pivoted and summarized to produce the desire order of variables and information.
* R – Used to modify, and analyze the two main data sets. R files are located at:
* A youtube presentation is located at: 

# EDA (Exploratory Data Analysis)
### Data Set 1
The data sets were uploaded, summaries, data frames, tables and plots created using the code below.
```{r}
setwd("~/REGIS/Practicum I/RStudio")
dataSet <- read_excel("./dataSet.xlsx")
#View(dataSet)
```
Transform data set into data frame
```{r}
dfDataSet <- as.data.frame(dataSet)
head(dfDataSet)
```
```{r}
head(dfDataSet)
```

```{r}
summary(dfDataSet)
```
Transform Variable's type to the appropriate data type
```{r}
dfDataSet[1] <- lapply(dfDataSet[1], as.integer)
dfDataSet[3] <- lapply(dfDataSet[3], as.numeric)
dfDataSet[8:24] <- lapply(dfDataSet[8:24], as.numeric)
dfDataSet[2] <- lapply(dfDataSet[2], as.factor)
dfDataSet[4:7] <- lapply(dfDataSet[4:7], as.factor)
str(dfDataSet)
```
```{r}
summary(dfDataSet)
```
Transform data frame into a table
```{r}
tbDataSet <- data.table(dfDataSet)
tbDataSet

```
Create a table for variable "GraduationStatus"
```{r}
tb <- table(dfDataSet$GraduationStatus)
tb

```
Create table with percentages of total
```{r}
tb.prop <- dfDataSet$GraduationStatus %>%
   table() %>%
   prop.table() %>% {. * 100} %>% 
   round(2)

tb.prop
```
Create a Pie chart
```{r}
pie(tb, main = "CS Students Status that Started 2008-2014", col = c("Light Blue","Navy Blue","Dark Orange"))
```
![](CS Students Status Pie.png)
Create a Bar chart
```{r}
barplot(tb, col = "navy blue", ylim=c(0,400),main = "Computer Science Students who Started the Program (2008-2014)")
```

Create a Bar plot where the "graduated"" students are divided into CS and Other Major students
```{r}
ggplot(dfDataSet) + 
  geom_bar(aes(x = factor(GraduationStatus), fill = CsGrad), position = 'dodge') +
  xlab('Graduation Status') + ylab('Frequency')
```
Create a plot to represent the CS students that have graduated in 4 years
```{r}
ggplot(dfDataSet) + 
  geom_bar(aes(x = factor(GraduationStatus), fill = dfDataSet$"4YG"), position = 'dodge') +
  xlab('Graduation Status') + ylab('Frequency')
```
Create a table of numbers and percetages of students that graduate in 4 years
```{r}
tb4YG <- table(dfDataSet$"4YG")
tb4YGpercent <- prop.table(tb4YG)
tb4YGpercent
cbind(tb4YG,prop.table(tb4YG))
```
Create a Pie Chart for Four-year graduation rate
```{r}
pie(tb4YG, main = "CS Students that Graduated in Four Years", col = c("Light Blue","Navy Blue","Dark Orange"))
```
Create a Bar chart for Four-year graduation rate
```{r}
barplot(tb4YGpercent, col = "navy blue", ylim=c(0,1),main = "Four Year Graduation Rate for CS Students who Started on 2008-2014")
```
Create a table of numbers and percetages of students that graduate in 5 years
```{r}
tb5YG <- table(dfDataSet$"5YG")
tb5YGpercent <- prop.table(tb5YG)
tb5YGpercent
cbind(tb5YG,prop.table(tb5YG))
```
Create a Pie Chart for Five-year graduation rate
```{r}
pie(tb5YG, main = "CS Students that Graduated in Five Years", col = c("Light Blue","Navy Blue","Dark Orange"))
```
Create a Bar Chart for Five-year graduation rate
```{r}
barplot(tb5YGpercent, col = "lightblue", ylim=c(0,1),main = "Five Year Graduation Rate for CS Students who Started on 2008-2014")
```
Create a table of numbers and percetages of students that graduate in 6 years
```{r}
tb6YG <- table(dfDataSet$"6YG")
tb6YGpercent <- prop.table(tb6YG)
tb6YGpercent
cbind(tb6YG,prop.table(tb6YG))
```
Create a Pie Chart for Five-year graduation rate
```{r}
pie(tb6YG, main = "CS Students that Graduated in Six Years", col = c("Light Blue","Navy Blue","Dark Orange"))
```
Create a Bar Chart for Six-year graduation rate
```{r}
barplot(tb6YGpercent, col = "navy blue", ylim=c(0,1), main = "Six Year Graduation Rate for CS Students who Started on 2008-2014")
```
### Data Set 2
Variable CS Grad:  
* Yes - CS Students
* OtherMajor - Left CS
* NG - Not Graduated. 

Data from 2008-2018 and excludes current students and students that graduated from CS.

Import Data Set and open libraries.
```{r}
library(readxl)
CourseDateData <- read_excel("CourseDateData.xlsx")
library(readxl)
CourseDateDataNoCS <- read_excel("CourseDateDataNoCS.xlsx")
```
Take a look at the data.
```{r}
summary(CourseDateDataNoCS)
```
```{r}
str(CourseDateDataNoCS)
```
Remove unecesary columns
```{r}
DataNoCS <- CourseDateDataNoCS[-(1:6)]
str(DataNoCS)
```
Transform data type to the appropriate type.
```{r}
DataNoCS$GraduationStatus <- as.factor(DataNoCS$GraduationStatus)
DataNoCS$CsGrad <- as.factor(DataNoCS$CsGrad)
str(DataNoCS)
```
Remove Math Courses to understand better when students leave the CS program.
```{r}
CourseDates <- DataNoCS[-(1:2)]
CourseDates <- CourseDates[-(6)]
CourseDates <- CourseDates[-(9)]
CourseDates <- CourseDates[-(10)]
CourseDates <- CourseDates[-(11:13)]
str(CourseDates)
```
Transform data set into data frame.
```{r}
dfCourseDates <- as.data.frame(CourseDates)
```
Replace NA with 0
```{r}
dfCourseDates[is.na(dfCourseDates)] <- 0
head(dfCourseDates)
```
Find highest level last class each student took.
```{r}
LastClass <- colnames(dfCourseDates)[max.col(dfCourseDates,ties.method="first")]
dfCourseDates$LastClass <- LastClass
head(dfCourseDates)
```
```{r}
summary(dfCourseDates)
```
Open additional libraries
```{r}
library(caret)
library(lattice)
library(ggplot2)
```
Create table from data frame.
```{r}
tbLastClass <- table(dfCourseDates$LastClass)
tbLastClass
```
Create a data frame from table for graphing.
```{r}
dfLastClass <- as.data.frame(tbLastClass)
dfLastClass
```
Graph frequency of last CS class taken by students that left the program.
```{r}
p<-ggplot(data=dfLastClass, aes(x= reorder(Var1, Freq),  y=Freq)) +
  geom_bar(stat="identity", fill="steelblue") +
  labs(title ="Last Highest CS Course Taken by Not Grad. and Other Major Students", x = "Course", y = "Frequency") +
  ylim(0,60) +
  theme(axis.text.x=element_text(angle=90, hjust=1)) +
  geom_text(aes(label = Freq), hjust=-.5 , position = position_dodge(width = 1),inherit.aes = TRUE) +
  coord_flip()
p
```
To start the analysis for four year graduation success the need of creating a subset of the data arised. It was necessary to look at just the students that had completed the CS program succesfully in four years. It was also helpful to find the correlation between the courses taken by the students. The code below was used to achieve this.
---
title: "Subsets of Data Set"
author: "Vanessa Gonzalez"
date: "`r format(Sys.Date())`"
output: html_notebook
---

## CS Graduated Students Data Set
```{r}
library("caret")
summary(dfDataSet)
```
Create a subset of data consisting of students with a "GraduationStatus" of "Graduated"
```{r}
GraduatedData<-subset(dfDataSet, GraduationStatus == 'Graduated')
head(GraduatedData)
```
Look at the data subset
```{r}
summary(GraduatedData)
```
```{r}
str(GraduatedData)
```
Remove not needed columns from data set and leave factor Four-year Graduation Factor
```{r}
DataSet4YG <- GraduatedData[(5:24)]
DataSet4YG <- DataSet4YG[-(2:3)]
head(DataSet4YG)
```
Transform data set into a data frame
```{r}
dfDataSet4YG <-as.data.frame(DataSet4YG)
```
Find coorelation between variables using "spearman" method
```{r}
res<- cor(dfDataSet4YG[-(1)], method = 'spearman', use = "complete.obs") 
round(res,2)
```
To substitute NA values with another value the KNN Imputation method is used
```{r}
library("DMwR")
DataSet4YGImpute <- knnImputation(DataSet4YG)
head(DataSet4YGImpute)
```
```{r}
str(DataSet4YGImpute)
```
```{r}
dfDataSet4YGImpute <-as.data.frame(DataSet4YGImpute)
```
Create a correlation plot between variables
```{r}
library(corrplot)
```
```{r}
corrplot(cor(dfDataSet4YGImpute[-(1)], method = 'spearman', use = "complete.obs"))
```
To determine variables with a correlation higher than 0.5
```{r}
highlyCorrelated <- findCorrelation(res, cutoff=0.5)
print(highlyCorrelated)
```
[1] 13 16  5 10 14 17

# Analysis


# Conclusions

# References 
link to video etc.

images: ![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")


