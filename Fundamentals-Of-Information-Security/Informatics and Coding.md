# Informatics and Coding

## 1.绪论

### 信息论的关键词

信息（定义）：各种事物的运动状态及状态变化的方式/接受者对事物的不确定性

- 信息的特征：无形的；可共享的；无限的；无所不在的；可度量的

消息（定义）：信息的载体，相对具体的概念，如语言、文字、数字等，非物理的

信号（定义）：表示消息的物理量，如电信号的幅度、频率、相位等

- 波束赋形（beamforming）：提高电磁波信号的指向性，提高通信的安全性，但是通信的效果可能会变差[如无法找到通信方]

信息科学（定义）：研究信息的获取、传输、交换、处理、存储、显示等操作

信息论（定义）：信息科学的基础理论，研究信息科学的可能性和存在性，为信息科学的具体实现提供理论依据

- 提供一个最为普遍的概念性框架，在该框架内可以构建世纪信源和信道更为详细的模型

- 在为给定系统构建编码器和译码器时，由该理论建立的关系可以。折衷 指明方向

信息技术（定义）：实现信息论的技术

### 1.2 信息论的研究内容

图示<img src="https://api2.mubu.com/v3/document_image/16619441859351751.jpg" alt="image" style="zoom:20%;" />

Shannon信息论的基本任务

- 1948年香农发表《通信的数学理论》，奠定了信息论的理论基础

- 基本任务是设计有效可靠的通信系统

  - 有效性：通过信源编码准确无失真地表示信源的输出，降低信源冗余度，并通过信源译码恢复出信源码字所属的类（高效的传递信息）

  - 可靠性：增加消息的冗余度，在保证信息传输无差错的前提下，通过信道编解码（纠错码）最大限度地利用信道的传输能力

- 香农理论

  - <img src="https://api2.mubu.com/v3/document_image/1661944937785bfd6.jpg" alt="img" style="zoom:15%;" />

  - <img src="https://api2.mubu.com/v3/document_image/1661945073093326a.jpg" alt="img" style="zoom:15%;" />
    香农只给出了理论，但是没有给出相应的实现方法

- 香农信息论的局限性

  - 如果实际信源和信道符合采用的概率模型，香农信息论是有效的，否则只能近似，甚至无效

  - 香农信息论适用于定量描述的信息，对不可量化的信息无能为力

- 香农信息论的启示

  - 理论与实际的关系，理论必须结合实际才有发展潜力

  - 简化模型

- 5G相关编码：Polour码、LDPC码

### 1.3通信系统的模型

图示<img src="Informatics and Coding.assets/16625477031789dbf.jpg" alt="image" style="zoom:25%;" />

#### 1.3.1 信源Source[消息源]

- 信源是向通信系统提供消息u的人和机器

- 信源的核心问题是它包含的信息到底有多少，怎样讲信息定量地表示出来，即如何确定信息量

- 消息可以是离散的，也可以是连续的，但必须是随机的

- 消息可以是文字[连续]、语音[连续]、图片[连续]等（一般分类，不能全信）

- 编码器：

  - 将信源发出的消息转换成适合在信道传输的信号的设备，包括：

  - 信源编码器：对信源进行编码，降低冗余度

  - 纠错编码器：对信源编码器输出的内容进行编码，增加消息冗余度，提升传输可靠性

  - 调制器：将纠错编码器的内容输出成信号

- 译码器：

  - 用于信道解码，将信号转换回二进制码

#### 1.3.2 信宿Destination

- 信息的接收者，可以是人或物
- 信宿接受的信息与信源信息相对应

#### 1.3.3 信道Channel

- 信道分为有线信道、无限信道、存储信道
- 信道容量：信道所能传输的最大信息量

#### 1.3.4 干扰源

- 在无线通信中，干扰一般为电子热噪声
- 加性干扰：外界引入的随机干扰，信道传输是输入与干扰之和
- 乘性干扰：内部干扰，信道传输是输入与干扰的乘积

#### 1.3.5 密钥源

