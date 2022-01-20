# 从头开始写一个人工神经网络第一部分：感知器


<!--more-->
<!-- Independent project via Python in Summer 2020 EconEx externship -->
## 请查看代码！

请查看 Github Gist => <script src="https://gist.github.com/Yumian-Cui/8eb25b27e1bf5440a8bd1de63a632341.js"></script>

要像我一样运行Colab，请访问[这里](https://colab.research.google.com/drive/1vcyY0qq-3jpmuG7UHAVEsctV7-WZpe-8?usp=sharing#scrollTo=Fmd55Zzd0Oyj)🙂。

特别感谢[Nagesh 的教程](https://www.kdnuggets.com/2019/11/build-artificial-neural-network-scratch-part-1.html)非常简单易懂地解释了神经网络，点击查看教程系列的第一部分。

## 关于梯度下降的解释

我很喜欢 Nagesh 关于梯度下降的解释，让我看到觉得醍醐灌顶。我很高兴在此复述，作为一次小小复习。

回想公式: $$ w=w-\alpha（\frac{\partial F}{\partial w}）$$

$\frac{\partial F}{\partial w}$ 是损失 F 相对于参数 w 的梯度，简单地说，它可以理解为为损失随参数 w 的变化而变化的速率，在 2-D 下称之为斜率。如果损失随着参数 w 的增加而增加，$\frac{\partial F}{\partial w}$ 将是一个正值，然后将其从 w 中减去相应值 $\alpha (\frac{\partial F}{\partial w})$，以沿梯度的相反方向前进。如果损失随着参数 w 的增加而减少，也同样适用:这意味着 $\frac{\partial F}{\partial w}$ 是一个负值，我们实际上（减去一个负值）加了 $\alpha (\frac{\partial F}{\partial w})$ 到 w。，我们的目标是将 w 推向让 F，我们感兴趣最小化的损失函数，最快下降的方向。


