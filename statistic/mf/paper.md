#                             展望理论简述——金融数学课程论文

​																				孔畅	3180104294







## 前言

​		在效用函数理论中，我们研究了一个重要的悖论——圣彼得堡悖论。通过建立不同的效用函数，来表现现实中的边际效用递减、风险厌恶、偏好更多等现象，成功解决了这个悖论。但期望效用理论也引出了更多的悖论，需要新的理论来进行完善。

​		对期望效用理论的各种改进中，最著名的就是Kahneman和Tversky提出的展望理论，也被称为前景理论，甚至由此产生了一门新的学科——行为金融学。本文将简要介绍展望理论以及其应用，说明其主要内容和思想。





## 期望效用理论

​		首先还是先从期望效用理论开始，因为展望理论的出现就是为了解决期望效用理论中存在的问题。

### 圣彼得堡悖论

​		假如有一个游戏，参与者每次投掷一枚硬币，如果硬币在第k次掷出正面，则获得$2^k$元并结束游戏，否则进行下一次投掷。那么很明显这个游戏的期望收益为：

​		$\sum 2^k \frac{1}{2^k} =+\infty $

​		但是参与者肯定不可能愿意支付非常多的代价，例如一万元，来进行这场游戏。这就是著名的圣彼得堡悖论。

​		为了解决这个悖论，Bernoulli在论文中指出，个体决策准则是追求期望效用值的最大化而不是期望财富值的最大化，因而需要考虑到边际效用递减。论文中通过对数期望效用函数解决了这个悖论，他认为个体对于财富的效用是：

​		$u(c)=a*log(c)$

​		从而原先的游戏带来的期望效用是：

​		$E(u(x))=\sum log(2^k) \frac{1}{2^k}=log4$

​		因此参与者至多愿意付4元来进行这个游戏。

​		虽然这个解决方案有很多问题，比如修改规则后就会失效，但为期望效用理论提供了一个良好的例子，从中可以体会到期望效用理论的主要思想。

​		不过随着期望效用理论的传播，又出现了新的关于期望效用理论的悖论，例如Allais悖论，Ellsberg问题和偏好反转现象。

### Allais悖论

​		考虑下面两组问题：

​		$A_1$：直接获得100万美元；

​		$A_2$：以0.1的概率获得500万美元，0.89的概率获得100万美元，0.01的概率获得0美元；

​		$B_1$：以0.1的概率获得500万美元，0.9的概率获得0美元；

​		$B_2$：以0.11的概率获得100万美元，0.89的概率获得0美元；

​		通过实验，大部分人会选择$A_1$和$B_1$，因为人们相对于可能的一无所获更希望直接获得100万美元，500万美元的选项存在着边际效用递减。而另一个选择中，$B_1$的预期收益明显要高于$B_2$。于是我们用$x_5,x_1,x_0$分别表示人们获得500万美元，获得100万美元，获得0美元的期望效用，可以得到：

​		$A_1 :x_1$

​		$A_2:0.1x_5 +0.89x_1 +0.01x_0$

​		由独立性公理得出：

​		$x_1 >\frac{1}{11}x_0 +\frac{10}{11}x_5$

​		再考虑另一个选择，可以得出：

​		$B_1:0.1x_5+0.9x_0$

​		$B_2:0.11x_1+0.89x0$

​		$x_1 <\frac{1}{11}x_0 +\frac{10}{11}x_5$

​		前后显然矛盾，期望效用理论出现漏洞。Allais悖论说明了人们相比于不确定性更偏向于确定性，也被称为确定性效应。

### Ellsberg问题

​		假设有100个球，被涂成黑白两色，考虑以下两个赌博：

​		$E_1$：已知黑白颜色各有50个球，参与者选择一种颜色，然后随机抽取一个球，如果颜色相同就获得1万美元，否则一无所获。

​		$E_2$：不知道黑白球的各自数量，其余同上。

​		实验表明大部分人会选择$E_1$，但根据期望效用理论二者的偏好应当是一样的。

### 偏好反转现象

​		考虑如下两个随机计划：

​		$P$：以概率$\frac{35}{36}$获得4美元，以概率$\frac{1}{36} $损失1美元。

​		$Q$：以概率$\frac{11}{36}$获得16美元，以概率$\frac{25}{36}$损失1.5美元。

​		在实验中，大部分人都愿意选择P，但是如果让他们对二者进行最低定价，绝大多数人选择Q比P更贵。记$A_P,A_Q$为二者的最低定价，我们有：

​		$P>Q$

​		$A_P$ ~ $P$ , $A_Q$ ~ $Q$

​		$A_P<A_Q$

​		这显然与偏好关系的传递性矛盾。

​		这些例子都表明期望效用理论虽然非常漂亮，但在现实中并不完全适用，我们需要一种更加完善的理论来解释人们的选择。







## 展望理论

### 股票市场中的“追涨杀跌”

​		先让我们举一个例子，如果有一支股票某天开盘价格10元/股，当天波动下跌，收盘时变成了5元/股，那么你会愿意在收盘时买入该股票吗？

​		大部分人都不会愿意。类似的例子还有股票涨停后大量个人投资者继续买进，也就是俗话说的“追涨杀跌”。

​		那么请思考以下几个问题：

​		1、为什么在股票涨停后，个人投资者会更倾向于继续持有，甚至是加仓买进股票呢？是什么让他们期待更高的股价呢？

​		2、突然涨停这一事件对于不同投资者的决策造成了怎样的影响？

​		3、如果是跌停，和涨停相比会有什么不同吗？反映出了怎样的风险态度？

### 风险决策过程与价值函数