#### *三类编码问题

- 1 信源编码

  - 编码器的作用：把消息变成合适信道传输的信号

  - 信源编码有两个作用：

    - 一是把信源发出的消息转换成由二进制码元（或多进制码元）组成的代码组，这种代码组就是基带信号

    - 而是通过信源编码压缩信源的冗余度，以提高通信传输消息的效率

    - 信源编码可分为无失真信源编码和限失真信源编码，前者适用于离散信号，后者主要用于连续或模拟信号

- 2 信道编码

- 3 加密编码

- 通信系统的基本目标——有效性

  - 消息若在信源中先去粗取精，则必能提高通信的有效性

  - 用尽可能短的时间和尽可能少的设备来传输一定量的消息

  - 对数字通信系统来说，即信源编码要解决的主要问题

- 通信系统的基本目标——可靠性

## 2.信源与信息熵

### 2.1 信源的分类及数学模型

- 信源输出消息，消息承载信息

  - 信源消息是随机、不确定的，因此基于信源的随机性和概率统计特性来建立信源的数学模型

  - 从数学上，用随机变量、随机序列（矢量）和随机过程来分别描述信源产生的消息（符号），消息序列和连续消息

- 信源的分类（课本的分类有误，暂时以此为基础）

  - 表示信源符号的参量个数是有限的——称为离散信源

  - 单符号连续信源

  - 符号序列信源（有记忆和无记忆）

  - 连续信源

#### 2.1.1单符号信源的概率空间描述

- 离散信源
  <img src="https://api2.mubu.com/v3/document_image/16625491209897963.jpg" alt="img" style="zoom:25%;" />
- 连续信源
  <img src="Informatics and Coding.assets/16625493929858536.jpg" alt="img" style="zoom:25%;" />

#### 2.1.2离散序列信源的概率空间描述

- 图示<img src="Informatics and Coding.assets/1662549615403f615.jpg" alt="img" style="zoom:15%;" />
- 离散无记忆序列信源（信息量最大的信源）
  <img src="Informatics and Coding.assets/16625498740433966.jpg" alt="img" style="zoom:15%;" />
- 独立同分布信源
  <img src="Informatics and Coding.assets/166255022807282d3.jpg" alt="img" style="zoom:15%;" />
- 离散有记忆序列信源
  <img src="Informatics and Coding.assets/16625502129644fcb.jpg" alt="img" style="zoom:15%;" />

#### 2.1.3连续信源

- 连续平稳信源：时间离散、幅度连续
- 随机波形信源：时间、幅度均连续

#### 2.1.4关于采样

图示
<img src="Informatics and Coding.assets/1662550729825bb1c.jpg" alt="image" style="zoom:15%;" /><img src="Informatics and Coding.assets/16625507794691201.jpg" alt="image" style="zoom:15%;" />

#### 2.1.5马尔可夫信源

- 当信源的记忆长度为m+1时，该时刻发出的符号与前m个符号相关，而与更前面的符号无关

  - 这种信源称为m阶马尔可夫信源，可用马尔可夫链描述

  - 如果条件概率与时间起点无关，则称为齐次马尔可夫信源

- 高阶马尔可夫信源需要引入矢量进行分析，可将矢量转化为状态矢量，从而将高阶马尔可夫过程转化为齐次马尔可夫过程

- 把某个时刻前出现的m个符号组成的序列定义为状态

  

  - 该序列共有n^m种可能的状态

  - 马尔可夫信源当前发出的符号与前m个符号相关，这里的‘前m个符号’可用n^m个状态中的某一个状态表示

- 信源在某一时刻输出符号Sj的概率与信源此时所处状态Si有关，用符号条件概率表示为p(Sj | Si)

- 当符号Sj出现后，信源转入新的状态，这种状态转移表示为：
  <img src="https://api2.mubu.com/v3/document_image/1662551624093bb7d.jpg" alt="img" style="zoom:15%;" /><img src="https://api2.mubu.com/v3/document_image/166315296101602a9.jpg" alt="img" style="zoom:15%;" />

