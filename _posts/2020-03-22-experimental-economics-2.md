---
title: 实验经济学02 - 个体决策与实验设计
date: 2020-03-22 15:31:12
category: 经济学
disqus: y
mathjax: true
---

这一讲有关“个体决策”，实验经济学家设计了几个实验，来测验被试者的风险偏好和时间偏好。但是实验中有种种延伸性的问题，为什么要这么做、不那么做呢？从而引出后半部分的几个“实验设计”原则。

## 个体决策 - 风险偏好

这个实验用来测试一个人对于“风险”的偏好。就像理财产品开户的时候也会让你填一大堆风险偏好的表格，做完测验可以被试者整体的风险偏好是激进、稳健还是保守。

>给你两个选择，你可以选择其中一个：
>
>- A：两个红包，一个装着 100 块，一个装着 1000 块，你只能随机拆一个；
>- B：不用拆红包，直接给你 500 块

这个时候有些激进型的人会选 A，搏一搏，单车变摩托；但很多人会选 B，因为 \\(E(A)=550\\)，比选 B 多不了多少，胜在很稳。

而这里有几个问题：

**1. 效用函数不是线性的**

对于这样的人，为了搞清楚他们进一步的风险偏好，可以把上面的实验改一下数字，改成这样：

> 给你两个选择，你可以选择其中一个：
>
> - A：两个红包，一个是空的，一个装着 3000 块，你只能随机拆一个；
> - B：不用拆红包，直接给你 1000 块

你会选哪个？为什么还有人会选 B，因为对于钱的多少，效用函数并不是线性的，而是平方根的函数：

$$U(x) = x^{(1-r)} = x^{0.5}\text{ (for } r=0.5)$$

所以对于这种不确定的情况，有些人就想还不如落袋为安。

**2. 真的后果与假设性后果不一样**

Holt and Laury 在上面的基础上设计过一组 10 个问题，这组问题会做四次

- 第 1 组：来真的，1 倍报酬（基线标准）
- 第 2 组：假设的，20 倍报酬（或 50 倍，或 90 倍）
- 第 3 组：来真的，20 倍报酬（或 50 倍，或 90 倍）
- 第 4 组：来真的，1 倍报酬（又回到基线标准）

抛掷一枚等概率的 10 面的骰子，选 A 或者 B 能有不同的期望与方差分布。

| 决定    | 选项 A                                  | 选项 B                                 | 你的选择 |
| ------- | --------------------------------------- | -------------------------------------- | -------- |
| 问题 1  | 1：获得 200 元<br />2~10：获得 160 元   | 1：获得 385 元<br />2~10：获得 10 元   |          |
| 问题 2  | 1~2：获得 200 元<br />3~10：获得 160 元 | 1~2：获得 385 元<br />3~10：获得 10 元 |          |
| 问题 3  | 1~3：获得 200 元<br />4~10：获得 160 元 | 1~3：获得 385 元<br />4~10：获得 10 元 |          |
| 问题 4  | 1~4：获得 200 元<br />5~10：获得 160 元 | 1~4：获得 385 元<br />5~10：获得 10 元 |          |
| …       | …                                       | …                                      |          |
| 问题 10 | 1~10：获得 200 元                       | 1~10：获得 385 元                      |          |

大部分人一开始会选 A，因为掷到 1 的概率太小，为了搏一搏 385 元，有 90% 的概率只能拿 10 块钱，还不如稳一点拿 160 元比较好。然后慢慢转到 B，因为最后一题是“必然”获取 200 元或者 385 元，肯定选 B。

如果你是一个风险中立的人，\\(U(x) = x\\)，那么你答题时只会计算期望值，因此 1~4 题会选 A，5~10 题会选 B。而如果你是一个风险厌恶的人，\\(U(x) = x^{0.5}\\)，这个效用函数下，到第 7 题才会开始选择 B。

但当做第二、三组实验的时候，奇怪的事情发生了：假设的 20 倍结果和玩真的 1 倍几乎没有区别

![实验结果](/images/experimental-economics-2-01.png)

而真的 20 倍和 1 倍相比，表现的明显右移。

![效用](/images/experimental-economics-2-02.png)

说明“假设的”和“来真的”会显著的影响人们的风险偏好。

**3. 实验顺序会影响结果**

有的学者对上面 4 组试验的顺序提出了质疑，把顺序颠倒一下会影响结果吗？所以 2005 年的时候  Harrison 等人决定挑战这个结果

![效用](/images/experimental-economics-2-03.png)

结果发现还真的影响，先真后假 6.4 题，先假后真跳到了 6.0。所以最干净的办法其实就是分为两群人，一群做来真的、一群做假设的。

**4. 受试者背景会影响结果**

另外，Holt 和 Laury 分析了受试者的背景，发现了几个影响因素：

1. 收入：收入越高比较不会趋避风险
2. 性别：女性比较厌恶风险，但是乘以 20、50、90 倍的时候，性别差异就越来越不明显了
3. 年龄：中年人比较风险中立
4. 教育程度：受教育程度越高，越风险中立

**5. 风险厌恶和损失厌恶不同**

卡尼曼质疑说，前面的实验只是测量了“风险厌恶”，而没有测量“损失厌恶”，因此他改了一下这个实验

| 决定    | 选项 A                                | 选项 B                                | 你的选择 |
| ------- | ------------------------------------- | ------------------------------------- | -------- |
| 问题 11 | 1~5：获取 60 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 65 元 |          |
| 问题 12 | 1~5：获取 55 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 65 元 |          |
| 问题 13 | 1~5：获取 50 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 65 元 |          |
| 问题 14 | 1~5：获取 45 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 65 元 |          |
| 问题 15 | 1~5：获取 40 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 50 元 |          |
| 问题 16 | 1~5：获取 40 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 45 元 |          |
| 问题 17 | 1~5：获取 35 元<br />6~10：损失 35 元 | 1~5：获取 75 元<br />6~10：损失 40 元 |          |

