# WDI
This is an exploratory data analysis of the World Development Indicators dataset. The dataset has a variety of data from different domains such as economic policies of a country, poverty, education, infrastructure and technology, healthcare. The goal was to evaluate performance of countries the best, see if there are certain countries that have significantly been able to change their results and try to find out if any identifiable reasons for that exist. As a goal, I tried to see if there are some controllable factors like government expenditure which generally result in human prosperity or better life quality. I also tried to find out which specific policy decisions, societal norms or perception of people is the difference between developed countries and developing countries. In order to check the overall importance of an indicator in the quality of living in a country, I analyzed developed nations with a focus on US and Canada and their comparison. To find the differentiating factors between developing and developed countries, Iused India as an example of a developing nation. In the end, I did find some indicators that are related to indicators in seemingly other domains. The results could potentially serve as a guide to the actions that can be taken by governments for betterment of quality of life.

# Introduction

The reason behind the choice of this dataset is the variety of data it provided. The fact that the dataset had covered all the aspects of human life, especially Economy, Health and Education made it worth exploring. To get better insights on our findings, we also added the data we collected from Happiness Index Report . The data from the World Development Indicators dataset helped us in understanding the objective, measurable elements of human development, but we also wanted to see how well how well some subjective, self-identified factors such as self-described happiness, perception of freedom, corruption, generosity depend on the objective measures of well being. The project was a great opportunity for us to dive deep into all the aspects of data science. Data manipulation, Statistical Analyses, Machine Learning and Data Visualization. Statistical Analysis on the data was a crucial part for us. We tried to be as thorough as we could in the statistical analysis part by analyzing our Hypothesis Test results deeply, checking for significance or magnitude of the results by running post-hoc tests. Visualization was another challenge for us because our project is data driven which makes representation of data really important. We tried to find best possible diagrams and tools that make it easy to interpret the information. We also familiarized ourselves with the concept of Time Series Analysis. Although we had learnt these things to one extent or another throughout the Big Data program, the project enhanced our knowledge about them and helped us learn how to put our knowledge into practice. Applying these methods to a real world problem, the WDI dataset, gave us a chance to learn and overcome the problems we faced while implementing them while simultaneously getting to know a lot about the problems faced by many countries and their possible solutions.There was some work that we did which ended up being insignificant. This echos either models that failed, tests that did not give expected or significant results, or results that we could not be sure about. We have added all of this in the Appendix part.

# Prior Research 
We looked for related work done by others on this dataset. There was not much that was done to comprehensively cover the entire dataset, but we found some interesting studies done on specific parts of the dataset.This study [3] by Krishna Ravikumar is a comparison between India and China’s development indicators on the same database. The focus was on some economic indicators such as GDP, Trade and import export as well as life expectancy and literacy rate. The conclusion was that China is ahead of India in most indicators. India’s lag from China was between 10 to 25 years depending on the indicator. The stated result was that India is that many years behind China in those indicators. This seemed like a too simplistic way to draw a conclusion and it was based on minimal data. However, the approach taken was novel, the visualization was good, and the overall idea seemed interesting. This study [4] by itssangeeta tries to explore global wealth inequality and growth over the years. It has some great observations about how far countries have come from 1960. It provides insightful information about countries that have been consistently poor or rich, countries that are emerging, and countries that stand out in terms of accumulation of wealth, average income or wealth distribution. The comparison it attempts to do is interesting, but it sometimes fails to recognize missing data at some points, specially in the earlier years, which sometimes makes the outcome of the graph look a bit contextless. Yet, there were some interesting observations and based on that they went deep into interesting specifics. From these projects, we picked up how to roughly observe outliers or significant deviations from ordinary and then try to find out more about them. These projects don’t go into any further statistical analyses or Machine learning. We wanted to do that but there was something to be gained from these projects about what things can be tried to find interesting trends and how to focus on interesting specifics which we could then analyse further.

