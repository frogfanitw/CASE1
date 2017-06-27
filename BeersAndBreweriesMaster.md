# BeersAndBreweriesCaseStudy
David Benepe  
June 23, 2017  



## Introduction

Organizers of the 2018 Craft Brewers Conference have requested a Data Analysis for presentation at the conference to be held April 18-May 3, 2018 in Nashville.  This report summarizes the available data on beers and breweries to be used in the Data Analysis along with answers to an initial list of questions submitted by the organizers.   From this information, the organizers will develop a formal request for the Data Analysis and Presentation.

## Breweries

The Breweries dataset contains data about US breweries, including a unique identifier, name, and the city and state where each brewery is located.
The following code reads in the original Breweries.csv dataset and displays summary information about the data.


```r
## source(file="testinfo/Analysis/LoadBreweryFile.R",print.eval=TRUE)
## this makefile is "LoadBreweryFile.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  load the raw data from "breweries.csv" file stored in the "/testinfo/DATA" folder of the working directory (Rproject folder) 
## assign the contents of the file to a dataframe called "OriginalBreweryData"
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# read in the BreweryData
filename=paste(DataPath,"Breweries.csv",sep="")
OriginalBreweryData<-read.csv(filename,sep=",",header=TRUE)
# display sample data for data checking
class(OriginalBreweryData)
```

```
## [1] "data.frame"
```

```r
str(OriginalBreweryData)
```

```
## 'data.frame':	558 obs. of  4 variables:
##  $ Brew_ID: int  1 2 3 4 5 6 7 8 9 10 ...
##  $ Name   : Factor w/ 551 levels "10 Barrel Brewing Company",..: 355 12 266 319 201 136 227 477 59 491 ...
##  $ City   : Factor w/ 384 levels "Abingdon","Abita Springs",..: 228 200 122 299 300 62 91 48 152 136 ...
##  $ State  : Factor w/ 51 levels " AK"," AL"," AR",..: 24 18 20 5 5 41 6 23 23 23 ...
```

```r
head(OriginalBreweryData)
```

```
##   Brew_ID                      Name          City State
## 1       1        NorthGate Brewing    Minneapolis    MN
## 2       2 Against the Grain Brewery    Louisville    KY
## 3       3  Jack's Abby Craft Lagers    Framingham    MA
## 4       4 Mike Hess Brewing Company     San Diego    CA
## 5       5   Fort Point Beer Company San Francisco    CA
## 6       6     COAST Brewing Company    Charleston    SC
```

```r
tail(OriginalBreweryData)
```

```
##     Brew_ID                          Name          City State
## 553     553         Mickey Finn's Brewery  Libertyville    IL
## 554     554           Covington Brewhouse     Covington    LA
## 555     555               Dave's Brewfarm        Wilson    WI
## 556     556         Ukiah Brewing Company         Ukiah    CA
## 557     557       Butternuts Beer and Ale Garrattsville    NY
## 558     558 Sleeping Lady Brewing Company     Anchorage    AK
```

## Beers

The Beers dataset contains data about US Craft beers, including a unique identifier, name, alcohol by volume, international bitterness units, brewery identifier, style and ounces of beer.
The following code reads in the original Beers.csv dataset and displays summary information about the dataset


```r
## source(file="testinfo/Analysis/LoadBeersFile.R",print.eval=TRUE)
## this makefile is "LoadBeersFile.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  load the raw data from "beer.csv" file stored in the "/testinfo/DATA" folder of the working directory (Rproject folder) 
## assign the contents of the file to a dataframe called "OriginalBeersData"
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# read in the BeersData
filename=paste(DataPath,"Beers.csv",sep="")
OriginalBeersData<-read.csv(filename,sep=",",header=TRUE)
# display sample data for data checking
class(OriginalBeersData)
```

```
## [1] "data.frame"
```

```r
str(OriginalBeersData)
```

```
## 'data.frame':	2410 obs. of  7 variables:
##  $ Name      : Factor w/ 2305 levels "#001 Golden Amber Lager",..: 1638 577 1705 1842 1819 268 1160 758 1093 486 ...
##  $ Beer_ID   : int  1436 2265 2264 2263 2262 2261 2260 2259 2258 2131 ...
##  $ ABV       : num  0.05 0.066 0.071 0.09 0.075 0.077 0.045 0.065 0.055 0.086 ...
##  $ IBU       : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ Brewery_id: int  409 178 178 178 178 178 178 178 178 178 ...
##  $ Style     : Factor w/ 100 levels "","Abbey Single Ale",..: 19 18 16 12 16 80 18 22 18 12 ...
##  $ Ounces    : num  12 12 12 12 12 12 12 12 12 12 ...
```

