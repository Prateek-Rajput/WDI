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

![download](https://user-images.githubusercontent.com/46672370/119892088-bd81aa80-bf07-11eb-9f8a-37e28ccb3523.gif)

We saw that the population growth rate was decreasing for both these countries. In fact, both these countries have a lower population growth rate than the world average currently. 
An interesting discovery is that the sudden dip in China’s population growth occurred in 1979. The reason behind that was the One child policy introduced by China. Though they have lifted it in 2015, its immediate results can be clearly seen.


Since the population growth for these countries and the world is gradually decreasing, it seemed that the population may stabilize someday in the future. We wanted to see when the population growth will get to 0. We used forecast function by r, which can be used for forecasting time series, to find the approximate year when population growth may get to 0.

![image](https://user-images.githubusercontent.com/46672370/119892430-1f421480-bf08-11eb-9197-88d4b4e92178.png)

The results suggest that the population growth will get to 0 % around 2070. The results are close to a study done in 2014 which showed it will happen around 2075. 

## Economy

Our next focus was economy. We started by seeing the countries with highest GDP. European and North American countries topped this list. We then saw which countries have highest growth rate of GDP and as expected, this list was topped by countries that are developing but have good economies. 

![image](https://user-images.githubusercontent.com/46672370/119892708-79db7080-bf08-11eb-8734-9132eea8e2c8.png)

![image](https://user-images.githubusercontent.com/46672370/119892763-86f85f80-bf08-11eb-9c98-829d76768c1b.png)

The next thing we checked was the growth rate of USA and Canada, which are first world countries and India which is a developing nation to look for conclusive trends.

![download (1)](https://user-images.githubusercontent.com/46672370/119893020-d9398080-bf08-11eb-8310-dd9a118c6ac8.gif)

Out of these countries, India has consistently had highest GDP growth rate. US and Canada have had similar growth rates. Around 2008, all the countries had lowest growth rate in years. US, Canada and world average had gone below zero percent. This can be attributed to the Economic recession which hurt almost the entire world economically. 

We wanted to see if similar results are reflected by other countries with similar economic categories, so we plotted various country categories.

![image](https://user-images.githubusercontent.com/46672370/119893086-f3735e80-bf08-11eb-98d7-c7c5e1f54314.png)

The results we found were interesting. One of the things we noticed was how Lower middle income, middle income and upper middle income countries' economies almost go hand in hand. These categories are above the rest or world average which suggests that they are economies that are getting constantly better.High income countries have economies who have relatively stable growth rate just above zero. The world economy, however, is heavily influenced by the higher income countries. The line graphs of these two categories go together through the years. 

### Does US have a higher per capita GDP than Canada? 

We compared the adjusted GDP per capita of Canada and USA which are believed to be equally wealthy. We ran a hypothesis test with the null hypothesis that USA and Canada have the same GDP per capita over the years. 

![image](https://user-images.githubusercontent.com/46672370/119893270-26b5ed80-bf09-11eb-8506-7f1b037c943f.png)

The result showed that the GDP of USA was statistically higher than that of Canada. Since the data was not normally distributed, we ran Wilcoxon test which showed that the GDP Per Capita of US was high with a W-statistic of 64 (p<0.0001). Running the cohens_d test revealed that the magnitude of this difference was large.

### Income inequality and GDP per capita 

One of the most interesting facts we found was the correlation between GDP and percent of income share held by the wealthiest and least wealthiest. Here are the results of correlation tests between GDP per capita and income share held by the bottom 10% :

![image](https://user-images.githubusercontent.com/46672370/119893482-6aa8f280-bf09-11eb-8bab-813eb5cfe15d.png)

And here is the result of pearson correlation test between GDP per capita and income share held by the top 10% :

![image](https://user-images.githubusercontent.com/46672370/119893537-7c8a9580-bf09-11eb-973d-03cd5fda58fa.png)

The GDP per capita was directly proportional to the income share held by the bottom 10% of the country (r=0.32), but it was inversely proportional to the income share held by the richest 10% (r= -0.43). This was surprising and it clearly displayed how income inequality was a problem for the overall well-being of a country.

### Unemployment problem in India 

When we checked the unemployment rate of India, US and Canada, India’s unemployment rate turned out to be the lowest. It was surprising since US and Canada have much better economies than India. It turns out that the real problem in India is underemployment, which isn’t measured well in a country like India. We decided to check Youth unemployment rates (People between 16-25 who are not in school nor working). That gave us a much better picture of the performance of these countries.

![image](https://user-images.githubusercontent.com/46672370/119893721-b52a6f00-bf09-11eb-8ceb-657431f1e720.png)

In both of the graphs, US and Canada have a drop at around 2008 near the recession years, but India has a much higher rate of youth unemployment than US and Canada. The fact that it is much higher than even the lower middle income countries and is continuously increasing in past few years is concerning.

## Education

The very first thing that we wanted to check in education was to see that which were the countries that spent the most on education. For most of the parts, we wanted to analyze the indicators for the latest year in which the largest amount of data was available. So, the spending was checked for the year 2017, which turned out to be that the  most of the countries among the top 10 countries were African countries such as Lesotho(7.42%), Burkina Faso(6.42%), Guyana(6.23%), South Africa(6.11%) and Mozambique(5.75%).

![image](https://user-images.githubusercontent.com/46672370/119894302-70530800-bf0a-11eb-8200-cab814951d98.png)

Then we checked the educational expenditure for the country categories according to the income and also the average of the world and compared it to the literacy rates for the same. The country categories were Low income, Low & middle income, Middle income. The results indicated that the more a country spends on education, the more the literacy rate of the country is. Also, the better the economy of a country is, the more it spends on education. Therefore, middle income countries spend more on education than low & middle income countries, and as a result, the literacy rate of middle income countries is better than that of low income countries as well.

![image](https://user-images.githubusercontent.com/46672370/119894416-924c8a80-bf0a-11eb-8826-75fb783cc54c.png)

### Education problem in Pakistan

One really interesting indicator in education was the one that displayed the amount of primary age children that should have been enrolled in primary or secondary school, but are not. After delving into this indicator, one shocking fact was found that in the year 2018, there were more than six million primary school age children in Pakistan who were not enrolled in school. This number is three times greater than that of Tanzania, which is the 2nd country for this indicator. 

![image](https://user-images.githubusercontent.com/46672370/119895270-94631900-bf0b-11eb-8dc1-ca8f6e3f8476.png)

The last thing that we checked in education sector was the educational attainment for different levels and seeing the top 10 countries in each country. It turns out that in Germany, 100% of adults have attained primary level education. Germany also comes in top 10 countries in other level of education (upper secondary, bachelors, masters and doctoral). Uzbekistan, Kazakhstan, Australia, Maldova and United States of America have 99% of adults that completed primary education. Kazakhstan also tops in upper secondary level education.United Arab Emirates has most number of bachelors graduated while Switzerland has most number of people that have masters and doctorate degrees.

Countries with highest people with Primary education attainment

![image](https://user-images.githubusercontent.com/46672370/119895322-a47af880-bf0b-11eb-8c76-4ac5b4ccfd4d.png)

Countries with highest people with Secondary education attainment

![image](https://user-images.githubusercontent.com/46672370/119895476-d42a0080-bf0b-11eb-969e-26afa6d95e75.png)

Countries with highest people with Bachelor's degree

![image](https://user-images.githubusercontent.com/46672370/119895614-fae83700-bf0b-11eb-8ac7-2ebcb0ea24cd.png)

Countries with highest people with Master's degree

![image](https://user-images.githubusercontent.com/46672370/119895657-0a678000-bf0c-11eb-87d2-520aafad6b51.png)

Countries with highest people with PhD

![image](https://user-images.githubusercontent.com/46672370/119895740-1fdcaa00-bf0c-11eb-87c0-4ceefa272f81.png)

Then we wanted to see the correlation between the percent of youth educated and percent of youth unemployed. The value for the Pearson Correlation Coefficient is 0.36 indicating that there is a moderate correlation between the aforementioned indicators.

![image](https://user-images.githubusercontent.com/46672370/119895815-3420a700-bf0c-11eb-8115-8ce07c4d3c1c.png)

## Infrastructure

### Cellphone users in India 

While seeing the indicators available in infrastructure sector, we were particularly intrigued by the percent of population using internet. So, we checked it for the years after 2000 in India. And an interesting thing was found that in the early 2000s, almost 0% of the population in India was using internet. The number grew gradually and reached over 20% in 2014, then dropped a bit in the following year. But after 2015, a huge spike can be seen, a 15% increase was experienced. The reason behind the growth was the introduction of a telecommunication company named Jio. The very first year of the company, a usage of 2gb of data was given to everyone who bought the sim at no cost for a whole year.

![download](https://user-images.githubusercontent.com/46672370/119896058-7f3aba00-bf0c-11eb-8185-43edc61f93f9.gif)

### Europe's supremacy in infrastructure 

Another thing that we found in Infrastructure was that the European developed countries outperformed other developed countries of the world in the infrastructure sector.
In efficiency of customs procedure, countries like Finland(6.3), Netherlands(6.3) Sweden(5.6), United Kingdom(5.5), Ireland(5.4), Switzerland(5.4) and Austria(5.3) have the highest ratings.This indicator is a rating given by the business executives of the country according to their perspective on their country's efficiency on customs procedure.
For quality of port infrastructure too, European developed countries were among the top 10. With having rating above 5 out of 7.

![image](https://user-images.githubusercontent.com/46672370/119896363-ea848c00-bf0c-11eb-91f9-de2398430a45.png)

![image](https://user-images.githubusercontent.com/46672370/119896394-f40df400-bf0c-11eb-9e81-f3393988adb7.png)

## Public and Private Sector

The first thing that we analyzed in this domain was the debts of countries, but we were specifically interested in India. Then we compared the debt of India with United States of America. We saw the progression of debt of both of the countries over the years. 
In the first graph, it can be seen that the debt of India has been rising on a very fast pace each year. It started with a bit above 1 trillion USD in 1991 and by the year 2015, it reached above 55 trillion USD. The debt of USA has also been rising over the years, but it is not as huge amount as India and also the progression is not that large. 
After seeing the debt, we then calculated and added the deficit for each year. We noticed a huge spike in the deficit of USA in the year 2001. On researching about it, we came to know that there was a huge tax cut in USA in 2001 and also the military expenditure of USA was very high.

![image](https://user-images.githubusercontent.com/46672370/119896489-1273ef80-bf0d-11eb-84a7-88cb8f327a12.png)

![image](https://user-images.githubusercontent.com/46672370/119896532-2586bf80-bf0d-11eb-874c-e61ead77854e.png)

The next thing was to check the expenditure of government.For this, we checked it for the high income category to get a general idea on how much a country with a good economy would spend. We also considered World average, United States of America, Canada and India for this one, to get a diverse outcome. 

In 2017,the high income countries spend more than that of the world average and as expected, USA's expenditure was also more than Canada and India.

![image](https://user-images.githubusercontent.com/46672370/119896578-3800f900-bf0d-11eb-9464-3cb4933b644d.png)

While exploring the indicators for this sector, we came around the total tax rate of a country and decided to analyze the same for the different country categories and compared it with the World average too. The tax rate of the countries with better economy have a fairly stable and low tax rate over the years but it's not the same with low income countries. As wealthy a country gets, the tax rate also decreases accordingly. 

![image](https://user-images.githubusercontent.com/46672370/119896629-48b16f00-bf0d-11eb-8ddc-a9966b494295.png)

### Drop in Canada's corporate tax rates 

One interesting high income country was Canada because we noticed a huge drop in the tax rate in the year 2009. So after researching why it happened, we came to know that due to recession, to keep up with the world market, Canada had to lower the tax rate to almost half(42% - 22%). Since then, it has been a bit stable and is increasing in the recent years.

![image](https://user-images.githubusercontent.com/46672370/119896737-71d1ff80-bf0d-11eb-8e77-395ec17a29bc.png)

### Do better economies have less bribery incidences?

We came across an interesting indicator that recorded that how much percent of firms were offered bribe at least once in a country.
So, we then delved into the indicator and noticed that better economies had less bribery incidences. Therefore, to confirm it, we ran a Pearson correlation test between bribery incidences and GDP of a country. The value for the coefficient was -0.45 suggesting that better economies do experience less bribery incidences.

![image](https://user-images.githubusercontent.com/46672370/119896805-8a421a00-bf0d-11eb-8f7e-f3a5d4ee6340.png)

### Predictors of GDP 

After observing all the data and finding interesting models and correlations, we wanted to see if we can find some definitive facts about how human well being can be achieved. Firstly, we used GDP per capita as the metric of human well being and checked which specific factors affect it the most. We ran multiple models with a combination of different predictors but the one with highest value of adjusted r-squared was the model with a combination of UHC index, Bachelor’s education attainment rate and unemployment rate. Out of these three, UHC index and Educational attainment were the most significant ones. This makes sense as Health and Education are considered really important and basis for the progress of a country.

![image](https://user-images.githubusercontent.com/46672370/119896889-aa71d900-bf0d-11eb-87a7-4e3a4525b7af.png)

The adjusted r-squared for this was 0.56. UHC index, Bachelor's attainment rate and total unemployment rate can explain 56% of variability in GDP per capita.

### What Predicts Happiness? 

Though GDP is certainly a really important factor of well being of a country, we decided to go a step further and echo the Happiness index report dataset. Happiness Index Report consists of subjective data where questions are asked to people to get their perceived answers.  The dataset has Happiness Score, Freedom to make life choices, Generosity, Social support, perception of corruption. Here is a brief look at the dataset:

![image](https://user-images.githubusercontent.com/46672370/119896960-c5dce400-bf0d-11eb-9b6b-6a7e59b14e70.png)

We considered the average self-perceived happiness score of a country as a metric. Since all of the indicators in the HIR were self-perceived, we categorized them as Subjective. In contrast, the indicators in the WDI were Objective, since they were measurable numbers. Then, we took the Happiness Score as our dependant variable and again ran various models once with Subjective indicators, once with Objective indicators and once with a combination of both. The results are as follows: 

![image](https://user-images.githubusercontent.com/46672370/119897071-e73dd000-bf0d-11eb-980b-f74c45837049.png)

Details of these models:

1) Objective Predictors (From World Development indicators dataset)

![image](https://user-images.githubusercontent.com/46672370/119897138-fcb2fa00-bf0d-11eb-9aed-34e04f9a0f36.png)

2) Subjective Predictors (From Happiness Index dataset)

![image](https://user-images.githubusercontent.com/46672370/119897194-0e949d00-bf0e-11eb-8a34-4e3c401dc521.png)

3) Combination of objective and subjective predictors

![image](https://user-images.githubusercontent.com/46672370/119897252-22400380-bf0e-11eb-9c5b-1eff56afd10c.png)

We can see that when the indicators from World development indicators and Happiness index report are combined, the results get even better. This model explains 76% variability in Happiness score. We can safely say that Happiness is indeed a combination of perceived factors and objective indicators.

### Limitations and future work 

One of the shortcomings of our project is the lack of data. Many countries don’t provide some data at all, some data wasn’t available in the earlier years, some data is collected only once in a few years and these factors make it hard to implement deep analysis, especially machine learning. Because of the volume of the missing data, imputing missing data wasn’t a possibility either. The other issue is that the data is static. Some of the indicators mentioned in the data have values that change or are updated regularly, but the dataset as a whole is updated quarterly. Although most of the data won’t be affected by dynamic updating, it certainly could be a way to get much better outputs and tracking the progress of countries would be much easier.

Due to the size of the dataset, we were almost certain that we wouldn’t be able to cover all of it. There were some domains that we couldn’t cover and even within the domains we did, there could be some indicators we missed that could have given revealing results or enhanced our statistical analyses. There is a lot more that can be done with this dataset. People with expertise in specific domains such as Economy, health or gender studies can analyse that part of data substantially better than we did and the results they find would be much more accurate. Not only would they be able to explain the data well, but they would also be able to do a lot in terms of practical suggestions of solutions in the domains. 

We intended to show rest of our work (Graphs, tests that didn't give good results, tests where we later realized that the data isn't sufficient) at the end of the report in the appendix, but there is a lot of content in this section, so we decided to not show it in the report. We have echod the code in the code file at the end. 

## References

1) https://datacatalog.worldbank.org/dataset/world-development-indicators

2) https://worldhappiness.report/

3) https://www.kaggle.com/kmravikumar/how-far-is-china-ahead-of-india

4) https://www.kaggle.com/smondal93/exploring-global-inequality-and-growth
