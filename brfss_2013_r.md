## BRFSS 2013 Dataset Exploration with R

**Project description and link:** 
1. Behavioral Risk Factor Surveillance System (BRFSS) a telephone survey that state health departments conduct monthly over landline telephones and cellular telephones with a standardized questionnaire.
2. The dataset is accessible in [CDC website.](https://www.cdc.gov/brfss/annual_data/annual_2013.html)
3. The data gathering in this survey is a type of random sampling method, so the conclusion could be generalized to the sampled population.([Survey Documentation](https://www.cdc.gov/brfss/data_documentation/index.htm))
4. I explored data for questions about Sleep time, Health Care Access and Demographics.  
5. Full project document is accessible [here.](Exploring-the-BRFSS-data.html)

<br>
<img src="images/BRFSS.PNG?raw=true"/>
<br>

### Summary of analysis and findings:

**1. Sleep time raletion to a,b and c:** 

I was interested to find attributes in the dataset that correlates with Sleep time of the survey respondents. On the first attempt I looked at Gender, Income, Education to see if there is connection.

```r

ggplot(data = sleep_clean, aes(x = sleptim1)) +
  geom_boxplot() +
  xlab("Sleep time")

```
<img src="images/Sleep_time.PNG?raw=true"/>
