---
toc: true
layout: post
description:
categories: [journal]
---
# Machine Learning as a Service vs Feature – BigML vs. Infer

This is a personal follow-up for the LA Machine Learning meetup, David Gerster @ eHarmony on October 8th, 2013.

David Gerster, VP of Data Science at BigML, also former Director of Data Science at Groupon, gave an overview of BigML’s Machine Learning (ML) platform for predictive analytics. Here are my thoughts about its business model and other alternatives offering ML.

# BigML

[![](https://img.youtube.com/vi/JVM8qIn3xPQ/0.jpg)](https://youtu.be/JVM8qIn3xPQ)

BigML offers, so called, Machine-Learning-as-a-Service (MLaaS), that allows users (ex. a wine seller) to upload their data (ex. historical wine sales data) to BigML and get predictions for the variable of interest (ex. right prices for new wines, expected sales number for future) while keeping users from complicated Machine Learning algorithms, which are key components of predictive analytics.

# Machine Learning as a Service

As of November 2013, there are a few start-up companies + Google offering (or claiming to offer) MLaaS other than BigML:

* Algorithms.io
* SnapAnalytx
* wise.io
* Predixion Software
* Google Prediction API

It is similar to Analytics-as-a-Service (AaaS) in a way that it delivers the power of predictive analytics to users, but it is different from AaaS in a way that it leaves data ETL (Extract-Transform-Load) and problem identification steps to users.

The pros and cons of MLaaS over AaaS would be:

* Pros – Cheaper: $150-300 / month for MLaaS from BigML vs. $200-300 / hour / person (+ hardware, licensing fees) for AaaS from analytics consulting firms
* Cons – Harder: ETL and problem identification are by far the hardest parts in predictive modeling.  No matter how good your algorithm is, garbage-in leads garbage-out (ETL), and aiming wrong target leads wrong predictions (problem definition).

If you know what you’d like to predict and how to clean up your data, then MLaaS would be the right solution for you.  However, for many prospective users of MLaaS (those who are inexperienced in data analytics), I guess that it’s not the case.

# Machine-Learning-as-a-Feature, Infer.com

Another business model other than MLaaS and AaaS to provide users with the power of ML for their predictive modeling needs is Machine-Learning-as-a-Feature (MLaaF, Don’t google it.  I just made it up).

Infer, a startup founded in 2010, is on this track, and offers ML plugins for popular CRM softwares (Salesforce, Marketo and Eloqua) to predict sales leads.

[![](https://img.youtube.com/vi/AGwDuOU9sbU/0.jpg)](https://youtu.be/AGwDuOU9sbU)

By focusing on the specific need (sales lead prediction) and  specific users (those who use popular CRM softwares), Infer manages to provide the power of ML with the painless user experience and affordable price tag.

# Closing Thought

To be fair, BigML’s user interface and visualization are quite impressive, and it is equipped with the Random Forest algorithm, which is one of most popular algorithms with good out-of-the-box performance.  For data scientists who do not have much ML experience, it will be worth to try out.

However, I believe that for most of users, it will work best with well defined MLaaF rather than MLaaS (Investors seem to agree with me based on the fact that Infer got 10M in funding compared to BigML got 1M from CrunchBase profiles).