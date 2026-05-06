---
layout: page
title: "Project 3: Water Safety Risk Indicators"
permalink: /projects/Project3/
categories: [data-science, project]
---

**Predicting Water System Violations with Data Science**

Clean drinking water is something most people expect to have without thinking twice about it. It is as simple as pouring faucet water into a cup and trusting that the water is safe. But behind that trust are thousands of public water systems being monitored for possible health risks, including nitrate contamination.

For this project, my team came up with the idea of identifing patterns in nitrate-related water system violations across united state counties. Aiming for a more predicitve question then simply "which counties had violations" we instead asked:

**Can machine learning help identify counties that may be at higher risk for nitrate-related water system violations?**

To answer that, we worked with several datasets related to nitrate violations, population served, groundwater systems, and surface-water systems. The first step was to clean and combine the data. Each county has a FIPS code, which acts like a county ID. Because these codes can lose leading zeroes when read into Python, they were standardized in the code so the datasets could merge correctly. That matters because even a small coding issue like that could cause counties to mismatch or disappear from the final dataset.

After cleaning the data, we created a more meaningful measure: **violations per 1,000 people served**. Raw violation counts can be misleading because larger counties or systems may naturally have more recorded violations simply because they serve more people. Adjusting by population helped us compare counties more fairly. Counties above the **75th percentile** in violations per 1,000 people were labeled as high risk, making the highest-risk quarter of counties the focus of the supervised models.

We compared multiple machine learning approaches. Random Forest served as a baseline model, while Gradient Boosting was used because it builds decision trees sequentially, with each new tree trying to improve on the mistakes of the previous ones. We also used K-Means Clustering to group counties based on similar characteristics rather than simply labeling them as high or low risk.

The supervised models were evaluated using accuracy, recall, F1-score, and ROC-AUC. Random Forest had slightly higher overall accuracy at **68.2%**, but it only identified **31%** of true high-risk counties. Gradient Boosting had slightly lower accuracy at **65.9%**, but it identified **69%** of true high-risk counties and achieved a higher ROC-AUC of **0.705**.

That tradeoff was one of the newest and most valuable part of this project. In a public-health context, the best model is not always the one with the highest overall accuracy. If the goal is to detect high-risk water systems, then missing a truly high-risk county is more concerning than flagging an extra county for review. Because Gradient Boosting caught far more true high-risk counties, it was the more useful model for this project.

K-Means Clustering added another layer of insight. It grouped counties into four categories based on population served, groundwater violation percentage, surface-water violation percentage, and violations per 1,000 people. The most concerning group was made up of smaller-population counties with the highest violation rates per 1,000 people. This is important because smaller and more rural communities can be overlooked when analysis focuses only on raw numbers or large population centers.

The project also showed the limits of data. The dataset relies on state-reported information, and reporting gaps created major blind spots. Some areas, especially rural and lower-income regions, had limited available data. That means the absence of reported violations does not necessarily mean the absence of risk. In some cases, missing data may itself point to communities with fewer resources, less monitoring, or weaker compliance infrastructure.

Ultimately our group practiced the full data science workflow: cleaning messy data, merging multiple datasets, engineering a meaningful target variable, building classification models, evaluating performance beyond accuracy, creating geographic visualizations, and interpreting results responsibly.

The takeaway was that machine learning can help reveal patterns in public-health and infrastructure data, but that the models aren't everything. A strong result is useful, but understanding what the model misses, what the data leaves out, and how the results could affect real communities is what turns cool looking code into a meaningful analysis.

## Dataset
- Source: https://catalog.data.gov/dataset/safe-drinking-water-information-system-sdwis
- Description: [This dataset covers around 160,000 public water systems all around the U.S. and it included monitoring, enforcement, and violation data that was collected by states and then reported to the EPA.]

## Full Essay & Code
- [Click here to read the full essay (PDF)](/assets/files/finalprojectwriteup.pdf)
- [Juypter Notebook Code](/assets/files/DS_Studio_2_Project_3-1.html)

## Results
![Water Violation Poster](/assets/files/Screenshot091634.png)
