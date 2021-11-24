---
weight: 4
title: "心力衰竭死亡预测项目-Data Challenge 2020"
date: 2020-11-05T01:44:15-06:00
lastmod: 2021-11-19T01:44:15-06:00
draft: false

description: "我在 UW-Madison Data Science Club 主办的 Data Challenge 中的项目概述"
# resources:
# - name: "featured-image"
#   src: "featured-image.png"

tags: ["机器学习", "统计", "数据分析", "Python"]
categories: ["projects"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---

<!--more-->

In Junior Fall 2020, I collaborated with Shaonan Wang, an ISYE major at UW-Madison, on the Data Challenge hosted by Data Science Club. The task was to preprocess the dataset given and develop best prediction statiscal/ML models possible ("best" means highest accuracy) 

The dataset came from Kaggle.com, about predicting death due to heart failure based on twelve health characteristics on almost 300 patients (diabetes, high blood pressure, etc.). We applied Logistic Regression and Random Forest, with the latter achieving 87% at the end. For model evaluation, we used confusion matrix and ROC curve. Finally, we did an [analysis report](/pdf/Data_Challenge_Report.pdf) and presented our findings to professors and other teams ([slides](/pdf/Presentation.pdf)).