```r
head(OriginalBeersData)
```

```
##                  Name Beer_ID   ABV IBU Brewery_id
## 1            Pub Beer    1436 0.050  NA        409
## 2         Devil's Cup    2265 0.066  NA        178
## 3 Rise of the Phoenix    2264 0.071  NA        178
## 4            Sinister    2263 0.090  NA        178
## 5       Sex and Candy    2262 0.075  NA        178
## 6        Black Exodus    2261 0.077  NA        178
##                            Style Ounces
## 1            American Pale Lager     12
## 2        American Pale Ale (APA)     12
## 3                   American IPA     12
## 4 American Double / Imperial IPA     12
## 5                   American IPA     12
## 6                  Oatmeal Stout     12
```

```r
tail(OriginalBeersData)
```

```
##                             Name Beer_ID   ABV IBU Brewery_id
## 2405 Rocky Mountain Oyster Stout    1035 0.075  NA        425
## 2406                   Belgorado     928 0.067  45        425
## 2407               Rail Yard Ale     807 0.052  NA        425
## 2408             B3K Black Lager     620 0.055  NA        425
## 2409         Silverback Pale Ale     145 0.055  40        425
## 2410        Rail Yard Ale (2009)      84 0.052  NA        425
##                         Style Ounces
## 2405           American Stout     12
## 2406              Belgian IPA     12
## 2407 American Amber / Red Ale     12
## 2408              Schwarzbier     12
## 2409  American Pale Ale (APA)     12
## 2410 American Amber / Red Ale     12
```

## Questions (from Conference Organizers)

#### 1.  How many breweries are present in each state?

A table with the number of breweries for the 50 states and district of columbia ("DC") follows:


```r
## source(file="testinfo/Analysis/BreweriesPerStateFile.R",print.eval = TRUE)
## this makefile is "BreweriesPerStateFile.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  compute and display the number of Breweries Per State 
## Assumes that OriginalBreweryData is already in the workspace
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# Use the Summary function to count the breweries per State
BreweriesPerState<-data.frame(summary(OriginalBreweryData$State,maxsum=51))
BreweriesPerState<-data.frame(BreweriesPerState,State=row.names(BreweriesPerState))
names(BreweriesPerState)[1]<-"No. Of Breweries"
row.names(BreweriesPerState)<-NULL
BreweriesPerState
```

```
##    No. Of Breweries State
## 1                 7    AK
## 2                 3    AL
## 3                 2    AR
## 4                11    AZ
## 5                39    CA
## 6                47    CO
## 7                 8    CT
## 8                 1    DC
## 9                 2    DE
## 10               15    FL
## 11                7    GA
## 12                4    HI
## 13                5    IA
## 14                5    ID
## 15               18    IL
## 16               22    IN
## 17                3    KS
## 18                4    KY
## 19                5    LA
## 20               23    MA
## 21                7    MD
## 22                9    ME
## 23               32    MI
## 24               12    MN
## 25                9    MO
## 26                2    MS
## 27                9    MT
## 28               19    NC
## 29                1    ND
## 30                5    NE
## 31                3    NH
## 32                3    NJ
## 33                4    NM
## 34                2    NV
## 35               16    NY
## 36               15    OH
## 37                6    OK
## 38               29    OR
## 39               25    PA
## 40                5    RI
## 41                4    SC
## 42                1    SD
## 43                3    TN
## 44               28    TX
## 45                4    UT
## 46               16    VA
## 47               10    VT
## 48               23    WA
## 49               20    WI
## 50                1    WV
## 51                4    WY
```

#### 2.  Merge the two datasets together by brewery id.   Print the first 6 and last 6 observations to check the merged file.

Before merging, we'll clean up the data a bit, so both data frames use the same variable (Brewery_id) for the brewery identifier and to distinguish between brewery names and beers names in the merged table.  

The first 6 and last 6 observations of the cleaned data are displayed first, followed by the same information for the merged data, as requested.


```r
## source(file="testinfo/Analysis/CleanAndMergeDataFrames.R", print.eval = TRUE)
## this makefile is "CleanAndMergeDataFrames.R" 
## location: "/testinfo/ANALYSIS" folder
## purposes: make working copies of the original data  
##           align the brewery identifiers in each table 
##           clarify the "Name" column in each table
## assumes that OriginalBreweryData and OriginalBeersData are already in the workspace
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
## make working copies of the original data
BreweryData<-OriginalBreweryData
BeersData<-OriginalBeersData
## align brewery identifiers and clarify "Names" columns
library(plyr)
BreweryData<-rename(BreweryData,c("Brew_ID"="Brewery_id","Name"="Brewery_Name"))
head(BreweryData)
```