配合前面的 10 个问题，一共是 17 个问题，可以综合来看被试者的风险和损失偏好。

## 个体决策 - 时间偏好

这个实验可以用于测量时间偏好。

> 有 1000 块钱，你可以选择以下两个选项：
>
> A：1000 块全部今天拿，无利息
>
> B：1000 块钱全部一个月之后拿，支付1%的利息 

更进一步可以出一个表：

| 决定     | 利率 (r) | 第一次拿 (t) | 第二次拿 (t+h) |
| -------- | -------- | ------------ | -------------- |
| 第 1 题  | 0.5%     | 今天         | 4 周后         |
| 第 2 题  | 1.0%     | 今天         | 4 周后         |
| 第 3 题  | 1.5%     | 今天         | 4 周后         |
| 第 4 题  | 2.0%     | 今天         | 4 周后         |
| 第 5 题  | 2.5%     | 今天         | 4 周后         |
| 第 6 题  | 0.5%     | 6 周后       | 10 周后        |
| 第 7 题  | 1.0%     | 6 周后       | 10 周后        |
| 第 8 题  | 1.5%     | 6 周后       | 10 周后        |
| 第 9 题  | 2.0%     | 6 周后       | 10 周后        |
| 第 10 题 | 2.5%     | 6 周后       | 10 周后        |

这就是用来测试当利率要高到什么程度的时候，被试者才愿意放弃现在的享受，把它延迟到未来去。比较前 5 题跟后 5 题的差别，可以判断人对“明日复明日”这个跨期不一致的情况是不是存在，而只看前 5 题或只看后 5 题，可以判断人到底多有耐心。

一般通用的折现方法是指数型折现（Exponential），也就是说每多过一天，那一天的效用比前一天就要多乘以一个 δ：

$$U(c_1, \cdots, c_n, \cdots) = u(c_n) + \sum_{k=1}^\infty{\delta^k·u(c_k)}$$

但这个函数没有跨期不一致的情况，也就是说，我今天打算明天戒烟，明天仍然打算明天戒烟。然而研究证明，人类对于“现在”是看的特别重要，因此折现的行为是“短视近利”的，也就是说今天的效用不变，而所有未来的效用要额外乘以一个系数β，这也称为半双曲型折现（Quasi-Hyperbolic Discounting）：

$$U(c_1, \cdots, c_n, \cdots) = u(c_n) + \beta\sum_{k=1}^\infty{\delta^k·u(c_k)}$$

这个“短视近利”其实是有神经科学上的证据。有科学家在让被试者做决策时，同时用 fMRI 扫描人脑，发现当问题有跟今天有关的时候，β 脑区会活动；当只有未来的时候，比如明天跟后天，δ 脑区会活动。

人类的生理构造就是短视近利的，小孩都会嚷着我要什么要什么，都不能等，如果要等的话要更多奖赏才愿意。耐心其实是后天培养的，成长的过程中，人会变得越来越理性。

## 实验设计原理

由上面的“风险偏好”和“时间偏好”里的几个实验的讲解，可以总结归纳出怎样才是一个受控制的实验环境：

1. **要真实的有后果或真实的诱因**

   “来真的”和“只是假设”，对于人的决策会有巨大的影响

2. **要有好的对照组的设计**

   否则没法证明因果性，例如一个人说他在街上赶长颈鹿，你说完全没看到长颈鹿啊，他说对啊我工作做得好啊！

3. **要随机分组**

   否则老师如果说上课点名，没有来的举手，一看没有人举手，好大家都来了

4. **完全不欺骗受试者，来造成所谓的控制的环境**

   心理学的实验可以欺骗受试者，但是经济学的实验完全不能用“声东击西”这样的手段。

   但是并不是说把所有的资讯都公开，例如模拟市场实验中，交易双方并不知道对方手上的筹码价格。

以下是实验设计的原理，**实验设计“十诫”**

1. **控制、测量或假设**

   最好的情况是能完全控制变因，不能控制的话可以假设（但存在错误假设的可能），

2. **实验说明**

   将实验说明强迫大家念出来，让它成为一个“公共知识”，打消认为“其他人不了解规则”的错觉

3. **匿名性**

   不能让被试者心有顾忌

4. **配对方式与受试者信誉**

   每一个都随机配对，独立试验，不能让受试者建立自己“守信”的形象

5. **金钱诱因**

   通过付钱的办法来产生真实的效果。或者不用钱的办法，比如实验是选一幅画，告诉被试者结束之后可以拿一件印着这幅画的T恤。总之要造成真实的后果。

6. **不同实验的先后次序**

   保险起见，需要把所有次序都做一遍。但是这样成本太高，因此一般是把人群分为 N 组，每组做不同的实验，把相关性完全隔绝干净。

7. **控制风险偏好**

   如果用彩券改成钱，人们会更偏向风险中立

8. **同一 or 不同受试者**

   对照组是我自己还是别人。如果是自己跟自己比，因为背景资料都一模一样，可信度非常高。

9. **实验计量**

   通常会用 Mann Witney Wilcoxon Test + 最大似然估计。可以进行样本外预测，例如用前 15 回合拟合公式，用最后 5 回合来验证。偶尔会用 Markov switching。

10. **不欺骗受试者**

    徙木立信，如果允许欺骗的话，被试者的内心就会有一些斗智的想法，博弈等。这和实验经济学家研究真实的诱因的目的相违背。