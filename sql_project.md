## Covid Data Exploration with SQL (MS SQL Server)

**Project description:** 
1. Data origin: The data was pulled from [ourworldindata.org](https://ourworldindata.org/covid-deaths)
2. The data covers a wide range of information from death count to test, vaccination, hospital admissions, financial and medical conditions, GDP, etc of all countries from the beginning of the pandemic till 24th Jan 2022.
3. Goal of the project: I did some exploration with some of the columns (attributes) of the dataset, namely daily new_case, death and vaccination counts and filtered and did some calcualtion to make quantitative observations and get a sense for the data.
4. Gist of what I have found in the data set: 

<br>
<img src="images/coronavirus-data-explorer.png?raw=true"/>
<br>

### Summary of quesries to explore the data

1. **Mortaity rate in Europe:** 
Percent of confirmed cases that passed away in European countries in Desending order (as of 2022-01-24).
It shows the possibility of death in case of infection for each country and for more precise outlook the analysis could be broken down to provinces and cities combined with socio-demographic and health conditions. 
For example, it could be the case that amount of daily sunlight in a region could have an effect on mortality rate of men over 60 with certain medical condition.  

```sql

SELECT location, date, total_cases, total_deaths, round((total_deaths/total_cases)*100, 2) AS death_percent
From SQL_Project..[covid-death]
WHERE continent = 'Europe' and date = '2022-01-24 00:00:00.000'
order by 5 desc

```

2. **Infection rate in Asia:**
Percent of population infected in Asian countries based on confirmed cases (as of 2022-01-24). 
(Of course someone could ask if people who are infected many times are counted again in the total_cases or not.)

```sql

SELECT location, date, MAX(total_cases) as Highest_case_count, population, MAX((total_cases/population)*100) AS Infected_population_perc
From SQL_Project..[covid-death]
WHERE continent = 'Asia'
group by location, population, date
order by Infected_population_perc desc

```

3. Vaccination count in countries around the world (till 2022-01-24) 
(Inner Join)

```sql

SELECT dea.location, population, Max(cast (total_vaccinations as bigint)) as Total_vaccination
From SQL_Project..[covid-death] dea
Inner Join SQL_Project..[covid-vaccinations] vac
	On dea.location = vac.location 
	and dea.date = vac.date
WHERE dea.continent is not null
Group by dea.location, population
Order by Total_vaccination desc

```

4. Rolling Count of vaccination in countries around the world (till 2022-01-24) 

```sql

SELECT dea.continent, dea.location, dea.date, dea.population, vac.new_vaccinations,
	Sum(Convert(bigint, vac.new_vaccinations)) OVER (Partition by dea.location Order by dea.location,
	dea.date) as Rolling_vac_count
From SQL_Project..[covid-death] dea
Join SQL_Project..[covid-vaccinations] vac
	On dea.location = vac.location 
	and dea.date = vac.date
WHERE dea.continent is not null
Order by 2,3

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


