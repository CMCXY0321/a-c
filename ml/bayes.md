#### 基于成分
新观察到的样本信息将修正人们曾经对事物的认知

- 频率派把须要判断的參数θ看做是固定的未知常数。即概率尽管是未知的，但最起码是确定的一个值，同一时候，样本X 是随机的，所以频率派重点研究样本空间，大部分的概率计算都是针对样本X 的分布
- 而贝叶斯派的观点则截然相反。他们觉得參数是随机变量，而样本X 是固定的，由于样本是固定的，所以他们重点研究的是參数的分布

#### 应用：拼写检查
用户输入一个单词时，可能拼写正确，也可能拼写错误。
假设把拼写正确的情况记做c（代表correct），拼写错误的情况记做w（代表wrong），那么"拼写检查"要做的事情就是：在发生w的情况下。
试图判断出c。换言之：已知w，然后在若干个备选方案中，找出可能性最大的那个c。
P(c|w) = P(w|c)*P(c)/P(w)

- P(c)表示某个正确的词的出现"概率"。它能够用"频率"取代
- P(w|c)表示在试图拼写c的情况下，出现拼写错误w的概率

#### 贝叶斯网络
贝叶斯网络(Bayesian network)，又称信念网络(Belief Network)，或有向无环图模型(directed acyclic graphical model)，是一种概率图模型，它是一种模拟人类推理过程中因果关系的不确定性处理模型，其网络拓朴结构是一个有向无环图(DAG)

#### 贝叶斯决策
贝叶斯决策主要包含四个部分： 数据（D）、假设（W）、目标（O）、决策（S）

- 理清因果链条，哪个是假设，哪个是证据
- 给出所有可能假设，即假设空间
- 给出先验概率
- 根据贝叶斯概率公式求解后验概率，得到假设空间的后验概率分布
- 利用后验概率求解条件期望，得到条件期望最大值对应的行为

贝叶斯决策如果一旦变成自动化的计算机算法，它就是机器学习
