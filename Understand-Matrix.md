<a name="content">目录</a>

[【整理·非原创】理解矩阵](#title)
- [1. 我们对于矩阵的种种疑惑——本质是线性代数教学中直觉性丧失](#questions-about-matrix)
- [2. 对线形空间和矩阵的几个核心概念的理解](#understand-linear-space-and-matrix)
	- [2.1. 什么是空间](#what-is-space)
	- [2.2. 线性空间与线性空间运动的表示方式——矩阵](#linear-space-and-linear-transformation)
	- [2.3. 进一步辨析”矩阵是运动的描述”：引出变换](#precise-definition-of-matrix-movement)
	- [2.4. 理解“矩阵是线性空间中的线性变换的一个描述”](#understand-linear-transformation)
		- [2.4.1. 什么是线性变换](#what-is-linear-transformation)
		- [2.4.2. 什么是基](#what-is-base)
		- [2.4.3. 区别“线性变换”与“线性变换的一个描述”](#seperate-linear-transformation-and-its-description)
- [3. 对1、2的总结及引出下一部分](#summary-above)
- [4. 将矩阵当作对一组基（坐标系）的描述](#regard-matrix-as-description-of-bases)
	- [4.1. 为什么可以将矩阵看作坐标系](#why-can-regard-matrix-as-description-of-base)
	- [4.2. 比较运动视角与坐标系视角下的矩阵](#compare-2-views-to-matrix)
	- [4.3. 重新理解向量](#understand-vector-again)
	- [4.4. 回头理解“固定坐标系下一个对象的变换等价于固定对象所处的坐标系变换”](#remind-coordinates-transformation)

<h1 name="title">【整理·非原创】理解矩阵</h1>

<p align="center"><img src=./picture/Understand-Matrix-1.jpg width=600 /></p>

“如果不熟悉线性代数的概念，要去学习自然科学，现在看来就和文盲差不多”

“按照现行的国际标准，线性代数是通过公理化来表述的，它是第二代数学模型，...，这就带来了教学上的困难”

<p align="right">——瑞典数学家Lars Garding《Encounter with Mathematics》</p>

当我们开始学习线性代数的时候，不知不觉就进入了**“第二代数学模型”**的范畴当中，这意味着数学的表述方式和抽象性有了一次全面的进化，对于从小一直在“第一代数学模型”，即以实用为导向的、具体的数学模型中学习的我们来说，在没有并明确告知的情况下进行如此剧烈的paradigm shift，不感到困难才是奇怪的。

<a name="questions-about-matrix"><h2>1. 我们对于矩阵的种种疑惑——本质是线性代数教学中直觉性丧失 [<sup>目录</sup>](#content)</h2></a>

对于矩阵的一些基础问题：

> （1）矩阵究竟是什么东西？向量可以被认为是具有n个相互独立的性质（维度）的对象的表示，矩阵又是什么呢？我们如果认为矩阵是一组列（行）向量组成的新的复合向量的展开式，那么为什么这种展开式具有如此广泛的应用？特别是，为什么偏偏二维的展开式如此有用？如果矩阵中每一个元素又是一个向量，那么我们再展开一次，变成三维的立方阵，是不是更有用？
> 
> （2）矩阵的乘法规则究竟为什么这样规定？为什么这样一种怪异的乘法规则却能够在实践中发挥如此巨大的功效？很多看上去似乎是完全不相关的问题，最后竟然都归结到矩阵的乘法，这难道不是很奇妙的事情？难道在矩阵乘法那看上去莫名其妙的规则下面，包含着世界的某些本质规律？如果是的话，这些本质规律是什么？
> 
> （3） 行列式究竟是一个什么东西？为什么会有如此怪异的计算规则？行列式与其对应方阵本质上是什么关系？为什么只有方阵才有对应的行列式，而一般矩阵就没有（不要觉得这个问题很蠢，如果必要，针对m x n矩阵定义行列式不是做不到的，之所以不做，是因为没有这个必要，但是为什么没有这个必要）？而且，行列式的计算规则，看上去跟矩阵的任何计算规则都没有直观的联系，为什么又在很多方面决定了矩阵的性质？难道这一切仅是巧合？
> 
> （4）矩阵为什么可以分块计算？分块计算这件事情看上去是那么随意，为什么竟是可行的？
> 
> （5）对于矩阵转置运算AT，有(AB)T = BTAT，对于矩阵求逆运算A-1，有(AB)-1 = B-1A-1。两个看上去完全没有什么关系的运算，为什么有着类似的性质？这仅仅是巧合吗？
> 
> （6）为什么说P-1AP得到的矩阵与A矩阵“相似”？这里的“相似”是什么意思？
> 
> （7）特征值和特征向量的本质是什么？它们定义就让人很惊讶，因为Ax =λx，一个诺大的矩阵的效应，竟然不过相当于一个小小的数λ，确实有点奇妙。但何至于用“特征”甚至“本征”来界定？它们刻划的究竟是什么？

这样的问题如果不能获得回答，线性代数对于我们来说就是一个**粗暴的、不讲道理的、莫名其妙的规则集合**，我们会感到，自己并不是在学习一门学问，而是被不由分说地“抛到”一个强制的世界中，只是在考试的皮鞭挥舞之下被迫赶路，全然无法领略其中的美妙、和谐与统一。

之所以会存在这么多的为什么，很大原因是**线性代数教学中直觉性丧失**的后果，即知其然不知其所以然

> 上述这些涉及到“如何能”、“怎么会”的问题，虽然能够通过数学性证明来回答，但并不能够让提问者的疑惑得到解决
> 
> 比如对于“矩阵为什么可以分块计算”这个问题
> 
> 提问者其实真正的疑惑是在于：矩阵分块运算为什么竟然是可行的？究竟只是凑巧，还是说这是由矩阵这种对象的某种本质所必然决定的？如果是后者，那么矩阵的这些本质是什么？

<a name="understand-linear-space-and-matrix"><h2>2. 对线形空间和矩阵的几个核心概念的理解 [<sup>目录</sup>](#content)</h2></a>

<a name="what-is-space"><h3>2.1. 什么是空间 [<sup>目录</sup>](#content)</h3></a>

空间有很多种。你要是去看某种空间的数学定义，大致都是“存在一个集合，在这个集合上定义某某概念，然后满足某些性质”，就可以被称为空间，即用“空间”来称呼一些具有某些特性的集合

我们一般人最熟悉的空间，毫无疑问就是我们生活在其中的（按照牛顿的绝对时空观）的三维空间，从数学上说，这是一个三维的欧几里德空间

我们先不管那么多，先看看我们熟悉的这样一个空间有些什么最基本的特点。仔细想想我们就会知道，这个三维的空间：

> - 由很多（实际上是无穷多个）位置点组成；
> - 这些点之间存在相对的关系；
> - 可以在空间中定义长度、角度；
> - **这个空间可以容纳运动，这里我们所说的运动是从一个点到另一个点的移动（变换），而不是微积分意义上的“连续”性的运动**；

上面的这些性质中，最最关键的是第4条：**容纳运动是空间的本质特征**

认识到了这些，我们就可以把我们关于三维空间的认识扩展到其他的空间：

> 不管是什么空间，都必须容纳和支持在其中发生的符合规则的运动（变换）
> 
> 在某种空间中往往会存在一种相对应的变换：
> 
> - 拓扑空间中有拓扑变换；
> - 线性空间中有线性变换；
> - 仿射空间中有仿射变换；
> 
> 其实这些变换都只不过是对应空间中允许的运动形式而已

**“空间”是容纳运动的一个对象集合，而变换则规定了对应空间的运动**

<a name="linear-space-and-linear-transformation"><h3>2.2. 线性空间与线性变换的表示方式——矩阵 [<sup>目录</sup>](#content)</h3></a>

既然我们承认线性空间是个空间，那么有两个最基本的问题必须首先得到解决，那就是：

- 空间是一个对象集合，线性空间也是空间，所以也是一个对象集合。那么线性空间是什么样的对象的集合？或者说，线性空间中的对象有什么共同点吗？

	> **线性空间中的任何一个对象，通过选取基和坐标的办法，都可以表达为向量的形式**
	> 
	> 举两个例子：
	> 
	> （1）最高次项不大于n次的多项式的全体构成一个线性空间，也就是说，这个线性空间中的每一个对象是一个多项式。如果我们以 x <sup>0</sup>, x <sup>1</sup>, ..., x <sup>n</sup> 为基，那么任何一个这样的多项式都可以表达为一组n+1维向量，其中的每一个分量 a <sub>i</sub> 其实就是多项式中 x <sup>(i-1)</sup> 项的系数
	> 
	> 值得说明的是，基的选取有多种办法，只要所选取的那一组基线性无关就可以
	> 
	> （2）闭区间[a, b]上的n阶连续可微函数的全体，构成一个线性空间。也就是说，这个线性空间的每一个对象是一个连续函数。对于其中任何一个连续函数，根据**魏尔斯特拉斯定理**，一定可以找到最高次项不大于n的多项式函数，使之与该连续函数的差为0，也就是说，完全相等。这样就把问题归结为L1了

	所以说，向量是很厉害的，只要你找到合适的基，用向量可以表示线性空间里任何一个对象

	这里头大有文章，因为向量表面上只是一列数，但是其实由于它的有序性，所以除了这些数本身携带的信息之外，还可以在每个数的对应位置上携带信息。

- 线性空间中的运动如何表述的？也就是，线性变换是如何表示的？

	线性空间中的运动，被称为**线性变换**。也就是说，你从线性空间中的一个点运动到任意的另外一个点，都可以通过一个线性变化来完成。

	那么，线性变换如何表示呢？

	> 在线性空间中，当你选定一组基之后，不仅可以用一个向量来描述空间中的任何一个对象，而且可以用矩阵来描述该空间中的任何一个运动（变换）。而使某个对象发生对应运动的方法，就是用代表那个运动的矩阵，乘以代表那个对象的向量。

**在线性空间中选定基之后，向量刻画对象，矩阵刻画对象的运动，用矩阵与向量的乘法施加运动**

是的，**矩阵的本质是运动的描述**

<a name="precise-definition-of-matrix-movement"><h3>2.3. 进一步辨析”矩阵是运动的描述”：引出变换 [<sup>目录</sup>](#content)</h3></a>

初等数学是研究常量的数学，是研究静态的数学，高等数学是变量的数学，是研究运动的数学

<p align="right">——《高等数学·微积分》</p>

大家口口相传，差不多人人都知道这句话。但是真知道这句话说的是什么意思的人，好像也不多

> 简而言之，在我们人类的经验里，运动是一个连续过程，从A点到B点，就算走得最快的光，也是需要一个时间来逐点地经过AB之间的路径，这就带来了连续性的概念。而连续这个事情，如果不定义极限的概念，根本就解释不了
> 
> 古希腊人的数学非常强，但就是缺乏极限观念，所以解释不了运动，被芝诺的那些著名悖论（飞箭不动、飞毛腿阿喀琉斯跑不过乌龟等四个悖论）搞得死去活来。

不过在矩阵相关的研究中，“运动”的概念不是微积分中的连续性的运动，而是**瞬间发生的变化**

> 比如这个时刻在A点，经过一个“运动”，一下子就“跃迁”到了B点，其中不需要经过A点与B点之间的任何一个点。这样的“运动”，或者说“跃迁”，是违反我们日常的经验的。不过了解一点量子物理常识的人，就会立刻指出，量子（例如电子）在不同的能量级轨道上跳跃，就是瞬间发生的，具有这样一种跃迁行为。所以说，自然界中并不是没有这种运动现象，只不过宏观上我们观察不到。

为了避免产生歧义，作者对”矩阵是运动的描述”进行了更为精确的定义

<p align="center">**“矩阵是线性空间里跃迁的描述”**</p>

可是这样说又太物理，也就是说太具体，而不够数学，也就是说不够抽象。因此我们最后换用一个正牌的数学术语——**变换**，来描述这个事情

因此，**所谓变换，其实就是空间里从一个点（元素/对象）到另一个点（元素/对象）的跃迁**

比如说，拓扑变换，就是在拓扑空间里从一个点到另一个点的跃迁。再比如说，仿射变换，就是在仿射空间里从一个点到另一个点的跃迁

```
附带说一下，这个仿射空间跟向量空间是亲兄弟

做计算机图形学的朋友都知道，尽管描述一个三维对象只需要三维向量，但所有的计算机图形学变换矩阵都是4 x 4的。
说其原因，很多书上都写着“为了使用中方便”，这在我看来简直就是企图蒙混过关。

真正的原因，是因为在计算机图形学里应用的图形变换，实际上是在仿射空间而不是向量空间中进行的。
```

一旦我们理解了“变换”这个概念，矩阵的定义就变成：

<p align="center">**“矩阵是线性空间里的变换的描述”**</p>

到这里为止，我们终于得到了一个看上去比较数学的定义。

<a name="understand-linear-transformation"><h3>2.4. 理解“矩阵是线性空间中的线性变换的一个描述” [<sup>目录</sup>](#content)</h3></a>

“在一个线性空间V里的一个线性变换T，当选定一组基之后，就可以表示为矩阵”

“线性变换：设有一种变换T，使得对于线性空间V中间任何两个不相同的对象x和y，以及任意实数a和b，有：T(ax + by) = aT(x) + bT(y)”

<p align="right">——《线性代数》</p>

<a name="what-is-linear-transformation"><h4>2.4.1. 什么是线性变换 [<sup>目录</sup>](#content)</h4></a>

线性变换究竟是一种什么样的变换？

> **变换是从空间的一个点跃迁到另一个点，而线性变换，就是从一个线性空间V的某一个点跃迁到另一个线性空间W的另一个点的运动。**
> 
> 这句话里蕴含着一层意思，就是说一个点不仅可以变换到同一个线性空间中的另一个点，而且可以变换到另一个线性空间中的另一个点去
> 
> 不管你怎么变，只要变换前后都是线性空间中的对象，这个变换就一定是线性变换，也就一定可以用一个非奇异矩阵来描述。而你用一个非奇异矩阵去描述的一个变换，一定是一个线性变换
> 
> >**补充知识：奇异与非奇异**
> >
> > 首先，看这个矩阵是不是**方阵**（即行数和列数相等的矩阵。若行数和列数不相等，那就谈不上奇异矩阵和非奇异矩阵）。
> >
> > 然后，再看此矩阵的**行列式|A|是否等于0**，若等于0，称矩阵A为奇异矩阵；若不等于0，称矩阵A为非奇异矩阵
> >
> > 同时，由|A|≠0可知矩阵A可逆，这样可以得出另外一个重要结论:**可逆矩阵就是非奇异矩阵，非奇异矩阵也是可逆矩阵**

<a name="what-is-base"><h4>2.4.2. 什么是基 [<sup>目录</sup>](#content)</h4></a>

什么是基呢？

为了方便理解，这里只要**把基看成是线性空间里的坐标系**就可以了

这样一来，“选定一组基”就是说在线性空间里选定一个坐标系。

<a name="seperate-linear-transformation-and-its-description"><h4>2.4.3. 区别“线性变换”与“线性变换的一个描述” [<sup>目录</sup>](#content)</h4></a>

最后我们把矩阵的定义完善如下：

**“矩阵是线性空间中的线性变换的一个描述。在一个线性空间中，只要我们选定一组基，那么对于任何一个线性变换，都能够用一个确定的矩阵来加以描述。”**

理解这句话的关键，在于把**“线性变换”**与**“线性变换的一个描述”**区别开。一个是那个对象，一个是对那个对象的表述。

同样的，对于一个线性变换，只要你选定一组基，那么就可以找到一个矩阵来描述这个线性变换。换一组基，就得到一个不同的矩阵。所有这些矩阵都是这同一个线性变换的描述，但又都不是线性变换本身。

**这些对于同一个线性变换基于所选择的基的不同而得到的一组描述矩阵，它们之间互为相似矩阵**

那么问题来了：你给我两个矩阵，我怎么知道这两个矩阵是描述的同一个线性变换呢？

> 同一个线性变换的矩阵兄弟们的一个性质：
> 
> 若矩阵A与B是同一个线性变换的两个不同的描述（之所以会不同，是因为选定了不同的基，也就是选定了不同的坐标系），则一定能找到一个非奇异矩阵P，使得A、B之间满足这样的关系：
> 
> <p align="center">A = P<sup>-1</sup>BP</p>
> 
> 线性代数稍微熟一点的读者一下就看出来，这就是相似矩阵的定义
> 
> 上面式子里那个矩阵P，其实就是A矩阵所基于的基与B矩阵所基于的基这两组基之间的一个变换关系

同一个线性变换的不同矩阵描述，从实际运算性质来看**并不是不分好环**的。有些描述矩阵就比其他的矩阵性质好得多。这很容易理解，同一头猪的照片也有美丑之分嘛。所以矩阵的相似变换可以把一个比较丑的矩阵变成一个比较美的矩阵，而保证这两个矩阵都是描述了同一个线性变换。

<a name="summary-above"><h2>3. 对1、2的总结及引出下一部分 [<sup>目录</sup>](#content)</h2></a>

1. 首先有空间，空间可以容纳对象运动的。一种空间对应一类对象。

2. 有一种空间叫线性空间，线性空间是容纳向量对象运动的。

3. 运动是瞬时的，因此也被称为变换。

4. 矩阵是线性空间中运动（变换）的描述。

5. 矩阵与向量相乘，就是实施运动（变换）的过程。

6. 同一个变换，在不同的坐标系下表现为不同的矩阵，但是它们的本质是一样的，所以本征值相同。

引出下一部分：

> 矩阵不仅可以作为线性变换的描述，而且可以作为一组基的描述
> 
> 作为变换的矩阵，不但可以把线性空间中的一个点给变换到另一个点去，而且也能够把线性空间中的一个坐标系（基）表换到另一个坐标系（基）去

<a name="regard-matrix-as-description-of-bases"><h2>4. 将矩阵当作对一组基（坐标系）的描述 [<sup>目录</sup>](#content)</h2></a>

我们知道，线性空间里的基本对象是向量，而向量是这么表示的：

[ a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>, ..., a<sub>n</sub> ]

矩阵是这么表示的：

a<sub>11</sub>, a<sub>12</sub>, a<sub>13</sub>, ..., a<sub>1n</sub>

a<sub>21</sub>, a<sub>22</sub>, a<sub>23</sub>, ..., a<sub>2n</sub>

...

a<sub>n1</sub>, a<sub>n2</sub>, a<sub>n3</sub>, ..., a<sub>nn</sub>

可以很容易看出，矩阵是一组向量组成的。特别的，n维线性空间里的方阵是由n个n维向量组成的

我们在这里只讨论这个n阶的、非奇异的方阵，因为理解它就是理解矩阵的关键，它才是一般情况，而其他矩阵都是意外，都是不得不对付的讨厌状况，大可以放在一边

**如果一组向量是彼此线性无关的话，那么它们就可以成为度量这个线性空间的一组基，从而事实上成为一个坐标系体系，其中每一个向量都躺在一根坐标轴上，并且成为那根坐标轴上的基本度量单位（长度1）。**

现在到了**关键的一步**：看上去矩阵就是由一组向量组成的，而且如果矩阵非奇异的话（我说了，只考虑这种情况），那么组成这个矩阵的那一组向量也就是线性无关的了，也就可以成为度量线性空间的一个坐标系。

结论：**矩阵描述了一个坐标系**

<a name="why-can-regard-matrix-as-description-of-bases"><h3>4.1. 为什么可以将矩阵看作坐标系 [<sup>目录</sup>](#content)</h3></a>

你可能会产生下面的困惑：前面刚说了矩阵就是运动吗？怎么这会矩阵又是坐标系了？

之所以矩阵又是运动，又是坐标系，那是因为——

<p align="center"><strong>“运动等价于坐标系变换”</strong></p>

或者说得更直白一点：

<p align="center"><strong>“固定坐标系下一个对象的变换等价于固定对象所处的坐标系变换”</strong></p>

其实这就相当于物理中说到的，**参考系选择的不同，运动的描述也就不同**，即运动是相对的：打个比方，把线性空间的一个对象（即一个向量）当作是你，坐标系当作是地面，你在路上走，若以地面为参考系，那么你是运动的，若以你为参考系，地面是运动的

举个简单的例子：

> 把点(1, 1)变到点(2, 3)去，你可以有两种做法：
>
> - 坐标系不动，点动，把(1, 1)点挪到(2, 3)去
>
> - 点不动，变坐标系，让x轴的度量（单位向量）变成原来的1/2，让y轴的度量（单位向量）变成原先的1/3，这样点还是那个点，可是点的坐标就变成(2, 3)了

<a name="compare-2-views-to-matrix"><h3>4.2. 比较运动视角与坐标系视角下的矩阵 [<sup>目录</sup>](#content)</h3></a>

（1）从第一个方式来看，把矩阵看成是运动描述，矩阵与向量相乘就是使向量（点）运动的过程

Ma = b：向量a经过矩阵M所描述的变换，变成了向量b

（2）从第二个方式来看，矩阵M描述了一个坐标系

Ma = b：有一个向量，它在坐标系M的度量下得到的度量结果向量为a，那么它在坐标系I的度量下，这个向量的度量结果是b

或者也可以这么理解：

在M为坐标系的意义下，如果把M放在一个向量a的前面，形成Ma的样式，我们可以认为这是**对向量a的一个环境声明**。它相当于是说：

“注意了！这里有一个向量，它在坐标系M中度量，得到的度量结果可以表达为a。可是它在别的坐标系里度量的话，就会得到不同的结果。为了明确，我把M放在前面，让你明白，这是该向量在坐标系M中度量的结果。”

那么我们再看孤零零的向量b：多看几遍，你没看出来吗？它其实不是b，它是——Ib，也就是说：“在单位坐标系，也就是我们通常说的直角坐标系I中，有一个向量，度量的结果是b。”

而  Ma = Ib的意思就是说：

 “在M坐标系里量出来的向量a，跟在I坐标系里量出来的向量b，其实根本就是一个向量啊！”

<a name="understand-vector-again"><h3>4.3. 重新理解向量 [<sup>目录</sup>](#content)</h3></a>

向量这个东西客观存在，但是要把它表示出来，就要把它放在一个坐标系中去度量它，然后把度量的结果（向量在各个坐标轴上的投影值）按一定顺序列在一起，就成了我们平时所见的向量表示形式。

你选择的坐标系（基）不同，得出来的向量的表示就不同。向量还是那个向量，选择的坐标系不同，其表示方式就不同。

因此，按道理来说，每写出一个向量的表示，都应该声明一下这个表示是在哪个坐标系中度量出来的。表示的方式，就是 Ma，也就是说，有一个向量，在M矩阵表示的坐标系中度量出来的结果为a。我们平时说一个向量是[2 3 5 7]<sup>T</sup>，隐含着是说，这个向量在 I 坐标系中的度量结果是[2 3 5 7]<sup>T</sup>，因此，这个形式反而是一种简化了的特殊情况。

注意到，M矩阵表示出来的那个坐标系，由一组基组成，而那组基也是由向量组成的，同样存在这组向量是在哪个坐标系下度量而成的问题。也就是说，表述一个矩阵的一般方法，也应该要指明其所处的基准坐标系。所谓M，其实是 IM，也就是说，M中那组基的度量是在 I 坐标系中得出的。从这个视角来看，**M×N也不是什么矩阵乘法了，而是声明了一个在M坐标系中量出的另一个坐标系N，其中M本身是在I坐标系中度量出来的**。

<a name="remind-coordinates-transformation"><h3>4.4. 回头理解“固定坐标系下一个对象的变换等价于固定对象所处的坐标系变换” [<sup>目录</sup>](#content)</h3></a>

回过头来说变换的问题。我刚才说，**“固定坐标系下一个对象的变换等价于固定对象所处的坐标系变换”**，那个“固定对象”我们找到了，就是那个向量。但是坐标系的变换呢？我怎么没看见？

<p align="center"><strong>Ma = Ib</strong></p>

我现在要变M为I，怎么变？对了，在前面乘以个M<sup>-1</sup>，也就是M的逆矩阵。换句话说，你不是有一个坐标系M吗，现在我让它乘以个M<sup>-1</sup>，变成I，这样一来的话，原来M坐标系中的a在I中一量，就得到b了

尝试去理解这个事件：

比如，你画一个坐标系，x轴上的衡量单位是2，y轴上的衡量单位是3，在这样一个坐标系里，坐标为(1，1)的那一点，实际上就是笛卡尔坐标系里的点(2, 3)。而让它原形毕露的办法，就是把原来那个坐标系:

<p align="center"><img src=./picture/Understand-Matrix-2.png height=70 /></p>

在x方向度量缩小为原来的1/2，而y方向度量缩小为原来的1/3，这样一来坐标系就变成单位坐标系I了。保持点不变，那个向量现在就变成了(2, 3)了。

怎么能够让“x方向度量缩小为原来的1/2，而y方向度量缩小为原来的1/3”呢？就是让原坐标系被矩阵：

<p align="center"><img src=./picture/Understand-Matrix-3.png height=70 /></p>

左乘，而这个矩阵就是原矩阵的逆矩阵。

下面我们得出一个重要的结论：

<p align="center"><strong>“对坐标系施加变换的方法，就是让表示那个坐标系的矩阵与表示那个变化的矩阵相乘。”</strong></p>

---

参考资料：

(1) [孟岩 《理解矩阵（一）》](https://blog.csdn.net/myan/article/details/647511)

(2) [孟岩 《理解矩阵（二）》](https://blog.csdn.net/myan/article/details/649018)

(3) [孟岩 《理解矩阵（三）》](https://blog.csdn.net/myan/article/details/1865397)

(4) 《高等数学》

(5) 《线性代数》

(6) 百度百科《奇异矩阵》