- 马尔可夫信源状态矩阵
  <img src="https://api2.mubu.com/v3/document_image/166315311640149c7.jpg" alt="img" style="zoom:15%;" />

- 切普曼-柯尔莫哥洛方程
  <img src="Informatics and Coding.assets/1663153933776c43e.jpg" alt="img" style="zoom:15%;" /><img src="Informatics and Coding.assets/166315529283660d4.jpg" alt="img" style="zoom:15%;" />

  

  当某一状态i经过k步转移到状态j时的概率由上述方程得出；
  齐次马尔可夫链的一步转移概率完全决定了k步转移概率 

  - 一步转移的路径有k种

- 马尔可夫信源的稳态分布概率

  <img src="Informatics and Coding.assets/16631555593860583.jpg" alt="img" style="zoom:15%;" />

  - 当遍历所有可能性时，每种状态的概率就已经能基本确定，无论再发生多少次变化都不改变其概率

  - 其中的Wj即每个状态在变化中出现的概率，可以用下列方程组求解<img src="https://api2.mubu.com/v3/document_image/16637581713905d88.jpg" alt="img" style="zoom:15%;" />

  - 在例题中即表示为求每一个概率的Wj即用变化到该状态的概率乘以上一个概率的Wj即可（如W1=1/2*W1+2/3*W3），然后带入W1+Ｗ2+…+Wj=1即可求解每一个Wj

  - 例题在课本19页

- 稳定状态的充分条件

  <img src="Informatics and Coding.assets/16631562673045347.jpg" alt="img" style="zoom:15%;" />

  <img src="Informatics and Coding.assets/1663156586011fd8b.jpg" alt="img" style="zoom:15%;" />

  - 从一个状态出发，总能到达所有的可能状态，才能称为马尔可夫链

- 定理
  <img src="https://api2.mubu.com/v3/document_image/16637570010218f24.jpg" alt="img" style="zoom:25%;" />

- 马尔可夫信源极限熵
  <img src="Informatics and Coding.assets/1663758421973198b.jpg" alt="img" style="zoom:25%;" />

总结：信源发出的消息时随机的，但其统计特性是可以确定的

### 2.2离散信源和互信息

#### 2.2.1 自信息量

- 直观推导信息测度
  <img src="https://api2.mubu.com/v3/document_image/1663758622683659e.jpg" alt="img" style="zoom:15%;" />

- 信息量与信源的概率成反比，即信息量越大概率越小

- 自信息量的定义
  <img src="https://api2.mubu.com/v3/document_image/16637589474901c43.jpg" alt="img" style="zoom:15%;" />

- 自信息量与不确定度

  - 自信息量：符号出现后，提供给收信者的信息量

  - 不确定度：符号出现前，所含有的不确定性

  - 二者数量相等，物理意义不同

- 自信息量的性质
  <img src="https://api2.mubu.com/v3/document_image/16637595233247d0e.jpg" alt="img" style="zoom:15%;" />

- 联合自信息量
  <img src="https://api2.mubu.com/v3/document_image/1663759734631e2ce.jpg" alt="img" style="zoom:15%;" />

- 条件自信息量
  <img src="https://api2.mubu.com/v3/document_image/166375974210690bd.jpg" alt="img" style="zoom:15%;" />

- 联合自信息量、条件自信息量与自信息量的关系
  <img src="Informatics and Coding.assets/1663759866984e99f.jpg" alt="img" style="zoom:15%;" />

#### 2.2.2 离散信源熵

- 定义：离散概率空间表示的信源所定义的自信息量的数学期望为 信源的信息熵，单位为比特/符号
  <img src="https://api2.mubu.com/v3/document_image/166376064016992c1.jpg" alt="img" style="zoom:15%;" />

- 单符号离散信源熵
  <img src="Informatics and Coding.assets/16637608812048add.jpg" alt="img" style="zoom:15%;" />

  - H(X)表示信源X所需要的最少的每符号比特数

  - 若对信源一无所知（x的符号数、概率等）——H(X)无穷大

  - 若已知x的符号数（但不知道概率，假设等概）——H(X)=logM
    - 已知信源的概率空间，不等概率时H(X)进一步变小，说明获得信息能使对信源的不确定度减少

