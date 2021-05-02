# Time Series Analysis: Detecting Anomalies in Turbidity of New York Drinking Water
![R](https://img.shields.io/badge/Made%20With-R-yellow?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgdmlld0JveD0iMCAwIDY0IDY0IiB3aWR0aD0iNTEyIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxwYXRoIGQ9Ik0zOC4zNCA0OC43M2wzLjA0IDQuODdjLTIuOTQuOTEtNi4xIDEuNC05LjM4IDEuNHYtNi4xMmEyNS42OCAyNS42OCAwIDAwNi4zMy0uMTV6IiBmaWxsPSIjODM2MGY0Ii8+PHBhdGggZD0iTTYxIDI5YzAgOC45LTQuOTkgMTYuNzYtMTIuNiAyMS40NGwtMS40OS0yLjM4Yy0uMzQtLjU0LS43MS0xLjA2LTEuMTEtMS41NiA2LjctMy4yIDExLjItOS4xNyAxMS4yLTE2QzU3IDIwLjI4IDQ2LjkzIDEyIDM0LjUgMTJTMTIgMjAuMjggMTIgMzAuNWMwIDcuMSA0Ljg2IDEzLjI3IDEyIDE2LjM3djcuMTJDMTEuODcgNTAuODkgMyA0MC44NyAzIDI5IDMgMTQuNjQgMTUuOTggMyAzMiAzczI5IDExLjY0IDI5IDI2eiIgZmlsbD0iIzgzNjBmNCIvPjxwYXRoIGQ9Ik00OC40IDUwLjQ0TDU1IDYxaC05bC04LjgyLTE0LjEyYTQuMDIgNC4wMiAwIDAwLTMuNC0xLjg4SDMydjE1YTEgMSAwIDAxLTEgMWgtNmExIDEgMCAwMS0xLTFWMjBhMSAxIDAgMDExLTFoMTdhMTEgMTEgMCAwMTExIDExdjJhMTAuOTcgMTAuOTcgMCAwMS0xMSAxMSAxNi42NyAxNi42NyAwIDAxNC45MSA1LjA2ek00NSAzMmE1LjAyIDUuMDIgMCAwMC01LTVoLTh2MTBoOGE1IDUgMCAwMDUtNXoiIGZpbGw9IiM2NTk5ZWQiLz48ZyBmaWxsPSIjMWExYTFhIj48cGF0aCBkPSJNNDYgMzJhNiA2IDAgMDAtNi02aC04YTEgMSAwIDAwLTEgMXYxMGExIDEgMCAwMDEgMWg4YTYgNiAwIDAwNi02em0tNiA0aC03di04aDdhNCA0IDAgMDEwIDh6Ii8+PHBhdGggZD0iTTMyIDJDMTUuNDYgMiAyIDE0LjExIDIgMjljMCAxMS43NyA4LjYgMjIuMjQgMjEgMjUuNzRWNjBjMCAxLjEuOSAyIDIgMmg2YTIgMiAwIDAwMi0ydi00LjA0YTMyLjYgMzIuNiAwIDAwNy45Mi0xLjJsNC4yMyA2Ljc3Yy4xOC4zLjUuNDcuODUuNDdoOWExIDEgMCAwMC44NS0xLjUzbC02LjA4LTkuNzNDNTcuNDQgNDUuNjYgNjIgMzcuNiA2MiAyOSA2MiAxNC4xMSA0OC41NCAyIDMyIDJ6bS05IDE4djI1LjI5Yy02LjItMy4yLTEwLTguNzUtMTAtMTQuNzlDMTMgMjAuODUgMjIuNjQgMTMgMzQuNSAxM1M1NiAyMC44NSA1NiAzMC41YzAgNS45Ni0zLjggMTEuNTQtOS45NSAxNC43NC0uNDYtLjUzLS45Ni0xLjA0LTEuNDgtMS41MkExMi4wMiAxMi4wMiAwIDAwNTQgMzJ2LTJjMC02LjYyLTUuMzgtMTItMTItMTJIMjVhMiAyIDAgMDAtMiAyem0xMCAzMy45NnYtNGEyNi42OCAyNi42OCAwIDAwNC44MS0uMTdsMiAzLjJjLTIuMi41Ny00LjQ5LjktNi44MS45N3ptMC02LjAyVjQ2aC43OGMxLjA0IDAgMiAuNTMgMi41NSAxLjQxbC4zMS41Yy0xLjIuMS0yLjQzLjEtMy42NC4wM3pNNDYuNTUgNjBsLTguNTMtMTMuNjVBNC45NyA0Ljk3IDAgMDAzMy43OCA0NEgzMmExIDEgMCAwMC0xIDF2MTVoLTZWMjBoMTdjNS41MSAwIDEwIDQuNDkgMTAgMTB2MmMwIDUuNTEtNC40OSAxMC0xMCAxMGExIDEgMCAwMC0uNTUgMS44MyAxNS42NCAxNS42NCAwIDAxNC42MSA0Ljc2TDUzLjIgNjB6bTIuMTYtMTAuOTZsLS45NS0xLjUxLS40Ni0uNjhDNTMuOTMgNDMuMjcgNTggMzcuMTEgNTggMzAuNSA1OCAxOS43NSA0Ny40NiAxMSAzNC41IDExUzExIDE5Ljc1IDExIDMwLjVjMCA3LjEgNC41OCAxMy41NSAxMiAxN3Y1LjE1QzExLjc2IDQ5LjI1IDQgMzkuNyA0IDI5IDQgMTUuMjEgMTYuNTYgNCAzMiA0czI4IDExLjIxIDI4IDI1YzAgNy45Mi00LjIgMTUuMzMtMTEuMyAyMC4wNHoiLz48L2c+PC9zdmc+)
![Outlier](https://img.shields.io/badge/Anomalies-Detection-red?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMiA5OCA5OCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiPjxsaW5lYXJHcmFkaWVudCBpZD0iYSIgZ3JhZGllbnRVbml0cz0idXNlclNwYWNlT25Vc2UiIHgxPSIyNi4xNSIgeTE9IjcuMjUiIHgyPSIyNi4xNSIgeTI9Ijk0LjUxIj48c3RvcCBvZmZzZXQ9IjAiIHN0b3AtY29sb3I9IiMwMGVmZDEiLz48c3RvcCBvZmZzZXQ9IjEiIHN0b3AtY29sb3I9IiMwMGFjZWEiLz48L2xpbmVhckdyYWRpZW50PjxwYXRoIGQ9Ik0yNi42IDI4LjhjLTQuMyA0LjMtNi41IDEwLjQtNS45IDE2LjZhMy4xIDMuMSAwIDAwMyAyLjdoLjNjMS42LS4yIDIuOS0xLjYgMi43LTMuMy0uNC00LjQgMS4xLTguNyA0LjEtMTEuOGEyLjkgMi45IDAgMDAwLTQuMmMtMS4yLTEtMy0xLjEtNC4yIDB6IiBmaWxsPSJ1cmwoI2EpIi8+PGxpbmVhckdyYWRpZW50IGlkPSJiIiBncmFkaWVudFVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgeDE9IjQ5IiB5MT0iNy4yNSIgeDI9IjQ5IiB5Mj0iOTQuNTEiPjxzdG9wIG9mZnNldD0iMCIgc3RvcC1jb2xvcj0iIzAwZWZkMSIvPjxzdG9wIG9mZnNldD0iMSIgc3RvcC1jb2xvcj0iIzAwYWNlYSIvPjwvbGluZWFyR3JhZGllbnQ+PHBhdGggZD0iTTg4LjcgODYuNUw2OSA2Ni43YzUtNiA4LTEzLjYgOC0yMiAwLTE4LjktMTUuNC0zNC4zLTM0LjMtMzQuM1M4LjQgMjUuOCA4LjQgNDQuN0M4LjQgNjMuNSAyMy44IDc5IDQyLjcgNzljOC40IDAgMTYuMS0zIDIyLThsMTkuOCAxOS44Yy42LjYgMS40LjkgMi4xLjkuNyAwIDEuNS0uMyAyLjEtLjkgMS4yLTEuMyAxLjItMy4zIDAtNC4zem0tMjUuOC0yMmwtLjIuMi0uMi4yYy01LjEgNS0xMi4xIDguMS0xOS44IDguMS0xNS42IDAtMjguMy0xMi43LTI4LjMtMjguMyAwLTE1LjYgMTIuNy0yOC4zIDI4LjMtMjguM0M1OC4zIDE2LjMgNzEgMjkgNzEgNDQuN2MwIDcuNi0zLjEgMTQuNi04LjEgMTkuOHoiIGZpbGw9InVybCgjYikiLz48L3N2Zz4=)
![Time](https://img.shields.io/badge/Time%20Series-Analysis-blue?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgd2lkdGg9IjUxMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNMjU2IDBMMTI4IDI1NmwxMjggMjU2YzE0MS4zOCAwIDI1Ni0xMTQuNjEgMjU2LTI1NlMzOTcuMzkgMCAyNTYgMHoiIGZpbGw9IiMyOGFiZmEiLz48cGF0aCBkPSJNMCAyNTZjMCAxNDEuMzggMTE0LjYxIDI1NiAyNTYgMjU2VjBDMTE0LjYyIDAgMCAxMTQuNjEgMCAyNTZ6IiBmaWxsPSIjMTRjZmZmIi8+PHBhdGggZD0iTTI1NiA2MGwtOTggMTk2IDk4IDE5NmMxMDguMjUgMCAxOTYtODcuNzUgMTk2LTE5NlMzNjQuMjUgNjAgMjU2IDYweiIgZmlsbD0iI2M0ZjNmZiIvPjxwYXRoIGQ9Ik02MCAyNTZjMCAxMDguMjUgODcuNzUgMTk2IDE5NiAxOTZWNjBDMTQ3Ljc1IDYwIDYwIDE0Ny43NSA2MCAyNTZ6IiBmaWxsPSIjZmZmIi8+PHBhdGggZD0iTTI5OC40MyAyNzcuMjFMMjU2IDIzNC44aC0yMGwyMCA0Mi40MiAyMS4yMSAyMS4yMnoiIGZpbGw9IiMzNDBkNjYiLz48cGF0aCBkPSJNMTcwLjggMTQ5LjU4bC0yMS4yMiAyMS4yMUwyNTYgMjc3LjIxVjIzNC44eiIgZmlsbD0iIzM3M2U5ZiIvPjxwYXRoIGQ9Ik0zNDEuNTYgMTQ5LjIzTDI1NiAyMzQuNzlsLTIwIDQyLjQyaDIwbDEwNi43Ny0xMDYuNzd6IiBmaWxsPSIjMzczZTlmIi8+PHBhdGggZD0iTTIxMy41NyAyNzcuMjFsMjEuMjIgMjEuMjJMMjU2IDI3Ny4yVjIzNC44eiIgZmlsbD0iIzM4NTdiYyIvPjxwYXRoIGQ9Ik0yNzEgOTBoLTE1bC0xMCAxNSAxMCAxNWgxNXoiIGZpbGw9IiMzNDBkNjYiLz48cGF0aCBkPSJNMjQxIDkwaDE1djMwaC0xNXoiIGZpbGw9IiMzNzNlOWYiLz48cGF0aCBkPSJNMjcxIDM5MmgtMTVsLTEwIDE1IDEwIDE1aDE1eiIgZmlsbD0iIzM0MGQ2NiIvPjxwYXRoIGQ9Ik0yNDEgMzkyaDE1djMwaC0xNXpNOTAgMjcxdi0zMGgzMHYzMHoiIGZpbGw9IiMzNzNlOWYiLz48cGF0aCBkPSJNMzkyIDI3MXYtMzBoMzB2MzB6IiBmaWxsPSIjMzQwZDY2Ii8+PC9zdmc+)



## Introduction
This is a time series analysis to detect anomalies/ outliers in New York Drinking Water Quality data available from [here](https://opendata.cityofnewyork.us/). The data consists of the turbidity values, coliform, fluoride and chlorine found at sites in distribution each month. However, there are missing values from certain months depending on the sites. There are 398 unque locations/ sites in the data. Each site presented data of different durations ranging from 43 days to 1673 days. For the purpose of time series analysis, I decided to analyse the data from the site with the longest amount of data. Specifically,I decided to analyse turbidity of the water

## Table of content

- [Background](#background)
- [Data Cleaning](#Data-Cleaning)
- [Exploratory Analysis](#Exploratory-Analysis)
- [`anomalize` package](#anomalize-package)
- [`tsoutliers` package](#tsoutliers-package)
- [What's next?](#What's-next?)
- [Conclusion](#Conclusion)

## Background
[Back to top](#table-of-content)
### What is turbidity?
According to [USGS](https://www.usgs.gov/special-topic/water-science-school/science/turbidity-and-water?qt-science_center_objects=0#qt-science_center_objects), turbidity is the measure of relative clarity of a liquid. It is an optical characteristic of water and is a measurement of the amount of light that is scattered by material in the water when a light is shined through the water sample. Figure here shows the levels of turbidity:

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/turbidity.jpg" alt="Different turbidity levels from low to high">
</p>

[WHO](https://www.who.int/water_sanitation_health/publications/turbidity-information-200217.pdf) maintained that turbidity is an extremely useful indicator that can yield valuable information quickly, relatively cheaply and on an ongoing basis. While the turbidity is aimed to be as low as possible, the target turbidity depends on the stage of the water treatment. In distribution, if the turbidity is >= 4, it indicates possible faults or breaches in the distribution. There are many sources of turbidity; it might be harmless (eg clay, soil) or it could be an indication of the presence of dangeous chemical or biological compounds.

### Objective of project
Here, I presented two different ways to detect outliers in time series in R. Specifically, I'm using `anomalize` and `tsoutliers`. Both R packages to detect outliers in time series. However, both have fundamentally very different basis for outliers and thus different ways to work to detect outliers. I'll go into a bit more details in the respective sections.

## Data Cleaning
[Back to top](#table-of-content)
<details>
    <summary>Data Cleaning (click to expand) </summary>
    
### Missing values
The data needed some cleaning at first. The class for the turbidity was character and so was the Date. After conversion, I decided to take three variables: turbidity, free chlorine and fluoride level at first. However, for the purpose of this project, we'll look only at turbidity. During data cleaning, I realise that some dates were missing and some values for fluoride is missing for some dates. The following chart displays the missing values:

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/Missing_by_date.png" alt="Missing values by date">
</p>

### Imputation of Missing Values
Using fluoride data, I imputed the missing values using different methods. The charts below show some examples. From the graphs, I decided to uses seasonal decomposition to impute the multivariate data as it presents the most visually believable pattern.

<img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/mean.png" width="400"/> <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/spline.png" width="400"/>
<img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/seadec.png" width="400"/> <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/linear.png" width="400"/>

</details>


## Exploratory Analysis
[Back to top](#table-of-content)
### Time Series Plot
Here's the plot of three series. At first glance, I thought chlorine and turbidity had some correlations.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/multi_time_plot.png" alt="Time series plot of the multivariate data">
</p>

### Correlation Plot
I was quite surprised to see that chlorine and turbidity had very weak correlation. 

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/correlation_plot.png" alt="Correlation of the variables">
</p>

### Histogram 
As I decided to look at turbidity, I wanted to see the distribution of the turbidity. From the histogram below, it can be seen that a large majority of it is <1 NTU. However, there are still some >1 NTU and even an entry around 1.5 NTU, which would be an anomaly.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/histogram.png" alt="Histogram of turbidity">
</p>



## `anomalize` package
[Back to top](#table-of-content)

`anomalize` package fundamentally decompose a time series into seasonal, trend and remainder (residuals). The decomposition method it uses are: seasonal decomposition of time series by Loess (STL) and seasonal decomposition by piecewise medians (Twitter). Then, it detects the anomalies using either inter-quantile range (IQR) or eneralized extreme studentized deviation (GESD). 

According to the author:
"STL works very well in circumstances where a long term trend is present. The Loess algorithm typically does a very good job at detecting the trend. However, it circumstances when the seasonal component is more dominant than the trend, Twitter tends to perform better.

The Twitter method works identically to STL for removing the seasonal component. The main difference is in removing the trend, which is performed by removing the median of the data rather than fitting a smoother. The median works well when a long-term trend is less dominant that the short-term seasonal component. This is because the smoother tends to overfit the anomalies."

IQR method basically uses the Q1 and Q3 to calculate IQR. By default, the package sets the limit to be 3xIQR above and below the median. However, it may not be as accurate in detecting anomalies since the high leverage anomalies can skew the centerline (median) of the IQR. GESD progressively eliminates out-liers using a Student’s T-Test comparing the test statistic to a critical value. For information on [GESD](https://www.itl.nist.gov/div898/handbook/eda/section3/eda35h3.htm).

The graphs below shows the outputs when using different decomposition method & different detection method:

<img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/stl_gesd.png" width="400"/> <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/twitter_gesd.png" width="400"/>
<img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/stl_iqr.png" width="400"/> <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/twitter_iqr.png" width="400"/>

From the results above, it can be seen that STL + GESD gives the highest number of anomalies while Twitter + IQR method gave the least. If cleaning of the anomalies is desired, the package also has a function to do that. The anomalize package also has the function to cleaned up outliers by replacing them with seasonal and trend components. 

## `tsoutliers` package
[Back to top](#table-of-content)

According to `tsoutliers`, the different types of outliers include:

- Additive outliers: represents an isolated spike
- Level shifts: abrupt change in mean and could be seasonal (aka Seasonal level shifts)
- Transient change: a spike that takes a while to disappear
- Innovation outliers: a shock in the innovation of the model

The fundamental processes:

- 1) Detection of outliers upon a chosen ARIMA model. Given  an  ARIMA  model  fitted  to  the  data,  outliers  are  detected  and located by checking the significance of all types of outliers at all possible time points.
- 2) Choose and/or refit the ARIMA model including the outliers detected in the previous step and remove those outliers that are not significant in the new fit.

The series is then adjusted for the detected outliers and the stages (1) and (2) are repeated until no more outliers are detected or until a maximum number of iterations is reached.

There is one issue with `tsoutliers`. The model might need some tuning in order to find the best model. Otherwise, it will rush to fit and fit model using approximation when `tso` is run. The output below illustrates what I meant. 

### `tso` with no tuning
`tsoutliers` identified 4 additive outliers without parameter tuning. The blue line shows the adjusted time plot while the red line show the outliers and their effect.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/ts_no_tuning.png" alt="Output of tsoutliers without tuning">
</p>

### `tso` with tuning
Here, `tsoutliers` identified both additive outliers (AO) and innovation outliers (IO). In the upper graph, the blue line represents the time plot adjusted for the effect outliers while the grey line shows the original time plot. In the lower graph, we could see that innovation outliers tend to have a longer impact on the rest of the series.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/ts_with_tuning.png" alt="Output of tsoutliers with tuning">
</p>

## What's next?
[Back to top](#table-of-content)

Deciding what to do with outliers has always been an issue in statistics. The difference here and matrix data is the temporal element. Outliers in matrices could be discarded (if that's the best option) while discarding an outlier in time series would create a temporal gap. Therefore, discretion should be used when it comes deciding what to do with it. The data was collected from different water distribution sites. According to [WHO](https://www.who.int/water_sanitation_health/publications/turbidity-information-200217.pdf), distribution comes after treatment and turbidity could indicate either of the following:

- intrusion of soils and sewage through main breaks
- External contamination from backflow or cross connections
- Resuspension of accumulated silts and sediments, or detachment of corrosion chemicals and scales 
- Detachment of biofilms 

Therefore, in order to further explore the outliers, I'd check the sensors to ensure that there is no malfunction. The mentioned factors should also be checked to analyse the possible correlations which might give a hint as to the reason of the outliers. 

Should one decide to use adjusted data for modelling, both `anomalize` and `tsoutliers` do return adjusted time series that could be use to fit a model. `anomalize` will substitute the outliers with the decompsoed seasonal and trend components of that particular point in time with `clean_anomalies`. `tsoutliers` return `yadj` which is the result of outliers included as regressors in a model, weighted by the estimated coefficients and removed from the original series. See [here](https://stats.stackexchange.com/questions/104882/detecting-outliers-in-time-series-ls-ao-tc-using-tsoutliers-package-in-r-how) for more information. Here is an example of 30 day-forecast using `yadj` from `tsoutliers` fitted with ARIMA(4,1,1). Note that this is not the best model as evident from the wide prediction interval and the forecast approximates the mean the longer it is.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/30_day_forecast_yadj_tsoutliers.png" alt="30 day-forecast using yadj from `tsoutliers`">
</p>

## Conclusion
[Back to top](#table-of-content)

Fundamentally, `tsoutliers` works differently from `anomalize`. It applies model to the data, test for the different types of outliers and then refit and retest while the latter decompose and detect outliers. `tsoutliers` is useful in detecting the different types of outliers and visualising the possible downstream effects. After detection, there is still the question of what to do with it. Outliers could be discarded or substituted and both packages could give adjusted series for modelling. However, using the adjusted y must be cautioned as removing outliers might give incorrect prediction interval. On the other hand, not removing outlier will present skewed distribution and thereby, possibly wrong conclusion. In short, discretion is needed when it comes to the decision about what to do with outliers. Check out this [post](https://stats.stackexchange.com/questions/69874/how-to-correct-outliers-once-detected-for-time-series-data-forecasting) for more information. These are only two new packages in R for detection. There are more packages as well as detection methods available such as DBSCAN, k-means etc. Get in touch if you have ideas to share!


<ins>Attribution</ins>
<div>R icon made by <a href="https://www.flaticon.com/authors/becris" title="Becris">Becris</a> from <a href="https://www.flaticon.com/" title="Flaticon">Flaticon</a></div>
<div>Maginifying glass icon made by <a href="" title="Kiranshastry">Kiranshastry</a> from <a href="https://www.flaticon.com/" title="Flaticon">Flaticon</a></div>
<div>Clock icon made by <a href="https://www.freepik.com" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">Flaticon</a></div>
Turbidity image is from [Marshall Pumps](https://www.marshallpumps.co.uk/turbidity/)