​		在一般的期望效用理论中，投资者是严格风险厌恶的，因此期望效用函数是一个严格的凹函数。随后马科维茨定义了一个通用财富，作为期望效用函数的拐点，从而使得期望效用函数在整体下凹的趋势上，局部凹凸性不确定。

​		在马科维茨的通用财富理论基础之上，Kahneman和Tversky构造了价值函数，并以此为基础提出了展望理论。

​		Kahneman和Tversky认为，个人风险条件下的决策过程分为两个阶段：编辑阶段和估值阶段。

​		编辑阶段会进行编码、合成、剥离、相抵、化简、占优检查等过程，然后决策者会在估值阶段将被编辑期望的全部价值$V$，用两个主观量度$\pi ,v$来表达。

​		其中$\pi$表示与概率p相对应的决策权重，即$\pi (p)$，反映了概率p对于全部价值的影响力，也就是主观概率。

​		$v$则用来反映主观价值，通过确立一个参考点，根据$v(x)$偏离参考点的程度表示收益或损失的大小。

​		Kahneman和Tversky参考了Allais悖论的实验，在1979年做了一个类似的实验：

​		$A_1$：直接获得2000美元；

​		$A_2$：以0.5的概率获得4000美元，0.5的概率获得0美元。

​		同Allais的实验结果一样，人们大多数选择$A_1$，但之后二人又进行了一个对称实验：

​		$A_1$：直接损失2000美元；

​		$A_2$：以0.5的概率损失4000美元，0.5的概率损失0美元。

​		这一次大部分人选择了$A_2$，并没有表现出期望效用理论中的风险厌恶。

​		通过不断改变实验参数，Kahneman和Tversky得出了以下结论：

​		1、价值函数应当以一个参考点为基准，划分成收益和损失两种不同的情况。

​		2、在收益区域内，人们往往表现出风险厌恶；而在损失区域内，人们往往寻求风险偏好。

​		3、价值函数在损失区域表现出的斜率要远大于收益区域，即损失1000美元带来的痛苦远超获得1000美元的快乐，前者大约是后者的2.5倍。

​		根据实验结果，Kahneman和Tversky还提出了价值函数的具体指数形式：

​		$v(x)=x^{\alpha},x\geq0$（即收益区域）

​		$v(x)=-\lambda (-x)^{\beta}$（即损失区域）

​		$0<\alpha <\beta <1,\lambda >0$

### 价值函数的参考点

​		Kahneman和Tversky所提出的展望理论中，价值函数与期望效用理论中的期望效用函数最大的不同之处，就在于价值函数存在一个拐点，即参考点。价值函数被参考点划分成收益区域和损失区域，这里的收益与损失并不是绝对的收益与损失，而是一种人的主观评价，不同事物、不同决策人之间各不相同。

​		例如假设有两家商店举办活动，A和B分别前往一家商店。A得知第10000位顾客获得了10000元，而自己是第10001位顾客，从而获得了150元。B则在另一家商店得知自己是第10000位顾客获得了100元。那么A和B谁会觉得自己的收益更大呢？大部分人都会觉得是B，这也就是参考点的存在意义。

​		同样还有一个著名实验：

​		$A$：先获得30元，再选择是否抛一次硬币，正面则再得到9元，否则失去9元。

​		$B$：选择是否抛一次硬币，正面则得到39元，否则得到21元，若不抛硬币则得到30元。

​		在A中选择抛硬币的人数要远远少于在B中选择抛硬币的人数，这也体现了参考点的作用。

​		价值函数和其参考点的出现，使得人们将研究目标从绝对收益转向了相对效益，同时指出了收益与损失之间的差异，以及价值函数的斜率不连续性。

​		价值函数表现出三大心理特征：

​		1、价值函数具有参考点，即人们对于收益的度量取决于相对收益。

​		2、价值函数为S型，即人们在面对收益和损失时展现出不同的风险态度。

​		3、价值函数在损失区域的斜率更大，即人们更不愿意受到损失。

### 决策权重函数

​		展望理论的另一大重要内容就是决策权重函数$\pi (p)$。

​		通过实验表明，大多数人的决策权重函数呈现倒S型，即高估低概率事件，低估高概率事件。但在概率接近0或1时，又倾向于直接将其视为0或1。

​		决策权重函数有着四个重要的特点：

​		1、高估小概率事件及其劣可加性（subadditive）。

​		2、各互补概率事件的决策权重之和小于确定性事件，即次确定性（subcertainty）。

​		3、概率比一定时，大概率对应权重比率小于小概率对应权重比率，即次比率性（subproportionality）。

​		4、在接近概率边界（0或1）时，决策权重发生突变，被忽视为0或放大为1，即端点不良性。

​		就拿概率性保险来举个例子：假设保险公司设计了一种新的保险，只需要付出一半的保费，在意外发生后，保险公司有50%的概率进行全额赔付，另外50%的概率退还保费。这种保险显然并不会受到大多数人的欢迎，就是因为决策权重函数$\pi(p)\ne p$。

### 展望理论与行为金融学

​		在提出了价值函数和决策权重函数后，Kahneman和Tversky设计出了展望理论，通过两个函数的乘积求和来决定决策的偏好：

​		$V=\sum \pi(p) v(x)$

​		其中p是对应情况x的发生概率，$\pi,v$分别是决策权重函数和价值函数。

​		而在Kahneman和Tversky之后，许多学者投入了展望理论的研究中，逐渐产生了一门新的学科——行为金融学。行为金融学在数学理论的基础上，更多地考虑现实世界中多变的因素，结合当代心理学进行分析，推动了现代金融的发展。