```
##   Brewery_id              Brewery_Name          City State
## 1          1        NorthGate Brewing    Minneapolis    MN
## 2          2 Against the Grain Brewery    Louisville    KY
## 3          3  Jack's Abby Craft Lagers    Framingham    MA
## 4          4 Mike Hess Brewing Company     San Diego    CA
## 5          5   Fort Point Beer Company San Francisco    CA
## 6          6     COAST Brewing Company    Charleston    SC
```

```r
BeersData<-rename(BeersData,c("Name"="Beer_Name"))
head(BeersData)
```

```
##             Beer_Name Beer_ID   ABV IBU Brewery_id
## 1            Pub Beer    1436 0.050  NA        409
## 2         Devil's Cup    2265 0.066  NA        178
## 3 Rise of the Phoenix    2264 0.071  NA        178
## 4            Sinister    2263 0.090  NA        178
## 5       Sex and Candy    2262 0.075  NA        178
## 6        Black Exodus    2261 0.077  NA        178
##                            Style Ounces
## 1            American Pale Lager     12
## 2        American Pale Ale (APA)     12
## 3                   American IPA     12
## 4 American Double / Imperial IPA     12
## 5                   American IPA     12
## 6                  Oatmeal Stout     12
```

```r
# merge the cleaned data on Brewery_id
BreweryAndBeersData<-merge(BreweryData,BeersData,all=TRUE,sort=TRUE)
head(BreweryAndBeersData)
```

```
##   Brewery_id       Brewery_Name        City State     Beer_Name Beer_ID
## 1          1 NorthGate Brewing  Minneapolis    MN       Pumpion    2689
## 2          1 NorthGate Brewing  Minneapolis    MN    Stronghold    2688
## 3          1 NorthGate Brewing  Minneapolis    MN   Parapet ESB    2687
## 4          1 NorthGate Brewing  Minneapolis    MN  Get Together    2692
## 5          1 NorthGate Brewing  Minneapolis    MN Maggie's Leap    2691
## 6          1 NorthGate Brewing  Minneapolis    MN    Wall's End    2690
##     ABV IBU                               Style Ounces
## 1 0.060  38                         Pumpkin Ale     16
## 2 0.060  25                     American Porter     16
## 3 0.056  47 Extra Special / Strong Bitter (ESB)     16
## 4 0.045  50                        American IPA     16
## 5 0.049  26                  Milk / Sweet Stout     16
## 6 0.048  19                   English Brown Ale     16
```

```r
tail(BreweryAndBeersData)
```

```
##      Brewery_id                  Brewery_Name          City State
## 2405        556         Ukiah Brewing Company         Ukiah    CA
## 2406        557       Butternuts Beer and Ale Garrattsville    NY
## 2407        557       Butternuts Beer and Ale Garrattsville    NY
## 2408        557       Butternuts Beer and Ale Garrattsville    NY
## 2409        557       Butternuts Beer and Ale Garrattsville    NY
## 2410        558 Sleeping Lady Brewing Company     Anchorage    AK
##                      Beer_Name Beer_ID   ABV IBU                   Style
## 2405             Pilsner Ukiah      98 0.055  NA         German Pilsener
## 2406         Porkslap Pale Ale      49 0.043  NA American Pale Ale (APA)
## 2407           Snapperhead IPA      51 0.068  NA            American IPA
## 2408         Moo Thunder Stout      50 0.049  NA      Milk / Sweet Stout
## 2409  Heinnieweisse Weissebier      52 0.049  NA              Hefeweizen
## 2410 Urban Wilderness Pale Ale      30 0.049  NA        English Pale Ale
##      Ounces
## 2405     12
## 2406     12
## 2407     12
## 2408     12
## 2409     12
## 2410     12
```

#### 3.  Report the number of missing values in each column of the merged dataset.

There are 62 missing values for alcohol by volume and 1005 missing values for international bitterness units.  These missing values will be removed from further analysis although they remain in the dataframe.


```r
## source(file="testinfo/Analysis/FindMissingValues.R",print.eval = TRUE)
## this makefile is "FindMissingValues.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  find and report the number of missing values in each column of the BreweryAndBeersData dataframe 
## assumes BreweryAndBeersData already exists in the workspace
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
## find missing values in each column of the merged data
B<-BreweryAndBeersData
MV<-"Missing Values"
N<-sapply(B,function(x) sum(is.na(x)))
MV[1]
```