- 离散信源条件熵
  <img src="https://api2.mubu.com/v3/document_image/16643627408139d83.jpg" alt="img" style="zoom:15%;" />

- ***离散信源的联合熵**
  <img src="https://api2.mubu.com/v3/document_image/16643629794279cb4.jpg" alt="img" style="zoom:15%;" />

- 联合熵、条件熵与熵的关系
  <img src="Informatics and Coding.assets/16643631145698ff8.jpg" alt="img" style="zoom:15%;" /><img src="Informatics and Coding.assets/1664363753777441f.jpg" alt="img" style="zoom:20%;" />

#### 2.2.3 互信息

- 定义：H(X)-H(X|Y)=？，减少量是已知Y活得的关于X的信息量，该信息量就是 互信息

- I(X,Y)=H(X)-H(X|Y)=I(Y|X)

- 平均互信息量与信源熵、条件熵的关系
  <img src="https://api2.mubu.com/v3/document_image/1664365004571764c.jpg" alt="img" style="zoom:15%;" />

- 噪声熵举例，信源发的是x，而接收到的为y（其实就如000110上信道传输后变成了100111）

  - 由噪声导致的Y的不确定性 

- 平均互信息量

  - 公式定义
    <img src="https://api2.mubu.com/v3/document_image/1664365323521a942.jpg" alt="img" style="zoom:25%;" />

  - 其中p(xi)为xi的先验概率，p(xi|yj)为xi的后验概率

  - 这是平均意义上的互信息量，而单个符号之间的互嘻嘻定义为符号后验概率与先验概率比值的对数

  - 性质

    - 非负性I(X;Y)>=0
      <img src="https://api2.mubu.com/v3/document_image/166436609429783b5.jpg" alt="img" style="zoom:15%;" />

    - 互异性

    - 极值性

    - 凸函数性

- 单符号离散信源互信息
  <img src="Informatics and Coding.assets/1664365873039a78b.jpg" alt="img" style="zoom:25%;" />

  - 定义：对于离散概率空间表示的信源，在出现Yi事件后所提供有关事件Xj的信息量定义为互信息

- 条件互信息量

  - 定义
    <img src="https://api2.mubu.com/v3/document_image/16649665516701a4f.jpg" alt="img" style="zoom:25%;" />

- 联合互信息量

  - 定义

#### 2.3.4 数据处理中信息的变化

***信息不增性**：

#### 2.2.5相对熵（看课本概念理解即可）

#### 2.2.6熵的性质

- 非负性
  - $H(X)=H(p_1,p_2,...,p_n)\geq0$
  - 上述式中的等号只有在$p_i=1$时成立，因为$0<p_i<1$，则$logp_i$一定是一个负数，但熵是非负的
  
- 确定性
  - $H(0,1)=H(1,0,0,...,0)=0$
  - 只要信源符号中，有一个符号出现的概率为1，信源熵就等于0
  - 其实就是概率空间中如果有两个基本事件，其中一个是必然事件，另一个就是不可能事件，因此不肯定性，熵就是0
  
- 对称性
  - 熵函数所有元可以互换，而不影响函数值
  - $H(p_1,p_2,...,P_n)=H(p_1,p_2,...p_n)$
  - **熵函数只与随机变量的总体结构有关**
  
- ***香农辅助定理**（香农不等式）
  
  - 对任意n维概率矢量$P=(p_1,p_2,...,p_n)和Q=(q_1,q_2,...q_n)$对如下不等式成立
    - $H(p_1,p_2,...,p_n)=-\sum_{i=11}^{n}{p_i}logp_i\leq-\sum_{i=1}^{n}{p_i}logq_i$
  - 对任意概率分布$p_i$，它对其他概率分布$q_i$的自信息量$-logq_i$取数学期望时，必须大于$p_i$本身的熵
  - 等号仅当$P=Q$ 时成立
  
