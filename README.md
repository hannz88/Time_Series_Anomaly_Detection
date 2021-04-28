# Time Series Analysis: Detecting Anomalies in Turbidity of New York Drinking Water
![R](https://img.shields.io/badge/Made%20With-R-yellow?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgdmlld0JveD0iMCAwIDY0IDY0IiB3aWR0aD0iNTEyIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxwYXRoIGQ9Ik0zOC4zNCA0OC43M2wzLjA0IDQuODdjLTIuOTQuOTEtNi4xIDEuNC05LjM4IDEuNHYtNi4xMmEyNS42OCAyNS42OCAwIDAwNi4zMy0uMTV6IiBmaWxsPSIjODM2MGY0Ii8+PHBhdGggZD0iTTYxIDI5YzAgOC45LTQuOTkgMTYuNzYtMTIuNiAyMS40NGwtMS40OS0yLjM4Yy0uMzQtLjU0LS43MS0xLjA2LTEuMTEtMS41NiA2LjctMy4yIDExLjItOS4xNyAxMS4yLTE2QzU3IDIwLjI4IDQ2LjkzIDEyIDM0LjUgMTJTMTIgMjAuMjggMTIgMzAuNWMwIDcuMSA0Ljg2IDEzLjI3IDEyIDE2LjM3djcuMTJDMTEuODcgNTAuODkgMyA0MC44NyAzIDI5IDMgMTQuNjQgMTUuOTggMyAzMiAzczI5IDExLjY0IDI5IDI2eiIgZmlsbD0iIzgzNjBmNCIvPjxwYXRoIGQ9Ik00OC40IDUwLjQ0TDU1IDYxaC05bC04LjgyLTE0LjEyYTQuMDIgNC4wMiAwIDAwLTMuNC0xLjg4SDMydjE1YTEgMSAwIDAxLTEgMWgtNmExIDEgMCAwMS0xLTFWMjBhMSAxIDAgMDExLTFoMTdhMTEgMTEgMCAwMTExIDExdjJhMTAuOTcgMTAuOTcgMCAwMS0xMSAxMSAxNi42NyAxNi42NyAwIDAxNC45MSA1LjA2ek00NSAzMmE1LjAyIDUuMDIgMCAwMC01LTVoLTh2MTBoOGE1IDUgMCAwMDUtNXoiIGZpbGw9IiM2NTk5ZWQiLz48ZyBmaWxsPSIjMWExYTFhIj48cGF0aCBkPSJNNDYgMzJhNiA2IDAgMDAtNi02aC04YTEgMSAwIDAwLTEgMXYxMGExIDEgMCAwMDEgMWg4YTYgNiAwIDAwNi02em0tNiA0aC03di04aDdhNCA0IDAgMDEwIDh6Ii8+PHBhdGggZD0iTTMyIDJDMTUuNDYgMiAyIDE0LjExIDIgMjljMCAxMS43NyA4LjYgMjIuMjQgMjEgMjUuNzRWNjBjMCAxLjEuOSAyIDIgMmg2YTIgMiAwIDAwMi0ydi00LjA0YTMyLjYgMzIuNiAwIDAwNy45Mi0xLjJsNC4yMyA2Ljc3Yy4xOC4zLjUuNDcuODUuNDdoOWExIDEgMCAwMC44NS0xLjUzbC02LjA4LTkuNzNDNTcuNDQgNDUuNjYgNjIgMzcuNiA2MiAyOSA2MiAxNC4xMSA0OC41NCAyIDMyIDJ6bS05IDE4djI1LjI5Yy02LjItMy4yLTEwLTguNzUtMTAtMTQuNzlDMTMgMjAuODUgMjIuNjQgMTMgMzQuNSAxM1M1NiAyMC44NSA1NiAzMC41YzAgNS45Ni0zLjggMTEuNTQtOS45NSAxNC43NC0uNDYtLjUzLS45Ni0xLjA0LTEuNDgtMS41MkExMi4wMiAxMi4wMiAwIDAwNTQgMzJ2LTJjMC02LjYyLTUuMzgtMTItMTItMTJIMjVhMiAyIDAgMDAtMiAyem0xMCAzMy45NnYtNGEyNi42OCAyNi42OCAwIDAwNC44MS0uMTdsMiAzLjJjLTIuMi41Ny00LjQ5LjktNi44MS45N3ptMC02LjAyVjQ2aC43OGMxLjA0IDAgMiAuNTMgMi41NSAxLjQxbC4zMS41Yy0xLjIuMS0yLjQzLjEtMy42NC4wM3pNNDYuNTUgNjBsLTguNTMtMTMuNjVBNC45NyA0Ljk3IDAgMDAzMy43OCA0NEgzMmExIDEgMCAwMC0xIDF2MTVoLTZWMjBoMTdjNS41MSAwIDEwIDQuNDkgMTAgMTB2MmMwIDUuNTEtNC40OSAxMC0xMCAxMGExIDEgMCAwMC0uNTUgMS44MyAxNS42NCAxNS42NCAwIDAxNC42MSA0Ljc2TDUzLjIgNjB6bTIuMTYtMTAuOTZsLS45NS0xLjUxLS40Ni0uNjhDNTMuOTMgNDMuMjcgNTggMzcuMTEgNTggMzAuNSA1OCAxOS43NSA0Ny40NiAxMSAzNC41IDExUzExIDE5Ljc1IDExIDMwLjVjMCA3LjEgNC41OCAxMy41NSAxMiAxN3Y1LjE1QzExLjc2IDQ5LjI1IDQgMzkuNyA0IDI5IDQgMTUuMjEgMTYuNTYgNCAzMiA0czI4IDExLjIxIDI4IDI1YzAgNy45Mi00LjIgMTUuMzMtMTEuMyAyMC4wNHoiLz48L2c+PC9zdmc+)
![Outlier](https://img.shields.io/badge/Anomalies-Deetection-9cf?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMiA5OCA5OCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiPjxsaW5lYXJHcmFkaWVudCBpZD0iYSIgZ3JhZGllbnRVbml0cz0idXNlclNwYWNlT25Vc2UiIHgxPSIyNi4xNSIgeTE9IjcuMjUiIHgyPSIyNi4xNSIgeTI9Ijk0LjUxIj48c3RvcCBvZmZzZXQ9IjAiIHN0b3AtY29sb3I9IiMwMGVmZDEiLz48c3RvcCBvZmZzZXQ9IjEiIHN0b3AtY29sb3I9IiMwMGFjZWEiLz48L2xpbmVhckdyYWRpZW50PjxwYXRoIGQ9Ik0yNi42IDI4LjhjLTQuMyA0LjMtNi41IDEwLjQtNS45IDE2LjZhMy4xIDMuMSAwIDAwMyAyLjdoLjNjMS42LS4yIDIuOS0xLjYgMi43LTMuMy0uNC00LjQgMS4xLTguNyA0LjEtMTEuOGEyLjkgMi45IDAgMDAwLTQuMmMtMS4yLTEtMy0xLjEtNC4yIDB6IiBmaWxsPSJ1cmwoI2EpIi8+PGxpbmVhckdyYWRpZW50IGlkPSJiIiBncmFkaWVudFVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgeDE9IjQ5IiB5MT0iNy4yNSIgeDI9IjQ5IiB5Mj0iOTQuNTEiPjxzdG9wIG9mZnNldD0iMCIgc3RvcC1jb2xvcj0iIzAwZWZkMSIvPjxzdG9wIG9mZnNldD0iMSIgc3RvcC1jb2xvcj0iIzAwYWNlYSIvPjwvbGluZWFyR3JhZGllbnQ+PHBhdGggZD0iTTg4LjcgODYuNUw2OSA2Ni43YzUtNiA4LTEzLjYgOC0yMiAwLTE4LjktMTUuNC0zNC4zLTM0LjMtMzQuM1M4LjQgMjUuOCA4LjQgNDQuN0M4LjQgNjMuNSAyMy44IDc5IDQyLjcgNzljOC40IDAgMTYuMS0zIDIyLThsMTkuOCAxOS44Yy42LjYgMS40LjkgMi4xLjkuNyAwIDEuNS0uMyAyLjEtLjkgMS4yLTEuMyAxLjItMy4zIDAtNC4zem0tMjUuOC0yMmwtLjIuMi0uMi4yYy01LjEgNS0xMi4xIDguMS0xOS44IDguMS0xNS42IDAtMjguMy0xMi43LTI4LjMtMjguMyAwLTE1LjYgMTIuNy0yOC4zIDI4LjMtMjguM0M1OC4zIDE2LjMgNzEgMjkgNzEgNDQuN2MwIDcuNi0zLjEgMTQuNi04LjEgMTkuOHoiIGZpbGw9InVybCgjYikiLz48L3N2Zz4=)
![Time](https://img.shields.io/badge/Time%20Series-Analysis-blue?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyBoZWlnaHQ9IjUxMiIgd2lkdGg9IjUxMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNMjU2IDBMMTI4IDI1NmwxMjggMjU2YzE0MS4zOCAwIDI1Ni0xMTQuNjEgMjU2LTI1NlMzOTcuMzkgMCAyNTYgMHoiIGZpbGw9IiMyOGFiZmEiLz48cGF0aCBkPSJNMCAyNTZjMCAxNDEuMzggMTE0LjYxIDI1NiAyNTYgMjU2VjBDMTE0LjYyIDAgMCAxMTQuNjEgMCAyNTZ6IiBmaWxsPSIjMTRjZmZmIi8+PHBhdGggZD0iTTI1NiA2MGwtOTggMTk2IDk4IDE5NmMxMDguMjUgMCAxOTYtODcuNzUgMTk2LTE5NlMzNjQuMjUgNjAgMjU2IDYweiIgZmlsbD0iI2M0ZjNmZiIvPjxwYXRoIGQ9Ik02MCAyNTZjMCAxMDguMjUgODcuNzUgMTk2IDE5NiAxOTZWNjBDMTQ3Ljc1IDYwIDYwIDE0Ny43NSA2MCAyNTZ6IiBmaWxsPSIjZmZmIi8+PHBhdGggZD0iTTI5OC40MyAyNzcuMjFMMjU2IDIzNC44aC0yMGwyMCA0Mi40MiAyMS4yMSAyMS4yMnoiIGZpbGw9IiMzNDBkNjYiLz48cGF0aCBkPSJNMTcwLjggMTQ5LjU4bC0yMS4yMiAyMS4yMUwyNTYgMjc3LjIxVjIzNC44eiIgZmlsbD0iIzM3M2U5ZiIvPjxwYXRoIGQ9Ik0zNDEuNTYgMTQ5LjIzTDI1NiAyMzQuNzlsLTIwIDQyLjQyaDIwbDEwNi43Ny0xMDYuNzd6IiBmaWxsPSIjMzczZTlmIi8+PHBhdGggZD0iTTIxMy41NyAyNzcuMjFsMjEuMjIgMjEuMjJMMjU2IDI3Ny4yVjIzNC44eiIgZmlsbD0iIzM4NTdiYyIvPjxwYXRoIGQ9Ik0yNzEgOTBoLTE1bC0xMCAxNSAxMCAxNWgxNXoiIGZpbGw9IiMzNDBkNjYiLz48cGF0aCBkPSJNMjQxIDkwaDE1djMwaC0xNXoiIGZpbGw9IiMzNzNlOWYiLz48cGF0aCBkPSJNMjcxIDM5MmgtMTVsLTEwIDE1IDEwIDE1aDE1eiIgZmlsbD0iIzM0MGQ2NiIvPjxwYXRoIGQ9Ik0yNDEgMzkyaDE1djMwaC0xNXpNOTAgMjcxdi0zMGgzMHYzMHoiIGZpbGw9IiMzNzNlOWYiLz48cGF0aCBkPSJNMzkyIDI3MXYtMzBoMzB2MzB6IiBmaWxsPSIjMzQwZDY2Ii8+PC9zdmc+)



## Introduction
This is a time series analysis to detect anomalies/ outliers in New York Drinking Water Quality data available from [here](https://opendata.cityofnewyork.us/). The data consists of the turbidity values, coliform, fluoride and chlorine found at sites in distribution each month. However, there are missing values from certain months depending on the sites. There are 398 unque locations/ sites in the data. Each site presented data of different durations ranging from 43 days to 1673 days. For the purpose of time series analysis, I decided to analyse the data from the site with the longest amount of data. I've also abritarily decided to analyse turbidity of the water from. 

According to [USGS](Turbidity is the measure of relative clarity of a liquid. It is an optical characteristic of water and is a measurement of the amount of light that is scattered by material in the water when a light is shined through the water sample.), turbidity is the measure of relative clarity of a liquid. It is an optical characteristic of water and is a measurement of the amount of light that is scattered by material in the water when a light is shined through the water sample. [WHO](https://www.who.int/water_sanitation_health/publications/turbidity-information-200217.pdf) maintained that turbidity is an extremely useful indicator that can yield valuable information quickly, relatively cheaply and on an ongoing basis. While the turbidity is aimed to be as low as possible, the target turbidity depends on the stage of the water treatment. In distribution, if the turbidity is >= 4, it indicates possible faults or breaches in the distribution. There are many sources of turbidity; it might be harmless (eg clay, soil) or it could be an indication of the presence of dangeous chemical or biological compounds.

Here, I presented two different ways to detect outliers in time series in R. Specifically, I'm using `anomalize` and `tsoutliers`. Both R packages to detect outliers in time series. However, both have fundamentally very different basis for outliers and thus different ways to work to detect outliers. I'll go into a bit more details in the respective sections.

## Data Cleaning
### Missing values
The data needed some cleaning at first. The class for the turbidity was character and so was the Date. After conversion, I decided to take three variables: turbidity, free chlorine and fluoride level at first. However, for the purpose of this project, we'll look only at turbidity. During data cleaning, I realise that some dates were missing and some values for fluoride is missing for some dates. The following chart displays the missing values:

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/Missing_by_date.png" alt="Missing values by date">
</p>

### Imputation of Missing Values
Using fluoride data, I imputed the missing values using different methods. The charts below show some examples. From the graphs, I decided to uses seasonal decomposition to impute the multivariate data as it presents the most visually believable pattern.

<img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/mean.png" width="400"/> <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/spline.png" width="400"/>
<img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/seadec.png" width="400"/> <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/linear.png" width="400"/>

## Exploratory Analysis
### Time Series Plot
Here's the plot of three series. At first glance, I thought chlorine and turbidity had some correlations.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/multi_time_plot.png" alt="Time series plot of the multivariate data">
</p>

### Correlation Plot
I was quite surprised to see that chlorine and turbidity had very weak correlation.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/correlation.png" alt="Correlation of the variables">
</p>

### Histogram 
As I decided to look at turbidity, I wanted to see the distribution of the turbidity. From the histogram below, it can be seen that a large majority of it is <1 NTU. However, there are still some >1 NTU and even an entry around 1.5 NTU, which would be an anomaly.

<p align="center">
    <img src="https://github.com/hannz88/Time_Series_Anomaly_Detection/blob/main/Images/histogram.png" alt="Histogram of turbidity">
</p>

## `anomalize`







































<div>R icon made by <a href="https://www.flaticon.com/authors/becris" title="Becris">Becris</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
<div>Maginifying glass icon made by <a href="" title="Kiranshastry">Kiranshastry</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
<div>Clock icon made by <a href="https://www.freepik.com" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