```
## [1] "Missing Values"
```

```r
N[N>0]
```

```
##  ABV  IBU 
##   62 1005
```

#### 4.  Compute the median alcohol content (mabv) and median international bitterness units (mibu) for each state.  Provide a bar chart for comparison.

The table below lists mabv and mibu by state.  Note that missing table values for abv and ibu by type of beer are ignored for the purpose of preparing this table.  Separate bar charts are provided for alcohol content and bitterness.  The bars for states are in the same order as the table.  The plots may also be found in the subdirectory "BeersAndBreweriesMaster_files".


```r
## source(file="testinfo/Analysis/ComputeAndPlotMedians.R",print.eval = TRUE)
## this makefile is "ComputeAndPlotMedians.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  Compute the median alcohol content and international bitterness units for each state.  Provide a bar chart for comparison.
## Assumes that the dataframe BreweryAndBeersData is already in the workspace
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# prepare data vectors
AlcoholContent<-BreweryAndBeersData$ABV
IbuContent<-BreweryAndBeersData$IBU
State<-BreweryAndBeersData$State
state=BreweriesPerState$State
mabv<-numeric(51)
maxabv<-numeric(51)
mibu<-numeric(51)
maxibu<-numeric(51)
for (i in 1:51) {
    s=state[i]
    mabv[i]=median(AlcoholContent[state=s],na.rm=TRUE)
    maxabv[i]=max(AlcoholContent[state=s]) # for use in question 5
    mibu[i]=median(IbuContent[state=s],na.rm=TRUE)
    maxibu[i]=max(IbuContent[state=s]) # for use in question 5
    }
MediansByState=data.frame(mabv,mibu,state)
MediansByState
```

```
##     mabv mibu state
## 1  0.060   38    AK
## 2  0.060   25    AL
## 3  0.056   47    AR
## 4  0.045   50    AZ
## 5  0.049   26    CA
## 6  0.048   19    CO
## 7  0.042   42    CT
## 8  0.080   68    DC
## 9  0.125   80    DE
## 10 0.077   25    FL
## 11 0.055   17    GA
## 12 0.050   25    HI
## 13 0.066   21    IA
## 14 0.040   13    ID
## 15 0.060   65    IL
## 16 0.050   20    IN
## 17 0.076   68    KS
## 18 0.051   38    KY
## 19 0.065   NA    LA
## 20 0.072   80    MA
## 21 0.048   15    MD
## 22 0.067   65    ME
## 23 0.049   45    MI
## 24 0.052   18    MN
## 25 0.060   24    MO
## 26 0.075   85    MS
## 27 0.080  100    MT
## 28 0.058   28    NC
## 29 0.080  100    ND
## 30 0.063   30    NE
## 31 0.063   42    NH
## 32 0.056   16    NJ
## 33 0.046   17    NM
## 34 0.047   19    NV
## 35 0.062   NA    NY
## 36 0.060   NA    OH
## 37 0.048   NA    OK
## 38 0.093   NA    OR
## 39 0.097   NA    PA
## 40 0.077   NA    RI
## 41 0.071   NA    SC
## 42 0.050   NA    SD
## 43 0.061   NA    TN
## 44 0.095   75    TX
## 45 0.083   NA    UT
## 46 0.071   NA    VA
## 47 0.087   NA    VT
## 48 0.073   NA    WA
## 49 0.050   NA    WI
## 50 0.057   NA    WV
## 51 0.070   NA    WY
```

```r
# prepare a side by side bar plot of mabv, mibu using state for labels
count1<-as.vector(mabv)
count2<-as.vector(mibu)
barplot(count1, main="Median Alchohol Content by State")
```

![](BeersAndBreweriesMaster_files/figure-html/q4-1.png)<!-- -->

```r
barplot(count2, main="Median Bitterness by State")
```

![](BeersAndBreweriesMaster_files/figure-html/q4-2.png)<!-- -->

#### 5.  Which state has the maximum alcoholic beer and which state has the most bitter beer?

Delaware has the most alcoholic beer, at 12.5% alcohol by volume.  

Montana has the bitterest beer, at 100 IBU units. 


```r
## source(file="Testinfo/Analysis/MaximumStatFile.R")
## this makefile is "MaximumStatFile.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  find the state with the maximum alcohol content and the state with the maximum international bitterness units for each state.  
## Assumes that the dataframe MediansByState and related variables are already in the workspace
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# Identify the state and value of the maximum abv and maximum ibu
shabv<-" "
gmaxabv<-0
shibu<-" "
gmaxibu<-0
for (i in 1:51) {
    s=state[i]
    if (!is.na(maxabv[i]) & maxabv[i]>gmaxabv) {gmaxabv=mabv[i]
       shabv=s}
    if (!is.na(maxibu[i]) & maxibu[i]>gmaxibu) {gmaxibu=mibu[i]
       shibu=s}
}
#display results
print(paste(shabv," has the maximum alcohol content of ", gmaxabv))
```