# Experiment and results 
## Health
After importing the data, the first domain that we chose to analyse was Health since quality and availability of healthcare in a country is one of the best indicators its overall well-being.
The first thing we checked was the life expectancy of countries in 2018. Then, we checked which countries spent more on healthcare. We measured the spending per capita in USD.
![image](https://user-images.githubusercontent.com/46672370/119705044-5213dc00-be26-11eb-969a-bb9bdfc0595f.png)


Then, we decided to see how both these things have progressed in different country categories. These categories were based on the economic condition of a country.

![image](https://user-images.githubusercontent.com/46672370/119705172-6eb01400-be26-11eb-8445-83d645e1accf.png)


We saw that the Life expectancy had gone up for the entire world progressively. Same can be said for spending as well. The average of high-income countries was $2700 in 1964 which went up to $5750 in 2017. For lower income countries, it went from $54 to $104. 
Next, we compared the health spending per capita of U.S., Canada and India. For a fair comparison, we compared their expenditure as a percent of their GDP.

![image](https://user-images.githubusercontent.com/46672370/119705265-85ef0180-be26-11eb-896b-ab9a66685c90.png)

We saw that Canada's expenditure was the closest to the world. United States spent a lot higher than Canada whereas India's spending seemed significantly lower than the world average. 

### Does more expenditure give better outcomes? 

Looking at these graphs, it looks like countries with higher spending have better Health coverage. We decided to verify this by doing a pearson correlation test between life expectancy and health expenditure.
![image](https://user-images.githubusercontent.com/46672370/119705455-c2226200-be26-11eb-9e21-9dc4c8d6c10e.png)

The correlation coefficient was 0.63, which makes it a decent correlation.

After this, we checked the correlation between Per capita expenditure and UHC index, which seemed like an even better indicator of a country's Health coverage and quality. UHC (Universal Health Coverage) index is given by the World Health Organization and it also considers factors such as access to healthcare, quality, child or new-born mortality rate, spread and prevalence of infectious disease etc.

![image](https://user-images.githubusercontent.com/46672370/119705735-1a596400-be27-11eb-90ce-296785cf1e0c.png)


The correlation was 0.677 which is an even better correlation. We could firmly say that spending more on healthcare results in better outcomes objectively.

![image](https://user-images.githubusercontent.com/46672370/119705859-4379f480-be27-11eb-844d-41317bc1052d.png)

### Does India spend significantly less than other lower middle income countries?

India was 3rd in this list. From this and other the data we saw, it looked like India's poor performance in healthcare was due to low spending on healthcare, which was substantially less than the world average. In fact, it seemed even less than the spending of countries of Lower middle income category. We wanted to statistically verify this hypothesis so we used t-test to see if the difference was actually statistically significant.

![image](https://user-images.githubusercontent.com/46672370/119705965-60aec300-be27-11eb-9f28-b7cd35a5e0f4.png)

It turned out that the difference between India's health expenditure as a percent of GDP and the average of spending of lower middle income countries was statistically significant with India's spending being low. We used cohens_d method to get the effect size, which was large. 

### Predictors of Universal Health Coverage Index 

Then we wanted to see what factors impact the UHC index the most, so we ran regression tests between UHC coverage and various indicators in the healthcare domain. In the end, the most effective combination of predictors was Government health expenditure and physicians per 1000.

![image](https://user-images.githubusercontent.com/46672370/119706192-a4a1c800-be27-11eb-839a-95921302a853.png)

![image](https://user-images.githubusercontent.com/46672370/119706276-c307c380-be27-11eb-8f5b-163c6faa7633.png)

Running a Linear model with Universal Health Coverage Index as the dependant variable and Life expectancy and Doctors per 1000 people as predictors, gave us an adjusted R-squared of 0.84 with 663.9 F-statistic on 2 and 250 df (p < 0.0001). 
The value of adjusted r-squared was 0.84 which means that 84% of variability in UHC index is explained by our selected predictors.
Our focus then was the population growth problem. We started by seeing the population growth of world’s most populated countries India and China and compared their growth to the world.


