---
title: "A/B Testing"
excerpt: "Identify changes that lead to improvements"
categories:
  - portfolio
tags:
  - data science
  - python
  - causal inference
  - machine learning

---
![AB Testing](/assets/images/portfolio/Slide2.JPG)  
A/B testing, also known as split testing, is a common practice in marketing ad campaigns aimed at optimizing conversion rates and maximizing performance. It involves comparing two versions of a marketing asset, such as an advertisement or a landing page, by randomly assigning users to one of the versions and measuring their response. By analyzing the results, marketers can identify which version performs better in terms of predefined metrics, such as click-through rates, conversion rates, or user engagement. A/B testing provides valuable insights into the effectiveness of different marketing strategies, allowing marketers to make data-driven decisions and refine their campaigns to achieve the desired outcomes.

### Example: A/B Testing on an ad-campaign
In this notebook, I demonstrate an A/B testing using Python for an example ad campaign dataset on Kaggle where the majority of the people will be exposed to ads (the experimental group). And a small portion of people (the control group) would instead see a Public Service Announcement (PSA) (or nothing) in the exact size and place the ad would normally be.

The idea of the dataset is to analyze the groups, find if the ads were successful, how much the company can make from the ads, and if the difference between the groups is statistically significant.

### Example: A/B Testing for a Travel site: Imperfect Compliance
An online business would like to test a new feature or offering of their website and learn its effect on downstream revenue. Furthermore, they would like to know which kind of users respond best to the new version. We call the user-specfic effect a heterogeneous treatment effect.

Ideally, the business would run an A/B tests between the old and new versions of the website. However, a direct A/B test might not work because the business cannot force the customers to take the new offering. Measuring the effect in this way will be misleading since not every customer exposed to the new offering will take it.

The business also cannot look directly at existing data as it will be biased: the users who use the latest website features are most likely the ones who are very engaged on the website and hence spend more on the company's products to begin with. Estimating the effect this way would be overly optimistic.

In this customer scenario walkthough, we show how tools from the `EconML` library can still use a direct A/B test and mitigate these shortcomings.

[Code](https://github.com/chaix026/A-B-Testing){: .btn .btn--success .btn--large}

