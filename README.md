# Statistical-Analysis
Inferential Statistics and Regression Analysis are performed to answer Business questions

## Quick Overview

This analysis was conducted with the aim of analysing and understanding the productivity of the employees of a company and how different factors affect the values of the productivity, overtime and consequently the costs of running the company. By preprocessing the data and conducting an Exploratory Data Analysis it was much easier to understand the data and later I could benefit from that by choosing the most appropriate approach for each given context. In this step I could understand even though there were no missing values or duplicates, I had categorical variables that should be converted into numerical variables and my variables were not normally distributed. This had to be then addressed later.

This ipynb file contains the answers and rationale for the business questions. The rationale is given both in the form of markdown and comments. I made my approaches adapted to the context of each problem.      

The Report can be found both at the end of this file and in the Word Document. You can also find the following sections in this file:

* Import Statments - Are located near the title of each section. This is where I import most of the libraries that I ended up using, a few other libraries are imported later on when needed.
* Data Collection/Loading - where I collect the data from the source (csv file) and load it in the form of a Pandas Dataframe
* EDA - where I perform a quick Exploratory Data Analysis in order to better understand the given dataset and select the best way to approach each question making use of the most appropriate resources. This way my approach gets more realistic and suitable for the context of the dataset.
* Questions - The questionas and resolutions for the questions to solve.
* Summary, Conclusions and Disclaimer  (Report) - limitations of the Analysis and wrap up.

## Business Context and Questions
### Business Context
The company believes implemented new machines would reduce the average overtime (in minutes) that the workers will do, which will lead to a cost reduction in the end. They tried it in a group of 200 workers, which shows an average overtime of 6300 minutes. 
#### Question 1
Can we say that the company is right in it's belief?

#### Question 2
What is the real average productivity of these workers each day of the week? Is there any difference between the days? 

#### Question 3
What are the factors that influence employee’s productivity?

## Summary of Analysis
Text report summarizing analysis rationale key points.

This analysis was conducted with the aim of analysing and understanding the productivity of the employees of a company and how different factors affect the values of the productivity, overtime and consequently the costs of running the company. By preprocessing the data and conducting an Exploratory Data Analysis it was much easier to understand the data and later I could benefit from that by choosing the most appropriate approach for each given context. In this step I could understand even though there were no missing values or duplicates, I had categorical variables that should be converted into numerical variables and my variables were not normally distributed. This had to be then addressed later.

The first question answered  was with regards to how the implementation of new machines would benefit the company by reducing the costs associated with the overtimes of the employees. The key here was to understand the question, have a good understanding of the fundamentals and use case of different statistical approaches and properly formulate the hypothesis. Since I wanted to objectively assure whether there was or not enough evidence in the sample to support the belief or claim of the company, knew that I had to perform a one-sample statistical test either t-test or z-test. Here I stumbled across the first hurdle: The data was not normally distributed and as parametric test, t-test and z-test, have some assumptions such as normal distribution of the data, which I knew that the data was not normally distributed due to the EDA performed. However, since my sample size what big enough (200) I could still proceed given that according to the Central Limit Theorem as the sample size increases the data distribution approximates a normal distribution. If that was not the case I could have performed a non-parametric test (Mann-Whitney U Test (McClenaghan, 2024)).

The second question was concerning whether there was any difference between the productivity for each day of the week. Given that I wanted to understand if there was any statistical difference between more than 2 groups ( the 6 days of the week) for one factor (Actual Productivity), I needed to perform a One-Way ANOVA test. However, before performing the ANOVA test I had to ensure 3 factors otherwise the results could not be accurate and correct for the given context and another methods and tests should be utilized. I had to check: Sample Independence; Variables Normal Distribution; Approximate same variance between variables. Then I came across the second hurdle: As per the graph I plotted and can also be found below, each day seems to display a cyclicity which suggests that sample independence may not be fulfilled. Because of the fact that the values for each day behave the same with similar oscillations, and when the minimum values for each oscillation is reached it is followed by a maximum value. This suggest dependence in the samples.

 
Due to this phenomenon, to proceed with the analysis and eventually perform an ANOVA test I had to ignore this and consider the samples independent. But I could rather have performed a non-parametric test instead of the ANOVA test such as the Friedman test (McClenaghan, 2024).

By proceeding with the analysis another hurdle was raised. The data was not normally distributed. To proceed I should have either performed a non-parametric test like the Friedman test or use a function to normalize the distribution of the data such as the logarithmic function or even the square root function depending on my aim. I still conducted the analysis and performed the ANOVA test which revealed there be no significant difference in productivity between the different days of the week. Nevertheless, I knew this values were not the most accurate given the context of the data.

Finally, for the last question selecting the features influencing the most the productivity of the employees and performing regression analysis, was one of the most enjoyable part of this analysis. 
Here, normalising the data would be very beneficial when I create the model but before normalising the features I first had to proceed with the feature selection. This way I could assure that the relationships between the features and target were preserved at the time of the feature selection to later benefit my regression model. I also wanted to check which score function for the SelectKBest class would provide the best feature selection for my model. I knew that according to the visualisations performed before (the scatter plots), the only features that seem to have a linear relationship with the 'actual productivity' feature were the 'incentive' and the 'targeted productivity'. Therefore, I utilized two different feature selection score functions: the ‘f_regression’ for linear relationships and the ‘mutual_info_regression’ for non-linear relationships and see which one would select the best features for my model. I chose ‘mutual_info_regression’ because most of the feature didn’t seem to have a linear relationship with the target variable. The model which performed the best was the Random Forest with the features suggested by the ‘mutual_info_regression’ score function, hyperparameter k=10 and a score of 84.87% of accuracy. 

Overall, the analysis went very well and the aims were attained even though having into consideration that some approaches would have been well beyond the scope of this analysis and as a matter of simplicity and showing accomplishment of the learning outcomes of the module I had to simplify the steps and make assumptions that in a real case shouldn’t have been made and I am cognizant of that. With this analysis I could also understand how critical the choice of our approach is for the success of the analysis.

Thank you!

Jonilson António
