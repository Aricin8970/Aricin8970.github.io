---
layout: page
title: "Project 3: Water Safety Risk Indicators"
permalink: /projects/Project3/
categories: [data-science, project]
---

**Predicting Water System Violations with Data Science**

Clean drinking water is something most people expect to have without thinking twice about it. You turn on the faucet, fill a glass, and trust that the water is safe. But behind that trust are thousands of water systems being monitored for possible health risks, including nitrate contamination.

For this project, my team came up with the idea of identifing patterns in nitrate-related water system violations across united state counties. Aiming for a more predicitve question then simply "which counties had violations" we instead asked:

**Can we use county-level water system data to predict whether an area is likely to have a high nitrate violation rate?**

To answer that, we worked with several datasets related to nitrate violations, population served, groundwater systems, and surface-water systems. The first step was to clean and combine the data. Each county has a FIPS code, which acts like a county ID. Because these codes can lose leading zeroes when read into Python,  they were standardized in the code so the datasets could merge correctly. That matters because even a small coding issue like that could cause counties to mismatch or disappear from the final dataset.

After cleaning the data, we created the measure: **violations per 1,000 people served** because raw violation counts can be misleading. A county serving a much larger population might naturally have more recorded violations than a smaller county. By adjusting for population, the project compared counties more fairly.

Then we turned the problem into one of classification. Counties above the median violation rate were labeled as “high violation,” and counties below it were labeled as “not high violation.” A Gradient Boosting Classifier was trained using three main features:

* population served
* percentage of groundwater systems with nitrate violations
* percentage of surface-water systems with nitrate violations

The model achieved an accuracy of about **83.5%**, meaning it correctly classified most counties in the test set. More interesting is that the feature importance showed that the variable "Population served" was by far the strongest predictor, accounting for about **85%** of the model’s decision-making. Groundwater violation percentage contributed about **13%**, while surface-water violation percentage contributed only about **2%**.

At first, this seems to suggest that population served is the key factor, however, since the target variable was calculated using population served, the model’s heavy reliance on population may partly reflect how the violation rate itself was created. In other words, the result is useful, but it is not absolute proof that population causes nitrate violations.

This project helped put into practice all the Data Science we had learned so far: cleaning messy datasets, merging data from multiple sources, engineering a meaningful target variable, training a machine learning model, and interpreting the results in context. More importantly, we were able to use data science to investigate real public-health and infrastructure questions.

The final note is that machine learning helps to identify patterns in water system violations, but as always results require careful communication. A high accuracy score is valuable, but beyond technicality, understanding why the model performs well — and what its limits are — is what turns cool code into a meaningful analysis.

## Dataset
- Source: https://catalog.data.gov/dataset/safe-drinking-water-information-system-sdwis
- Description: [This dataset covers around 160,000 public water systems all around the U.S. and it included monitoring, enforcement, and violation data that was collected by states and then reported to the EPA.]

## Full Essay & Code
- [Click here to read the full essay (PDF)](/assets/files/finalprojectwriteup.pdf)
- [Juypter Notebook Code](/assets/files/DS_Studio_2_Project_3-1.ipynb)

## Results
![Water Violation Poster](/assets/files/Screenshot091634.png)
