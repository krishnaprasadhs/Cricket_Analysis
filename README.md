# End_to_End_Cricket_Analysis
## Table of Contents :

- [Problem Statement](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#problem-statement-)
- [Datasource](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#datasource-)
- [Data Collection](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#data-collection)
- [Data Transformation](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#data-transformation)
- [Data Modelling](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#data-modelling)
- [Data Analysis Expression (DAX)](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#data-analysis-expression-dax)
- [Report](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#dashboard)
- [Tools, Software and Libraries](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#tools-software-and-libraries-)
- [References](https://github.com/krishnaprasadhs/End_to_End_Cricket_Analysis#references)

## Problem Statement :

In This project Created a Power BI Dashboard which helps to review and compare performances of all the players in T20 Men's Cricket World Cup 2022 tournament. This dashboard also enables us to select the best 11 of the tournament based on their performance based on defined selection criteria which is included as a part of problem statement.

## Datasource :

Scrapped all the data regarding match and world cup from www.espncricinfo.com and all details of player career performace and collect data on [brightdata](https://brightdata.com/)

## Data Collection:
Scrapped all the data regarding match and world cup and all details about players career from [brightdata](https://brightdata.com/) using Beautiful Soup library and Jupyter Notebook is used to convert the json files into the dataframes and then these dataframes into csv file for further data analysis on power bi.

## Data Transformation:
Performed initial data cleaning after scrapping such as player name correction, handle missing value, match id linking etc. using Pandas. Transformed the final data for dashboard using Power Query of Power BI.

## Data Modelling:
Connected all the datasets with based on some defined primary keys such as team and match ids. Also, created many measures, calculated columns and parameters for data analysis and dash boarding using DAX.

## Data Analysis Expression (DAX)
Measures used in visualization are:

- Total Runs = `SUM(t20_batting_summary[runs])`

- Total Innings Batted =`COUNT(t20_batting_summary[matchID])`

- Total Innings Dismissed = `SUM(t20_batting_summary[Out])`

- Batting Avg = `DIVIDE([Total Runs],[Total Innings Dismissed],0)`

- Total balls faced =`SUM(t20_batting_summary[balls])`

- Strike rate = `DIVIDE([Total Runs],[total balls faced],0)*100`

- Batting Possition = `ROUNDUP(AVERAGE(t20_batting_summary[battingPos]),0)`

- Boundary % = `DIVIDE(SUM(t20_batting_summary[Boundary runs]),[Total Runs],0)*100`

- Avg. balls faced = ` AVERAGE(t20_batting_summary[balls])`

- wickets = `SUM(t20_bowling_summary[wickets])`

- Balls Bowled = `SUM(t20_bowling_summary[balls])`

- Runs Conced = `SUM(t20_bowling_summary[runs])`

- Economy = `DIVIDE([Runs Conced],([Balls Bowled]/6),0)`

- Bowling Strike Rate =`DIVIDE([Balls Bowled],[wickets],0)`

- Bowling Avrage = `DIVIDE([Runs Conced],[wickets],0)`

- Total Innings Bowled = `DISTINCTCOUNT(t20_bowling_summary[matchID])`

- Dot Ball % =` DIVIDE(SUM(t20_bowling_summary[zeros]),SUM(t20_bowling_summary[balls]),0)`

- Player selection = `if(ISFILTERED(t20_players_info[name]),"1","0")`
