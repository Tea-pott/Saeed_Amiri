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

**1. Health Care coverage and Health care access raletion to Gender and Income level:** 

I was interested to see if Health care realted data of the survey respondents correlates with demographic data. On the first attempt I looked at Gender and Income to see if there is connection. As we go toward groups with higher income, the proportion of respondents with a health care plan increses, as shown in the chart.

```r

ggplot(subset(health_clean, !is.na(income2)), aes(x = income2, fill = hlthpln1)) +
  geom_bar(position = "fill", aes(y = (..count..)/sum(..count..))) +
  xlab("Income") +
  labs(fill = "Health care coverage") +
  scale_y_continuous(labels = scales::percent, name = "Proportion") +
  coord_flip()

```
<img src="images/income_healthplan.PNG?raw=true"/>