```
## [1] " DE  has the maximum alcohol content of  0.125"
```

```r
print(paste(shibu," has the maximum bitterness units of ", gmaxibu))
```

```
## [1] " MT  has the maximum bitterness units of  100"
```

#### 6.  Summarize statistics for Alcohol by Volume.

As shown below, nationwide data for AlcoholByVolume are in the range from [.001 to .128]
Measures of center:
    Median: .056
    Mean:   .05977
Interquartile range = [.05, .067]

The distribution is somewhat right-skewed with the upper-quartile including points in the range from [.067, .128]   
Drawing any conclusions from this data would benefit from identifying possible outliers or data errors, 


```r
## source(file="Testinfo/Analysis/AlcoholByVolumeSummaryFile.R")
## this makefile is "AlcoholByVolumeSummaryFile.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose:  compute and display the summary statistics on alcohol by volume 
## Assumes that the "Alchohol Content" vector (created by "ComputeAndPlotMedians.R") is already in the workspace
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# Use the Summary function
ABVSummary<-(summary(AlcoholContent))
print(" NATIONAL SUMMARY STATISTICS FOR ALCOHOL BY VOLUME")
```

```
## [1] " NATIONAL SUMMARY STATISTICS FOR ALCOHOL BY VOLUME"
```

```r
print(ABVSummary)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
## 0.00100 0.05000 0.05600 0.05977 0.06700 0.12800      62
```

#### 7.  Is there a relationship between the bitterness of the beer and its alcohol content?   Provide a scatter plot.

The points in the scatterplot form a cloud, indicating that a relationship between the bitterness of the beer and its alcohol content is unlikely.


```r
## source(file="Testinfo/Analysis/PrepareScatterplotFile.R")
## copied code inline from source to meet requirement that code is in the HTML
library(ggplot2)
qplot(AlcoholContent,IbuContent,geom="point",main="Scatterplot of Alcohol Content vs International Bitterness Units",xlab="ABV",ylab="IBU")
```

```
## Warning: Removed 1005 rows containing missing values (geom_point).
```

![](BeersAndBreweriesMaster_files/figure-html/q7-1.png)<!-- -->

## Conclusion

The cleaned and merged data may be found in the form of .cvs files in the "Testinfo/DATA" folder.   As noted in the answer to question 6, it would be helpful to speak with an expert in the collection of ABV data to investigate possible outliers or data errors.  Additionally, I look forward to reviewing these results with the convention organizers to further explore their requirements for the presentation of this data at their conference next year.


```r
## source(file="Testinfo/Analysis/OutputCleanedDataFile.R")
## this makefile is "OutputCleanedDataFile.R" 
## location: "/testinfo/ANALYSIS" folder
## purpose: to save the cleaned data in the form of .csv files:  
##  store the BreweryAndBeersData dataframe as "BreweryAndBeers.csv" in the "/testinfo/DATA" folder of the working directory (Rproject folder) 
##  store the BreweriesPerState dataframe as "BreweriesPerState.csv" in the "/testinfo/DATA" folder of the working directory (Rproject folder) 
##  store the cleaned BreweriesData dataframe as "BreweryData.csv" in the "/testinfo/DATA" folder of the working directory (Rproject folder)
##  store the cleaned BeersData dataframe as "BeersData.csv" in the "/testinfo/DATA" folder of the working directory (Rproject folder)
## copied code inline from source to meet requirement that code is in the HTML
AnalysisPath<-"testinfo/ANALYSIS/"
DataPath<-"testinfo/DATA/"
# filenames
filename1=paste(DataPath,"BeersData.csv",sep="")
write.csv(BeersData,file=filename1,row.names=TRUE)
filename2=paste(DataPath,"BreweryData.csv",sep="")
write.csv(BreweryData,file=filename2,row.names=TRUE)
filename3=paste(DataPath,"BreweryAndBeersData.csv",sep="")
write.csv(BreweryAndBeersData,file=filename3,row.names=TRUE)
filename4=paste(DataPath,"BreweriesPerState.csv",sep="")
write.csv(BreweriesPerState,file=filename4,row.names=TRUE)
```


For more information on the conference, please see:  https://www.craftbrewersconference.com/

