---
weight: 1
title: "Write an ANN from Scratch Part I : Perceptron"
date: 2020-08-09T01:44:15-06:00
lastmod: 2021-11-22T01:44:15-06:00
draft: false

description: "Adapted from Data Science Enthusiast Nagesh's tutorial about writing NN in Python"
# resources:
# - name: "featured-image"
#   src: "featured-image.jpg"

tags: ["Python", "ANN", "Neural Network"]
categories: ["projects"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---

<!--more-->
<!-- Independent project via Python in Summer 2020 EconEx externship -->

## Please view my work here!

Please checkout this Github Gist => <script src="https://gist.github.com/Yumian-Cui/ad4b1b9187fc5e36d4d53a75e4875c8e.js"></script>

To run the Colab just like I did, please click [here](https://colab.research.google.com/drive/1vcyY0qq-3jpmuG7UHAVEsctV7-WZpe-8?usp=sharing#scrollTo=Fmd55Zzd0Oyj)🙂. 

Special thanks to [Nagesh's tutorial](https://www.kdnuggets.com/2019/11/build-artificial-neural-network-scratch-part-1.html) which did an excellent job in explaining neural network in simple manners. Click to view part I of his tutorial series. 

## Explanation about Gradient Descent

I quite like Nagesh's explanation about gradient descent, which really illuminates the concept. I'm happy to reiterate it here as a refresher. 

Recall the formula: $$w = w - \alpha (\frac{\partial F}{\partial w})$$

$\frac{\partial F}{\partial w}$ is the gradient of the loss F with respect to the weight w, which, to put simply, translates to rate change of the loss with the change of the weight and in 2-D term the slope. If the loss increases as weight increases, $\frac{\partial F}{\partial w}$ would be a positive value which is then subtracted from w by the amount $\alpha (\frac{\partial F}{\partial w})$, to go in the opposite direction of the gradient. The same applies if the loss decreases as weight increases: it means $\frac{\partial F}{\partial w}$ is a negative value which we in effect (minus a negative value) add the amount $\alpha (\frac{\partial F}{\partial w})$ to w. Either way, the goal is to push w in the direction that causes most rapid decline in F, the cost function we're interested in minimizing. 