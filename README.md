# Chicago Motor Vehicle Theft Analysis (2026)
Authors: Thuy, Trian, Puru, Zac
This repository contains a Bayesian statistical analysis of motor vehicle thefts (MVT) in Chicago. Using 2026 crime data, we explore temporal patterns, daily volume predictions, and geographical risk factors to provide a "worst-case benchmark" for vehicle crime in the United States.
## Project Overview
With approximately 1 million vehicles stolen annually in the US, car theft remains a significant concern. This project investigates whether vehicles in Chicago are susceptible targets by breaking the research into four core questions
1. What is the probability that a theft occurs at night?
2. How many vehicles are expected to be stolen on any given day?
3. Which community areas face the highest probability of theft?
4. Do arrest rates for vehicle thefts vary significantly by district?
## Methodology & Models
1. Temporal Analysis (Beta-Binomial)
We investigated the "Night vs. Day" theft split using a Beta-Binomial model.
Prior: $Beta(104, 96)$ based on FBI national statistics (~52% night-time rate).
Findings: The posterior probability that a theft occurs at night ($6\text{pm} - 6\text{am}$) is approximately 0.574.
2. Daily Count Prediction (Gamma-Poisson)
To predict the number of thefts tomorrow, we modeled daily counts as independent Poisson variables.
Prior: $Gamma(6.2116, 0.1011)$ derived from Chicago's historical annual averages.
Posterior Predictive: With 95% probability, between 33 and 59 cars will be stolen in Chicago tomorrow, with a mean prediction of 45.57.
3. Community Risk Assessment
We calculated the probability of at least one theft occurring in specific community areas using a Gamma-Poisson hierarchical approach.
Top Risk Areas:
* Near West Side (28): 90.8% probability of $\ge 1$ theft tomorrow.
* West Town (24): 88.8% probability.
* Austin (25): 86.8% probability.
5. Arrest Rate Variability
Using a Beta-Binomial model, we compared the probability of arrest ($\pi_j$) across different police districts.
Prior: $Beta(2, 18)$ based on the national 10% arrest rate.
Comparison: We utilized pairwise posterior sampling and heatmaps to demonstrate that arrest rates differ with statistical significance between districts.
## Technologies UsedLanguage: RFormat: Revealjs (Quarto/RMarkdown)
Key Libraries: 
* tidyverse & ggplot2 (Data visualization)
* bayesrules (Bayesian toolkit)
* lubridate (Date-time manipulation)
## Data SourceThe analysis utilizes chicago_vehicle_theft_crimes_2026.csv, which includes timestamps, community areas, and arrest flags for motor vehicle thefts in Chicago.
Note: This analysis serves as a benchmark for law enforcement and insurance risk assessment. 
Limitations include a need for higher-resolution (hour-by-hour) analysis and hierarchical spatial modeling.
## How to Run
Ensure you have R and RStudio installed
.Clone this repository
.Open the .qmd or .Rmd file
.Render the file to view the Revealjs presentation:
