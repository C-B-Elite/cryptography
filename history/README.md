[![English](https://img.shields.io/badge/English-README-blue)](EnglishReadme.md)


# 第二章：密码学发展简史

密码学早在公元前400多年就已经产生，人类使用密码的历史几乎与使用文字的时间一样长，密码学的发展大致可以分为 3 个阶段: 1949 年之前的古典密码学阶段; 1949 年至 1975 年密码学成为科学的分支; 1976 年以后对称密钥密码算法得到进一步发展，产生了密码学的新方向—公钥密码学。1976 年，W.Diffie 和 M.Hellman 在发表的文章“密码学的新方向”中首次公开提出了公钥密码( Public-key Cryptography) 的概念。公钥密码的提出实现了加密密钥和解密密钥之间的独立，解决了对称密码体制中通信双方必须共享密钥的问题，在密码学界具有划时代的意义。

### 一. 古典密码学

古典密码学的历史可以追溯到公元 400 年前，斯巴达人发明了“塞塔式密码”，即把长条纸螺旋形地斜绕在一个多棱棒上，将文字沿棒的水平方向从左到右书写，写一个字旋转一下，写完一行再另起一行从左到右写，直到写完。解下来后，纸条上的文字消息杂乱无章、无法理解，这就是密文,但将它绕在另一个同等尺寸的棒子上后，就能看到原始的消息。这是最早的密码技术。

我国古代也早有以藏头诗、藏尾诗、漏格诗及绘画等形式，将要表达的真正意思或“密语”隐藏在诗文或画卷中特定位置的记载，一般人只注意诗或画的表面意境，而不会去注意或很难发现隐藏其中的“话外之音”。如《水浒传》中梁山为了拉卢俊义入伙，“智多星”吴用和宋江便生出一段“吴用智赚玉麒麟”的故事来，利用卢俊义正为躲避“血光之灾”的惶恐心理，口占四句卦歌：

    芦花丛中一扁舟，
    俊杰俄从此地游。 　　
    义士若能知此理，
    反躬难逃可无忧。 　

暗藏“卢俊义反”四字。结果，成了官府治罪的证据，终于把卢俊义“逼”上了梁山。

更广为人知的是唐伯虎写的“我爱秋香”：

    我画蓝江水悠悠，
    爱晚亭上枫叶愁。
    秋月溶溶照佛寺，
    香烟袅袅绕经楼。

古代的藏宝图，经过层层的加密化，其实也是我国古典密码学的一个表现。

这一时期的密码学更像是一门艺术，其核心手段是代换和置换。代换是指明文中的每一个字符被替换成密文中的另一个字符，接收者对密文做反向替换便可恢复出明文；置换是密文和明文字母保持相同，但顺序被打乱。代换密码的著名例子有古罗马的凯撒密码（公元前1世纪）和法国的维吉尼亚密码（16世纪）。凯撒密码是对字母表中每个字母用它之后的第k个字母来代换，如，将“comeatnine”加密为“htrjfysnsj”（k=5）。但这种加密方式无法掩盖各字母的频率特征，易被破解。维吉尼亚密码相比之下提升了安全性，它的密钥通常是一个单词，如，“hear”，对于上述明文“comeatnine”，加密时将第1个字母后移8位（密钥“hear”的第一个字母h处于字母表第8位），第2个字母后移5位（密钥的第二个字母e处于字母表第5位），……，因此加密后的结果是“jsmvhxnzui”。

我们大家应该都看过抗战片，里面发报文的时候发的是密文，这个密文会对应一个密码本，比方说《三国演义》这本书。它的加密方式会告诉你加密的文字属于书中的那个字，当你解密完成之后，就可以得到明文的报文。这是一种常见的古典加密方法。

#### 1.几种古典密码学

##### 1.1.滚桶密码

为了保证通信信息的密码性，古希腊人通过使用一根叫scytale的棍子，将信息进行加密。送信人先将一张羊皮条绕棍子螺旋形卷起来，然后把要写的信息按某种顺序写在上面，接着打开羊皮条卷，通过其他渠道将信送给收信人。如果不知道棍子的粗细是不容易解密里面的内容的，但是收信人可以根据事先和写信人的约定，用同样的scytale的棍子将书信解密。

下面是一个例子：

密文：

经大们的意日那方过家参名被的些式短启观字埋凉投进暂程了和在风奔行的去一生教吹他着欢一个前堂来的沟迎家大从里，灵通仪中教事，庭魂。式国堂的是院就后餐。职因里在，馆围业为的风一吃绕。据古中本饭着副说树，正。一市这沙和经途个长样沙一的中天说他作群市。井们响不长副的那死，信公市石底后让神干长板下的人的去先路埋位惬中了生上着置意国，又，死离，人爱兴许人上也用开致多。帝让一玩勃石人最人种笑勃板们近觉超的地上之。得越市带刻所一上语长领着以阵帝言和我人愿夏和的

经过滚筒解密后的明文

.： 
    ![.： 
](/img/1.png)

##### 1.2.掩格密码

16世纪米兰的物理学和数学家Cardano发明的掩格密码，可以事先设计好方格的开孔，将所要传递的信息和一些其他无关的符号组合成无效的信息，使截获者难以分析出有效信息。

##### 1.3.棋盘密码

我们可以建立一张表，使每一个字符对应一数 ， 是该字符所在行标号， 是列标号。这样将明文变成形式为一串数字密文。

##### 1.4. 凯撒（Caesar）密码

在罗马帝国时期，凯撒大帝曾经设计过一种简单的移位密码，用于战时通信。这种加密方法就是将明文的字母按照字母顺序，往后依次递推相同的字母，就可以得到加密的密文，而解密的过程正好和加密的过程相反。

原理：把一个字母替换为它后面固定位置的另一个字母（单表代换密码）。

A B C D E F G …… X Y Z

D E F G H I J …… A B C

明文:Caesar cipher is a shift substitution

密文:FDHVDU FLSKHU LV D VKLIW VXEVWLWXWLRQ

##### 1.5. 弗纳姆密码

1918年Gilbert Vernam 为AT&T设计的一种一次一密乱码本密码（多表代换密码）。

原理：使用一个任意长的不重复数字序列，把它和明文组合在一起。

明文：    V      E     R     N     A     M     C     I     P     H     E     R

等价数字：21     4     17    13    0     12    2     8     15     7    4     17

+随机数： 76    48     16    82    44    3     58   11     60     5    48    88

和mod26： 19    0      7     17   18    15     8    19     23    12    0     1

密文：    t     a      h     r     s     p     i    t      x     m      a    b

##### 1.6.圆盘密码

人们对凯撒密码进一步改善，只要将字母按照不同的顺序进行移动就可以提高破解的难度，增加信息的保密程度。如15世纪佛罗伦萨人Alberti发明圆盘密码就是这种典型的利用单表置换的方法加密的方法。如图在两个同心圆盘上，内盘按不同（杂乱）的顺序填好字母或数字，而外盘按照一定顺序填好字母或数字，转动圆盘就可以找到字母的置换方法，很方便的进行信息的加密与解密。凯撒密码与圆盘密码本质都是一样的，都属于单表置换，即一个明文字母对应的密文字母是确定的，截获者可以分析对字母出现的频率，对密码体制进行有效的攻击。Alberti的圆盘理论是古典密码学的主要代表之一, 在粘土圆盘的表面刻上带有空格的字母, 成为最初人类的加密方式, 这种方式至今还无人能破戒。

##### 1.7. 维吉尼亚密码

为了提高密码的破译的难度，人们有发明一种多表置换的密码，即一个明文字母可以表示为多个密文字母，多表密码加密算法结果将使得对单表置换用的简单频率分析方法失效，其中维吉尼亚密码就是一种典型的加密方法。维吉尼亚密码是使用一个词组（语句）作为密钥，词组中每一个字母都作为移位替换密码密钥确定一个替换表，维吉尼亚密码循环的使用每一个替换表完成明文字母到密文字母的变换，最后所得到的密文字母序列即为加密得到的密文。维吉尼亚是古典密码理论发展上的一个重要里程碑,他的理论又被称为多字母编码。

m个移位代换表由m个字母组成的密钥字确定

明文：w e a  r  d   i  s c o v e r e d s a v e 

密钥：d  e c  e  p  t  i v e d e c e p t i v e 

对应数字：3  4  2 15 19 8 21   

密文：Z  I  C V T WQNGRZGVTWAVZH


##### 1.8.换位密码（置换密码）

1.换位就是将明文中的字母的位置重排。最简单的换位就是逆序法：
      
明文：computer system

密文：metsys retupmoc

2.列置换（纵行换位）：把明文中的字符按列重新排列。
例如：
明文：THIS IS A MESSAGE.

          T   H    I    S    I
          
          S   A    M    E    S
          
          S   A    G    E    X
          
密文：TSSHAAIMGSEEISX

3.引入密钥k

如k=COMPUTER，明文为：WHAT CAN YOU LEARN FROM THIS BOOK

.： 
    ![.： 
](/img/2.png)


密文为：WORO NNSX ALMK HUOO TETX YFBX ARIX CAHX  

##### 1.9.Enigma转轮组的加密

Enigma转轮组的加密原理，正是多表替代——它通过不断改变明文和密文的字母映射关系，对明文字母们进行着连续不断的换表加密操作。 

.： 
    ![.： 
](/img/3.png)



* 三个转子不同的方向组成了26*26*26=17576种不同可能性； 
* 三个转子间不同的相对位置为6种可能性；
* 连接板上两两交换6对字母的可能性数目非常巨大，有100391791500种；于是一共有17576*6*100391791500，大约为10000000000000000，即一亿亿种可能性。

当时一台Enigma转轮组的加密24万人民币。

20世纪30年代领导波兰密码学家率先对德国使用的Enigma密码进行了系统性的研究和破译。在破译过程中，雷耶夫斯基首次将严格的数学化方法应用到密码破译领域，这在密码学的历史上是一个重要成就。雷耶夫斯基等人在二战期间破译了大量来自德国的信息，他们的工作成为整个二战期间盟国破译德军Enigma密码的基础。雷耶夫斯基与波兰数学家杰尔兹·罗佐基和亨里克·佐加尔斯基并称为密码研究领域的“波兰三杰”。

.： 
    ![.： 
](/img/4.png)


### 二. 近代密码学

密码形成一门新的学科是在20世纪70年代，这是受计算机科学蓬勃发展刺激和推动的结果。快速电子计算机和现代数学方法一方面为加密技术提供了新的概念和工具，另一方面也给破译者提供了有力武器。计算机和电子学时代的到来给密码设计者带来了前所未有的自由，他们可以轻易地摆脱原先用铅笔和纸进行手工设计时易犯的错误，也不用再面对用电子机械方式实现的密码机的高额费用。

Arthur Scherbius于1919年设计出了历史上最著名的密码机—德国的Enigma机,，在二次世界大战期间， Enigma曾作为德国陆、海、空三军最高级密码机。Enigma机使用了3个正规轮和1个反射轮。这使得英军从1942年2月到12月都没能解读出德国潜艇发出的信号。转轮密码机的使用大大提高了密码加密速度，但由于密钥量有限，到二战中后期时，引出了一场关于加密与破译的对抗。首先是波兰人利用德军电报中前几个字母的重复出现，破解了早期的Enigma密码机，而后又将破译的方法告诉了法国人和英国人。英国人在计算机理论之父——图灵的带领下，通过寻找德国人在密钥选择上的失误，并成功夺取德军的部分密码本，获得密钥，以及进行选择明文攻击等等手段，破解出相当多非常重要的德军情报。

这一阶段真正开始源于香农在20世纪40年代末发表的一系列论文，特别是1949年的《保密系统通信理论》，把已有数千年历史的密码学推向了基于信息论的科学轨道。近
代密码发展中一个重要突破是“数据加密标准”（DES）的出现。DES密码的意义在于，首先，其出现使密码学得以从政府走向民间，其设计主要由IBM公司完成，国家安全局等政府部门只是参与其中，最终经美国国家标准局公开征集遴选后，确定为联邦信息处理标准。其次，DES密码设计中的很多思想（Feistel结构、S盒等），被后来大多数分组密码所采用。再次，DES出现之后，不仅在美国联邦部门中使用，而且风行世界，并在金融等商业领域广泛使用。


### 三. 现代密码学

1976 年，美国密码学家提出“公钥密码”概念。此类密码中加密和解密使用不同的密钥，其中，用于加密的叫做公钥，用于解密的为私钥。1977年，美国麻省理工学院提出第一个公钥加密算法RSA算法，之后ElGamal、椭圆曲线、双线性对等公钥密码相继被提出，密码学真正进入了一个新的发展时期。一般来说，公钥密码的安全性由相应数学问题在计算机上的难解性来保证，以广为使用的RSA算法为例，它的安全性是建立在大整数素因子分解在计算机上的困难性，如，对于整数22，我们易于发现它可以分解为2和11两个素数相乘，但对于一个500位的整数，即使采用相应算法，也要很长时间才能完成分解。但随着计算能力的不断增强和因子分解算法的不断改进，特别是量子计算机的发展，公钥密码安全性也渐渐受到威胁。目前，研究者们开始关注量子密码、格密码等抗量子算法的密码，后量子密码等前沿密码技术逐步成为研究热点。

### 四.量子密码学

量子密码术是一种新的重要加密方法,它利用单光子的量子性质,借助量子密钥分配协议可实现数据传输的可证性安全.量子密码具有无条件安全的特性(即不存在受拥有足够时间和计算机能力的窃听者攻击的危险),而在实际通信发生之前,不需要交换私钥.本文综述了量子密码学的研究进展,其中包括了量子密码学的物理基础、量子密钥分配、保密增强、量子密钥的实用性以及目前技术限制所存在的缺陷。


### 五.密码学的前景

1976 年 Diffie 和 Hellman 的公钥密码的思想提出，标志着现代密码学的诞生，在国际密码学发展史上是具有里程碑意义的大事件，自此国际上已提出了许多种公钥密码体制  ，如基于分解大整数的困难性的密码体制——RSA 密码体制及其变种、基于离散对数问题的公钥密码体制——ElGamal 密码体制及其变种 ECC 等等，这些都得到了广泛的应用，并且为当今信息化时代提供了各种各样的安全性服务(如机密性、可信性(鉴别)、完整性、不可否认性  、可用性以及访问控制等)。这些公钥密码体制的安全性均依赖于数学难题(大整数分解难题和离散对数求解难题)的困难性．然而这些问题在量子计算情形下经过 Shor 算法均可变为易解问题——P问题，因而我们可以断言量子计算机出现之日，便是现今密码寿终正寝之日。因此，研究抗量子的计算的密码算法是未来密码学的新的研究方向。

