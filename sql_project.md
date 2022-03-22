## Covid Data Exploration with SQL (MS SQL Server)

**Project description:** 
1. Data origin: The data was pulled from [ourworldindata.org](https://ourworldindata.org/covid-deaths)
2. The data covers a wide range of information from death count to test, vaccination, hospital admissions, financial and medical conditions, GDP, etc of all countries from the beginning of the pandemic till 24th Jan 2022.
3. Goal of the project: I did some exploration with some of the columns (attributes) of the dataset, namely daily new_case, death and vaccination counts and organized and filtered to make quantitative observations and get a sense for the data.
4. Gist of what I have found in the data set: 


### Summary of the important quesries to explore the data

1. Percent of patients that passed away in European countries in Desending order (as of 2022-01-24).
It shows the possibility of death in case of infection for each country and for more precise outlook the analysis could be broken down to provinces and cities combined with socio-demographic and health conditions. 
For example, it could be the case that amount of daily sunlight in a region could have an effect on mortality rate of men over 60 with certain medical condition.  

```sql

SELECT location, date, total_cases, total_deaths, round((total_deaths/total_cases)*100, 2) AS death_percent
From SQL_Project..[covid-death]
WHERE continent = 'Europe' and date = '2022-01-24 00:00:00.000'
order by 5 desc

```

2. Percent of population infected in Asian countries (as of 2022-01-24).

```sql

SELECT location, date, total_cases, population, (total_cases/population)*100 AS Infected_population_perc
From SQL_Project..[covid-death]
WHERE continent = 'Asia' and date  = '2022-01-24 00:00:00.000'
order by 5 desc

```

3. 

```sql

SELECT location, date, total_cases, population, (total_cases/population)*100 AS Infected_population_perc
From SQL_Project..[covid-death]
WHERE continent = 'Asia' and date  = '2022-01-24 00:00:00.000'
order by 5 desc

```

### 1. Suggest hypotheses about the causes of observed phenomena

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

```javascript
if (isAwesome){
  return true
}
```

### 2. Assess assumptions on which statistical inference will be based

```javascript
if (isAwesome){
  return true
}
```

### 3. Support the selection of appropriate statistical tools and techniques

<img src="images/dummy_thumbnail.jpg?raw=true"/>

### 4. Provide a basis for further data collection through surveys or experiments

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
