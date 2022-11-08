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

设信源输出设备的随机序列为$\vec{F},\vec{F}=(X_1,X_2,...,X_l,...,X_L)$，序列中的单个符号变量$X_i\quad \in \{x_1,x_2,...,X_n\},l=1,2,...,L  $ ，即序列长度为L

- 随机序列的概率为$P(X=x_i)=p(X_1=x_{i_1},X_2=x_{i_2},...,X_L=x_{i_L}),i=1,2,...,n^L;i_l=1,2,...,n$

- 此时的信源熵为$H(X)=-\sum_{i=1}^{n^L}{p(x_i)logp(x_i)}=-\sum_{i_1=1}^{n}\sum_{i_2=1}^{n}...\sum_{i_L=1}^{n}p(x_{i_1},x_{i_2},...,x_{i_L})logp(x_{i_1},x_{i_2},...,x_{i_L})$

- *其中随机序列的概率可以表示为$p(\vec{X}=\vec{x_i})=p(x_{i_1})p(x_{i_2}|x_{i_1})p(x_{i_3}|x_{i_1}^2)...p(x_{i_L}|x_{i_1}^{L-1})$

  - 当信源无记忆时，$p(\vec{x_i})=p(x_{i_1},x_{i_2},...,x_{i_L})=\prod_{l=1}^{L}p(x_{i_l})$

- 当信源无记忆（即各序列相互独立）信源的序列熵为$H(\vec{X})=\sum_{l=1}^{L}H(\vec{X_l})$

  - 若又满足平稳性，即各独立向量的熵都相等$H(\vec{X_1})=H(\vec{X_2})=H(\vec{X_3})=...=H(\vec{X_L})$则信源熵可以表示为

    $H(\vec{X})=LH(X)$ 平均每一个符号的熵为$H_L(\vec{X})=\frac{1}{L}H(\vec{X})=H(X)$


#### 2.3.2 离散有记忆信源

- 对于两个符号组成的联合信源有以下结论
  - $H(X_1,X_2)=H(X_1)+H(X_2|X_1)=H(X_2)+H(X_1|X_2)$
  - $H(X_1)\geq H(X_1|X_2),H(X_2)\geq H(X_2|X_1)$
  - 当两个符号相互独立时有推论：$H(X_1,X_2)=H(X_1)+H(X_2)，H(X_1|X_2)=H(X_1),H(X_2|X_1)=H(X_2)$

- 若信源输出为一个序列时，有如下公式
  - $H(\vec{X})=H(X_1,X_2,\cdots,X_L)=H(X_1)+H(X_2|X_1)+\cdots+H(X_L|X_1,X_2,\cdots,X_{L-1})$
    - 通常记作$H(\vec{X})=H(X^L)=\sum_{l=1}^{L}{H(X_l|X^{l-1})}$
  - 平均每个符号的熵为：$H_L(\vec{X})=\frac{1}{L}H(X^L)$
  - 若当信源退化为无记忆时，有：$H(\vec{X})=\sum_{l=1}^{L}H(X_l)$
  - 若进一步又满足了平稳性时，则有：$H(\vec{X})=LH(X)$
  
- 关于离散有记忆信源的一些结论

  - 结论1：$H(X_L/X_{L-1})$是L的单调非增函数，由于条件熵小于或等于无条件熵，条件较的多的熵小于或等于条件减少一些条件的熵，考虑到平稳性，所以
    $$
    H(X_L|X_1,X_2,\cdots,X_{l-1})\leq H(X_L|X_2,\cdots,X_{L-1}) \\
    \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad=H(X_{L-1}|X_1,\cdots,X_{L-2})\quad(平稳性)\\
    \qquad\qquad\qquad\qquad\qquad\quad\;\;\;\leq H(X_{L-1}|X_2,\cdots,X_{L-2}) \\
    \qquad\qquad\qquad\qquad\qquad\quad\;\;=H(X_{l-2}|X_1,\cdots,X_{L-3})  \\
    \quad\;\;\vdots\\
    \qquad\qquad\qquad\;\;\leq H(X_2|X_1)
    $$

  - 结论2：$H_L(\vec{X})\geq H(X_L|X^{L-1})$

  - 结论3：$H_L(\vec{X})$是L的单调非增函数

  - 结论4：$L\rightarrow\infty$时，有$H_{\infty}(\vec{X})\triangleq \lim_{L\rightarrow\infty}{H_L(\vec{X})}=\lim_{L\rightarrow \infty}{H(X_L|X_1,X_2,\cdots,X_{L-1})}$
  
    - 其中$H_{\infty}(\vec{X})$称为极限熵，又称极限信息量
  
  - 对于齐次、遍历的马尔可夫链，其状态$s_i$由$(x_{i_1},\cdots,x_{i_m})$唯一确定，因此有
  
    - $p(x_{i_{m+1}}|x_{i_m},\cdots,x_{i_1})=p(x_{i_{m+1}}|s_{i})$
    - 对所有符号取统计平均，然后取负得到$H_{\infty}(\vec{X})=\sum_{i}p(s_i)H(X|s_i) \quad $**马尔可夫信源的极限熵**
      - 其中$p(s_i)$是马尔可夫链的稳态分布，熵函数$H(X|s_i)$表示信源处于某一状态$s_i$时发出一个消息符号的平均不确定性，即有$H(X|s_1)=-\sum_{j}p(x_j|s_i)log\;p(x_j|s_i)$
      - 对状态$s_i$的全部可能性做统计平均，就可得到马尔可夫信源的平均符号熵$H_{\infty}(\vec{X})$

### 2.4连续信源的熵和互信息

#### 2.4.1 幅度连续的单个符号信源熵

- 对于单个变量分析，假设$x \in [a,b]$，令$\Delta x=(b-a)/n，x_i \in [a+(i-1)\Delta x,a+i\Delta x],p_X(x)$为连续变量X的概率密度函数，则利用中值定理可得$X$取$x_i$ 的概率是

  - $p(x_i)=\int_{a+(i-1)\Delta x}^{a+i\Delta x}{p_X(x)dx}=p_X(x_i)\Delta x$，根据离散信源熵的定义，则$H_n(X)=-\sum_{i=1}^{n}p(x_i)logp(x_i)=-\sum_{i=1}^{n}p_X(x_i)\Delta xlog\;p_X(x_i)\Delta x$
  - 当$n\rightarrow\infty时，即\Delta x\rightarrow 0$时，由积分定义得：$H(X)=\lim_{n\rightarrow\infty}H_n(X)=-\int_{a}^{b}p_X(x_i)log\;p_X(x_i)dx-\lim_{\Delta x\rightarrow 0}log\Delta x$
    - 上述式的第一项具有离散信源熵的形式，是定值；第二项为无穷大。因而丢掉第二项，并定义**连续信源熵**为：
    - $H_c(X)=-\int_{-\infty}^{\infty}p_X(x)log\;p(x)dx$称为微分熵(differential entropy)，有时也简称为熵
  - 连续信源熵与离散信源熵具有相同的形式，但其意义不同

- 对于两个变量分析，定义X、Y两个变量的情况

  - 联合熵：$H_c(X,Y)=-\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}p_{X,Y}(x,y)log\;p_{X,Y}(x,y)dxdy$

  - 条件熵：$H_c(X|Y)=-\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}p_X(x)p_Y(y|x)log\;p_Y(y|x)dxdy$

  - 联合熵和条件熵之间与离散信源一样的相互关系，并且可以得到由信息特征的互信息，即

    - $H_c(X,Y)=H_c(X)+H_c(Y|X)=H_c(Y)+H_c(X|Y)$

    - $$
      I(X;Y)=I(Y;X)=H_c(X)-H_c(H|Y)\\\qquad\qquad\qquad\qquad\qquad\quad\quad\;\;=H_c(X)+H_c(Y)-H_c(X,Y)\\\qquad\qquad\qquad\quad\quad\;=H_c(Y)-H_c(Y|X)
      $$

      

#### 2.4.2 波形信源熵以及互信息

- 对于平稳随机矢量$\vec{X}=(X_1,X_2,\cdots,X_L)和\vec{Y}=(Y_1,Y_2,\cdots,Y_L)$，则平稳随机矢量$\vec{X}和\vec{Y}$的连续熵和条件熵为
  - $H_c(\vec{X})=H_c(X_1,X_2,\cdots,X_L)=-\int_{R}p_X(x)logp_X(x)dx$多维积分
  - $H_c(\vec{X}|\vec{Y})=H_c(Y_1,Y_2,\cdots,Y_L|X_1,X_2,\cdots,X_L)=-\int_{R}\int_Rp_X(x,y)logp_Y(y|x)dxdy$
- 对于随机波形信源，可由上述各项的极限表达式$L\rightarrow\infty $给出，则
  - $H_c(x(t))\cong\lim_{L\rightarrow\infty}H_c(\vec{X})$
  - $H_c(y(t)|x(t))\cong\lim_{L\rightarrow\infty}H_c(\vec{Y}|\vec{X})$
- 对于限频$f_m$、限时$t_B$的平稳随机过程，可以用有限维$L=2f_mt_B$随机矢量表示，

#### 2.4.3 最大熵定理

- **限峰功率最大熵定理：**对于定义域为有限的随机变量$\vec{X}$，当它是是品骏分布时，具有最大熵

  - 变量$\vec{X}$的幅度取值限制在$[a,b]$，则有$\int_{a}^{b}p_X(x)dx=1$,当任意$p_X(x)$符合平均分布条件
    $$
    p_X(x)=\begin{cases}
    \frac{1}{a-b} \;,a\leq x\leq b\\
    0\; , 				其他
    \end{cases}
    $$
    时，信源达到最大熵

  - $H_c(X)=-\int_{a}^{a}{\frac{1}{b-a}}log\frac{1}{b-a}dx=log(b-a)$，该结论与离散信源在以等概率出现时达到最大熵的结论相类似

- **限平均功率最大熵定理：**对于相关矩阵一定的随机变量$\vec{X}$，当它是正态分布时具有最大熵

  - 设随机变量$X$的概率密度分布为$p_X(x)=\frac{1}{\sqrt{2\pi\sigma^2}}e^{\frac{-(x-2)^2}{x\sigma^2}}$，其中m为数学期望，$\sigma^2$为方差，则连续熵为
    - $H_c(X)=\frac{1}{2}log(2\pi e\sigma^2)$

### 2.5 信源的冗余度

- **冗余度也称多余度或剩余度**，即给定信源在实际发出消息时包含的多于信息，如果一个消息所包含的符号比表达这个消息的符号多，那么这样的消息就存在冗余度
- 冗余度产生的两个原因：
  - 信源符号之间的相关性，相关程度越大，信源的实际熵越小，趋于极限熵$H_{\infty}(\vec{X})$；反之相关程度越小，信源的实际熵就增大
  - 信源符号的分布不均匀性，**当等概率分布时信源熵最大**，而实际应用中大多数不均匀分布使得实际熵减小为$H_1(X)$;当信源输出符号间彼此不存在依赖关系且等概率分布时，信源实际熵区域最大熵$H_0(X)$
- **信息效率**：$\upeta = \frac{H_{\infty}(X)}{H_m{X}}$
  - 表示不肯定性的程度，由定义可知$0\leq \upeta \leq 1 , (1-\upeta)$表示肯定性的程度，因为肯定性不会含有信息量，所以表示是冗余的
- 由上述信息效率定义**冗余度**为：$\upgamma =1-\upeta =1-\frac{H_{\infty}(X)}{H_{m}(X)}$
  - 实际上，当只知道信源符号有n个可能取值，而对其概率特性一无所知时，合理的假设是：
    - n个取值是等可能的，因为此时熵取最大值$H_0(X)=logn$

## 3.信道与信道容量

### 3.1 信道的基本概念

#### 3.1.1 信道的分类

- 根据用户数量可分为**单用户信道**和**多用户信道**
- 根据信道输入端和输出端的关系可分为**无反馈信道**和**反馈信道**
- 根据信道参数与时间的关系可分为**固定参数信道**和**时变参数信道**
- 根据噪声种类可分为**随机差错信道**和**突发差错信道**
- 根据输入、输出信号的特点可分为**离散信道**、**连续信道**、**半离散半连续信道**、**波形信道**

#### 3.1.2 信道的数学模型

- 信道输入矢量：$\vec{X}=(X_1,X_2,\cdots,X_i,\cdots),X_i \in A=\{a_1,a_2,\cdots,a_n\}$

- 信道输出矢量：$\vec{Y}=(Y_1,Y_2,\cdots,Y_i,\cdots),Y_i \in B=\{b_1,b_2,\cdots,b_n\}$

  - 通常采用条件概率$p(\vec{Y}|\vec{X})$来描述信道的输入、输出信号之间的统计的依赖关系
  - 在分析信道时，该条件概率通常称为**转移概率**

- 概率转移矩阵

  - $$
    \vec{P}=\left[\begin{matrix}
     p_{11} & p_{12}&\cdots & p_{1m} \\
     p_{12} & p_{22}&\cdots & p_{2m} \\
     \vdots & \vdots&\ddots &\vdots  \\
     p_{n1} & p_{n2}&\cdots & p_{nm} 
    \end{matrix}
    \right]
    $$

- 根据信道是否存在干扰以及有无记忆，将信道分为如下三类

  - 无噪声信道

    - 信道的输出信号$\vec{Y}$与输入信号$\vec{X}$之间有确定关系$\vec{Y}=f(\vec{X})$,已知输入信号后就确知输出信号

    - 转移概率
      $$
      p(\vec{Y}|\vec{X})=\begin{cases}
      1,\vec{Y}=f(\vec{X}) \\
      0,\vec{Y}\neq f(\vec{X})
      \end{cases}
      $$
      

  - 有干扰无记忆信道

    - 二进制离散信道(BSC)
      $$
      p(Y=0|X=1)=p(Y=1|X=0)=p \\
      p(Y=0|X=0)=p(Y=1|Y=1)=1-p
      $$
      
    - 离散无记忆信道(DMC)
      $$
      \vec{P}=[p(b_j|a_i)]=[p_{ij}]=\vec{P}=\left[\begin{matrix}
       p_{11} & p_{12}&\cdots & p_{1m} \\
       p_{12} & p_{22}&\cdots & p_{2m} \\
       \vdots & \vdots&\ddots &\vdots  \\
       p_{n1} & p_{n2}&\cdots & p_{nm} 
      \end{matrix}
      \right] \\
      其中输入符号由n个元素X \in \{a_1,a_2,\cdots,a_n\},输出符号m个元素Y \in \{b_1,b_2,\cdots,b_m\}\\
      显然\sum_{j=1}^{m}{p(b_j|a_i)=1},\;i=1,2,\cdots,n\\
      因此矩阵中各行元素之和为1，又因为BSC信道为DMC信道的特例，则BSC信道的概率转移矩阵为\\
      \vec{P}=\left[\begin{matrix}
      1-p,\;\;p\\
      p,\quad1-p
      \end{matrix}\right]
      $$
      
    - 离散输入、连续输出信道
  
      - 输入：有限的、离散的符号集$X\in \{a_1，a_2,\cdots,a_n\}$，输出信道为量化$（m\rightarrow \infin）$此时信道输出是实轴上的任意值即$Y\in \{-\infty ,\infty\}$，因此该信道模型又称为**离散时间无记忆信道**
      - 特性：由离散输入X、连续输出Y，以及一组条件概率密度函数$p_Y(y|X=a_i),i=1,2,\cdots,n$来决定
      - 重点：这是一种**加性高斯白噪声(AWGN)信道**即存在——$Y=X+G$，其中G是一个零均值，方差为$\sigma ^2$的高斯随机变量
      - 当$X=a_i$给定后，$Y$是一个均值为$a_i$方差为$\sigma ^2$的高斯随机变量，即$p_Y(y|a_i)=\frac{1}{\sqrt{2\pi }\sigma}e^{-(y-a_i)^2/2\sigma ^2}$
  
    - 波形信道：输入输出都是随机过程$\{x(t)\}$和$\{y(t)\}$时，该信道为波形信道
  
  - 有干扰有记忆信道

#### 3.1.3 信道容量的定义

- 信道中平均每个符号所能传输的信息量定义为信道的信息传输率R，即
  - $R=I(X;Y)=H(X)-H(X|Y)\quad bit/符号$
- 若已知平均传输一个符号所需时间为$t(s)$，则单位时间内平均传输的信息量定义为信息传输速率，即
  - $R_t=I(X;Y)/t$，单位为$bit/s$

- 信道容量：对于某特定信道，转移概率$p(b_j|a_i)$已经确定，则互信息就是关于输入符号分布概率$p(a_i)$的凸函数，也就是可以找到某种概率分布$p(a_i)$使得$I(X;Y)$达到最大，该最大值就是信道所能传输的最大信息量，即信道容量
  - $C=\max_{p(a_i)} I(X;Y)$
  - C的单位是信道上每传送一个符号所能携带的比特数，即bit/符号

- 关于信道是否有损有噪的讨论
  - 无损无噪：$H(X|Y)=H(Y|X)=0,I(X;Y)=H(X)=H(Y)$
  - 有损无噪：$噪声熵H(Y|X)=0,疑似(义)度I(X|Y)>0,C=\max H(Y)$
  - 无损有噪：$噪声熵H(Y|X)>0,疑似度I(X|Y)=0,C_{max}=\max H(X)$

- **对于固定信道参数的信道，信道容量是定值，但是在传输信息时信道是否能提供最大传输速率，取决于输入端的概率分布**
  - 如果输入端等概率分布，则信道的容量达到最大值


### 3.2 离散单个符号信道及其容量

**信道的输入和输出均以单个符号的形式表示，或者以序列形式表示，但符号之间不相关，即无记忆**

#### 3.2.1 无干扰离散信道

设信道输入为$X\in A=\{a_1,a_2,\cdots,a_n\}$，信道输出为$Y\in B=\{b_1,b_2,\cdots,\_m\}$，按照X于Y的对应关系可分为如下几种信道

- X、Y一一对应，对应到无噪无损，无噪有损，有噪无损三种信道就有如下结果
  - **n=m**，信道无噪无损，条件概率矩阵为一个单位矩阵，$H(Y|X)=0,I(X;Y)=H(X)=H(Y)$，当输入符号分布为等概率时，信道的传输能力达到信道容量$C=\max I(X;Y)=\log n$
  - **n>m**，多个输出变为一个输出，即无噪有损信道，噪声熵$H(Y|X)=0$，疑似(义)度$H(X|Y)\neq 0 $，所以$H(X)\ge H(Y)$，信道容量$C=\max I(X;Y)=\max H(Y)$
  - **n<m**，一个输入对应多个输出，但每个输入对应的输出值不重合，即有噪声无损信道，疑似(义)度$H(X|Y)= 0 $，噪声熵$H(X|Y)\neq 0$，所以$H(X) \le H(Y)$，信道容量$C=\max I(X;Y)=\max H(X)$

#### 3.2.2 对称DMC信道/对称离散无记忆信道

如果概率转移矩阵$P$的每一行都是第一行的置换（包含相同的元素），则称该矩阵是**输入对称**；如果转移概率矩阵$P$的每一列都是第一列的置换，则称该矩阵为**输出对称**

- 对称信道转移概率矩阵中每行的元素都相同，$\sum_{j}p(b_j|a_i)\log{p(b_j|a_i)}$的值于$i$无关则其条件熵
  - $H(X|Y)=-\sum_{i}{p(a_i})\sum_{j}{p(b_j|a_i)\log{p(b_j|a_i)}}=H(Y|a_i),i=1,2,\cdots,n$
  - 与信道输入符号的概率分布$p(a_i)$无关
- 而上述信道的信道容量如下
  - $C=\max_{p(a_i)}{H(Y)}-H(Y|X)$
- 如果信道输入信号等概率分布$p(a_i)=1/n$，由于转移概率矩阵的列对称，有
  - $p(b_j)=\sum_{i}{p(a_i)p(b_j|a_i)}=\frac{1}{n}\sum_{i}p(b_j|a_i)$，于**j**无关，即信道输出符号也等概分布；反之信道输出等概分布，则信道输入也等概分布
  - 此时对称DMC信道的信道容量为$C=\log{m}+\sum_{j=i}^{m}{p_{ij}\log{p_{ij}}}$，其中$m$为信道输出符号集中的数目，$p(b_j|a_i)$简写为$p_{ij}$

#### 3.2.3 准对称DMC信道*

如果转移概率矩阵$P$是输入对称而输出不对称，则转移概率矩阵$P$的每一行都包含同样的元素而各列的元素可以不同

