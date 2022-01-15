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
categories: ["项目"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---

<!--more-->

## 1.我做了什么

在 2020 年初秋，我与威斯康辛大学麦迪逊分校的Isye专业学生Shaonan Wang合作，参加了由数据科学俱乐部主办的数据挑战赛。任务是对给出的数据集进行预处理，并开发出可能的最佳预测 Statiscal/ML 模型（“最佳”表示最高准确度）

该数据集来自 Kaggle.com，它是基于近 300 名患者（糖尿病、高血压等）的 12 种健康特征，预测心力衰竭导致的死亡。采用 Logistic 回归和随机森林相结合的方法，最终得到了 87% 的随机森林.在模型评价中，我们使用了混淆矩阵和 ROC 曲线。最后，我们做了一个 [analysis report](/pdf/Data_Challenge_Report.pdf)，并向教授和其他团队展示了我们的成果。

## 2.最终结果

{{<admonition type=example title="deliverables">}}
👉 [colab代码](https://github.com/Yumian-Cui/model-prediction/blob/main/DataChallenge_code_Final.ipynb)

👉 [analysis report](/pdf/Data_Challenge_Report.pdf)
{{</admonition>}}

**幻灯片**

{{<gdocs src="https://docs.google.com/presentation/d/e/2PACX-1vSjBFzo1HRnauqDi2yGkKTOSZGejFfRP73K74_4C29nmJDUjXgYLzPIhN7flcWcNaYfsBAhgHgy-xk9/embed?start=false&loop=false&delayms=3000">}}