- ***最大熵定理**

  - 离散无记忆信源输出M个不同的信息符号，**当且仅当各个符号出现的概率相等（$p_i=1/M$）**,熵最大
  - 因为出现任何符号的概率相等时，不确定性最大，即
    - $H(X)\leq H(\frac{1}{M},\frac{1}{M},...,\frac{1}{M})=logM$

- 条件熵小于无条件熵

  - 条件熵小于信源熵：$H(Y|X)\leq H(Y)$
    - 当且仅当y和x相互独立是，$p(y|x)=p(y)$取等号

  - 两个条件下的条件熵小于一个条件下的条件熵：$H(Z|X,Y)\leq H(Z|Y)$
    - 当且仅当$p(z|x,y)=p(z|y)$时取等号

  - 联合熵小于信源熵之和：$H(X,Y)\leq H(X)+H(Y)$
    - 当且仅当两个集合相互独立时取等号，此时得联合熵最大值：$H(X,Y)_{max}=H(X)+H(Y)$

- 扩展性

  - $\lim_{\varepsilon \rightarrow 0}{H_{n+1}}(p_1,...p_n-\varepsilon,\varepsilon)=H_n(p_1,...,p_n)$
  - 因为$\lim_{\varepsilon \rightarrow 0}{\varepsilon}log \varepsilon=0$，所以上述式成立

- 可加性

  - $H(X,Y)=H(X)+H(x|Y)$，当且仅当X、Y相互独立时，$H(X,Y)=H(X)+H()Y$

  - 如果考虑概率的形式，设X的概率分布为$(p_1,p_2,...,p_n)$，已知X的情况下Y的条件概率为$p(Y=y_j|x_i)=p_{ij}$

    - 此时可加性表示为：
      $$
      H_{nm}(p_1p_{11},p_1P_{12},...,p_1p_{1m},...,p_np_{n1},...,p_np_{nm}) 
      =H_n(p_1,...,p_n)+\sum_{i=1}^{n}{p_i}H_m(p_{i1},...,p_{im})
      $$

    - 其中$\sum_{i=1}^n{p_i}H_m(p_{i1},...,p_{im})=H(Y|X)$

- 递增性

  - $$
    H_{n+m-1}(p_1,p_2,...,p_{n-1},q_1,q_2,...,q_m)=H_n(p_1,p_2,...,p_{n-1},p_n)+p_nH_m(\frac{q_1}{p_n},\frac{p_2}{q_n},..,\frac{q_m}{p_n})
    $$

  - 其中$\sum_{i=1}^{n}{p_i}=1,\sum_{j=1}^{m}{q_j}=p_n$

- 互信息量与熵之间的关系

  - $H(X，Y)=H(X)+H(Y|X)=H(Y)+H(X|Y)$
  - $H(X)\geq H(X|Y),H(Y)\geq H(Y|X)$
  - $I(X;Y)=H(X)-H(X|Y)=H(Y)-H(Y|X)=H(X)+H(Y)-H(X,Y)$
  - $H(X,Y)\leq H(X)+H(Y)$
  - 如果X和Y相互独立，则
    - $I(X;Y)=1$
    - $H(X,Y)=H(X)+H(Y)$
    - $H(X)=H(X|Y),H(Y)=H(Y|X)$


### 2.3离散序列信源的熵

#### 2.3.1 离散无记忆信源

设信源输出设备的随机序列为$\vec{F},\vec{F}=(X_1,X_2,...,X_l,...,X_L)$，序列中的单个符号变量$X_i\quad in \{x_1,x_2,...,X_n\},l=1,2,...,L  $ ，即序列长度为L

- 随机序列的概率为$P(X=x_i)=p(X_1=x_{i_1},X_2=x_{i_2},...,X_L=x_{i_L}),i=1,2,...,n^L;i_l=1,2,...,n$
- 此时的信源熵为

#### 2.3.2 离散有记忆信源

### 2.4连续信源的熵和互信息