- 因为每行元素相同，所以$H(X|Y)=H(Y|a_i)，i=1,2,\cdots,n$成立
- 因为每列的元素不相同，所以信道的输入和输出概率可能不等，此时$H(Y)$的最大值可能小于$Y$等概时的熵，所以准DMC信道的容量如下
  - $C\le \log{m}+\sum_{j=1}^{m}p_{ij}\log{p_{ij}}$
  - 当输出也对称时，上述式取等号
  - 输出最大时，输入等概率分布
  - 因为互信息输入符号概率的$\bigcap$型凸函数，根据信道容量的定义式，可引入拉格朗日乘子法解决极值问题，求得输入符号概率和最大互信息

#### 3.2.4 一般DMC信道

以输入符号概率矢量$\vec{P}_{x}$为自变量求函数$I(\vec{p}_{x})$极大值即信道容量问题，从数学上看是一个规划问题，这个问题已经解决。

- 对于上述问题，常用的算法为**Blahut-Arimoto**算法

- 一般而言，为使$I(X;Y)$最大化以便求取DMC容量，输入符号概率集$\{p(a_i)\}$必须满足的充要条件如下

  - 
    $$
    I(a_i;Y)=C \;对于所有满足p(a_i)>0条件的i \\
    I(a_i;Y)\le C\;对于所有满足p(a_i)=0条件的i
    $$

  - 上述式说明，**当信道平均互信息量达到信道容量时，输入符号概率集**$\{p(a_i)\}$**中每一个符号**$a_i$**对输出端**$Y$**提供相同的互信息，只是概率为零的符号除外**

### 3.3 离散序列信道及容量 

- **对于无记忆离散序列信道**，其转移概率为
  - $s(\vec{Y}|\vec{X})=p(Y_1,\cdots,Y_L|X_1,\cdots,X_L)=\prod_{l=1}^{L}{p(Y_l|X_l)}$
  - 即仅与当前输入有关，若信道是平稳的，则$p(\vec{Y}|\vec{X})=p^L(y|x)$
- 根据平均互信息量的定义
  - $I(\vec{X};\vec{Y})=H(X^L)-H(X^L|y^L)=\sum{p(\vec{X},\vec{Y})}\log{\frac{p(\vec{X}|\vec{Y})}{p(\vec{X})}}=H(Y^L)-H(Y^L|X^L)=\sum{p(\vec{X},\vec{Y})}\log{\frac{p(\vec{Y}|\vec{X})}{p(\vec{Y})}}$
  - 由此可知该互信息有两个性质
    - 其一，如果信道无记忆，则$I(\vec{X};\vec{Y})\le \sum_{l=1}^{L}{I(X_l;Y_l)}$
    - 其二，如果输入矢量$\vec{X}$中的各个分量相互独立，则$I(\vec{X};\vec{Y})\ge \sum_{l=1}^{L}{I(X_l;Y_l)}$
    - 当输入矢量达到最佳分布时：$c_L=\max_{P_X}I(\vec{X};\vec{Y})=\max_{P_X}{\sum_{l=1}^{L}I(X_l;Y_l)}=\sum_{l=1}^{L}\max_{P_X}{I(X_l;Y_l)}=\sum_{l=1}^{L}C(l)$，当信道平稳时$C_L=LC_1$
    - 一般情况下$I(\vec{X};\vec{Y})\le LC_1$
- 典型的无记忆离散序列信道——扩展信道
  - 如果对离散单符号信道进行L次扩展，即形成了L次离散无记忆序列信道，信道输入序列为$\vec{X}=X^L$，其输出序列为$\vec{Y}=Y^L$
  - 信道的序列转移概率为$p(\vec{Y}|\vec{X})=\prod_{l=1}^{L}{p(Y_l|X_l)}$ 
- 无记忆序列信道 

### 3.4 连续信道及其容量

#### 3.4.1 连续单符号加性信道

#### 3.4.2 多维无记忆加性连续信道

#### 3.4.3 限时限频限功率加性高斯白噪声信道

### 3.5多输入多输出信道及其容量（理解即可）

#### 3.5.1 MIMO信道模型

#### 3.5.2 MIMO信道容量

## 4 信息率失真函数

### 4.1 信息率失真函数的性质和概念

#### 4.1.1 失真函数和平均失真
