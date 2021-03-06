### 范围 
和PPML’19一样

- ML的安全多方计算技术 secure multi-party computation techniques for ML
- ML的同态加密技术 homomorphic encryption techniques for ML
- 实现隐私保护机器学习的基于硬件的方法 hardware-based approaches to privacy preserving ML
- 集中式和分散式协议，用于学习加密数据 centralized and decentralized protocols for learning on encrypted data
- 差分隐私：理论，应用和实现 differential privacy: theory, applications, and implementations
- 隐私的统计概念，包括差分隐私的放宽 statistical notions of privacy including relaxations of differential privacy
- 不同隐私概念之间的经验和理论比较 empirical and theoretical comparisons between different notions of privacy
- 隐私与实用性之间的权衡 trade-offs between privacy and utility

### Key Concept

#### Differential Privacy 差分隐私
https://blog.csdn.net/forest_open/article/details/81429458

衡量一套机制中（算法+数据集）对于个体的隐私保护程度。
如果对于任何一个可能查询结果，机制M对于任何相邻数据集的查询结果都**几乎不可区分**，那么就说机制M是满足差分隐私机制的。

#### Rényi差分隐私 Rényi Differential Privacy

Rényi差分隐私是差分隐私的细致化版本。它提供了一种使纯差分隐私（pure DP），近似差分隐私（approximate DP）和集中差分隐私（Concentrated Differential Privacy）相统一的观点。Rényi差分隐私在数据集被一系列随机机制处理后的情况下特别有用。

#### Membership inference 成员推断

给定一组数据，来推断一个模型的训练中是否使用了这组数据。已知这组数据在某几个上下文中是敏感的。

#### GDPR

《通用数据保护条例》（General Data Protection Regulation），欧洲联盟的条例。

#### Fully Homomorphic Encryption and Homomorphic Encryption 全同态加密和同态加密

同态加密是指一种在**不给出对数据的访问权限**的情况下**委托处理数据**的方法。同态加密提供了一种对加密数据进行处理的功能。也就是说，其他人可以对加密数据进行处理，但是处理过程不会泄露任何原始内容。同时，拥有密钥的用户对处理过的数据进行解密后，得到的正好是处理后的结果。

全同态加密算法是指一种算法同时满足：1.加法同态f(A)+f(B)=f(A+B) 2.乘法同态f(A)×f(B)=f(A×B)

#### privacy budget 隐私预算

衡量差分隐私的一个参数，表示一个贡献者对于输入数据集的隐私损失。

#### fedarated learning联邦学习

federated learning是一种训练数据去中心化的机器学习解决方案，最早于2016年由谷歌公司提出，目的在于通过对保存在大量终端的分布式数据开展训练学习一个高质量中心化的机器学习模型，解决数据孤岛的问题。

### ACCEPTED PAPERS

#### LEASGD: an Efficient and Privacy-Preserving Decentralized Algorithm for Distributed Learning 

Hsin-Pai Cheng, Patrick Yu, Haojing Hu, Feng Yan, Shiyu Li, Hai Li and Yiran Chen

##### 摘要
**分布式学习系统**使得在短时间内可以对大量数据进行大规模模型训练。 在本文中，我们专注于去中心化（decentralized）分布式深度学习系统，旨在以良好的收敛速度和较低的通信成本实现**差分隐私（differential privacy）**。 为了实现此目标，我们提出了一种新的**学习算法LEASGD（Leader-Follower Elastic Averaging Stochastic Gradient Descent）**，该算法由新颖的**Leader-Follower拓扑和差分隐私模型**驱动。 我们对收敛速度以及私有环境中性能与隐私之间的权衡进行了理论分析。 实验结果表明，LEASGD的性能优于最新的分散式
学习算法DPSGD，其方法是在同一迭代中稳定地降低损耗，并将通信成本降低30％。 此外，与私人设置下的DPSGD相比，LEASG花费的差异性隐私预算更少，并且最终准确性更高。

##### 背景和动机

分布学习系统+大训练集的情况越来越多， 但这种结构的系统隐藏泄露风险大，因为中心服务器存储所有关键数据。=》要用去中心化分布式学习系统

去中心化分布式学习系统有收敛速度慢，通信成本高和无法保证差分隐私的问题。=》开发对于算法

##### 工作

开发一种通用的去**中心化**学习方法，该方法具有更好的适用性，有良好的**收敛速度**和较低的**通信成本**并可实现**差分隐私**。

### Differentially Private Bayesian Inference for Exponential Families 

Garrett Bernstein and Daniel Sheldon

#### 摘要

当人们对来自敏感来源的数据进行分析时，人们越来越关注**私密推理（private inference）**，由此引发了对它的研究。 我们提出了第一种在**指数族**（exponential families）中进行**私密贝叶斯推理**（private Bayesian inference）的方法，该方法可以适当考虑隐私机制引入的噪声。它之所以有效是因为它仅适用于足够的统计数据，而不适用于单个数据。与其他方法不同，它在非渐近数据方案中给出了正确校准的后验信念。

#### 背景和动机

**满足差分隐私的私密算法（differentially private algorithms）**在机器学习任务中很重要。

#### 工作
当用贝叶斯推断计算后验P(theta|x)时不希望将x泄露，找到一种算法来生产y=A(x)≈P(theta|x)，并使y满足差分隐私。并可用P(theta|y)量化后验信念。

### Privacy-preserving Prediction  

Cynthia Dwork and Vitaly Feldman

#### 摘要
确保从敏感用户数据中学到的模型满足**差分隐私**是一项重要目标，近年来已进行了广泛研究。现已知道，对于一些基本的学习问题，尤其是涉及高维数据的问题，与没有隐私的学习相比，生成准确的私密模型需要更多的数据。同时，在许多应用程序中，不必公开模型本身。取而代之的是，可以仅通过适当的界面允许用户根据其输入查询预测模型。在这里，我们提出了确保各个预测的隐私性的问题，并在几个分类和回归的标准模型中研究了实现该预测所需的开销。我们首先描述一种简单的基线方法，该方法基于对不相交的数据子集训练几个模型并使用标准的私密聚合（Aggregation）技术进行预测。我们证明对于（任何类型的）**布尔函数**的（可实现的）PAC学习，这种方法几乎具有最佳的样本复杂度。同时，在没有强大数据假设前提下，聚合步骤会带来大量开销。我们证明，对于一条直线上经过深入研究的阈值类别以及凸回归的许多标准设置（the well-studied class of thresholds on a line and for a number of standard settings of convex regression），可以避免这种开销。对我们的学习阈值的算法的分析依赖于我们为所有差分私密预测算法建立的强泛化保证（strong generalization guarantees）

#### 背景和动机
有些训练数据敏感=》希望数据满足差分隐私=》但需要很多额外的花费（substantial additional cost）=》开发新的计算效率较低的算法

考虑一种模式，使用者不能访问整个预测模型，而只能通过特定接口访问数据和模型的特定部分。使访问到的特定部分（即使结合该使用者之前访问到的结果也）一直满足差分隐私。这样就能防范**成员推断攻击（membership inference attacks）**。

#### 工作
实现一种类似于上述模式的算法

### Distributed and Secure ML with Self-tallying Multi-party Aggregation

#### 摘要
保持隐私的多方计算在医学和在线广告等领域有许多应用。 在这项工作中，我们提出了一个在不受信任的个人之间进行分布式安全机器学习的框架。该框架由两部分组成：基于**同态加法（homomorphic addition）的两步训练协议**和**数据有效性的零知识证明**。 通过结合这两种技术，我们的框架提供了每个用户数据的私密性，防止恶意用户将损坏的数据添加到共享池，使每个用户无需依赖外部可信第三方即可自行计算算法的结果，并且不需要用户组之间的私密通道。 我们展示了不同的ML算法（例如隐狄利克雷分配模型-Latent Dirichlet Allocation，朴素贝叶斯，决策树等）如何适应我们的分布式安全计算框架。

#### 背景和动机
ML越来越多使用**原始数据**并共享数据进行**联合训练**，这样有很多好处但也更容易涉及到隐私。

#### 工作
提出一种框架用于机器学习的联合训练并满足以下几个特点：
1. 用于不受信任的个体
2. 联合训练模型但不暴露自己部分的数据
3. 对恶意用户的非法（恶意的用于攻击的）数据有鲁棒性
4. 不需要可信任的外部代理

### An Algorithmic Framework For Differentially Private Data Analysis on Trusted Processors

Joshua Allen, Bolin Ding, Janardhan Kulkarni, Harsha Nori, Olga Ohrimenko and Sergey Yekhanin

#### 摘要
**差分隐私**已成为私有数据分析和机器学习的主要定义。假设用户信任数据收集器的全局差分隐私模型提供了强有力的隐私保证，并在输出中引入了小错误。相反，Apple，Google和Microsoft在商业系统中的差分隐私应用程序使用本地模型。这里，用户不信任数据收集器，因此在将其数据发送到数据收集器之前将其数据随机化。不幸的是，局部（差分）模型对于一些重要应用来说太强大了，因此这些应用受到限制。在这项工作中，我们提出了一个基于受信任处理器的框架和一个称为**“遗忘差分隐私”（Oblivious Differential Privacy）**的**差异性隐私新定义**，该定义结合了**局部（差分）模型**和**全局（差分）模型**中的优点。 我们在此框架中设计的算法显示了流算法（streaming algorithms），遗忘算法和差分隐私这三种有趣观点的相互作用。

#### 背景和动机
机器学习中使用原始数据涉及到的隐私问题是个挑战。局部（差分）模型（local model）在很多应用中很重要，但隐私性不强。

#### 工作
形式化受信任处理器环境中的差分私有算法的设计，共享包括：
1. 提出了一个框架，该框架可以在不依赖可信赖的管理者的情况下，在差分隐私的全局模型中收集和分析数据。我们的框架使用加密和安全处理器来保护数据和计算，以便仅显示最终的差分私密输出。
2. 可信任的执行环境对算法的设计施加了某些限制。我们将数学模型形式化，以设计可信任的执行环境（Trusted Execution Environments，TEEs）中的差分私密算法。
3. 定义了一类新的差分私密算法，称为遗忘差分私密算法（ODP），该算法可以确保通过算法的内存访问模式和输出所发生的隐私泄漏一起满足差分隐私保证。
4. 证明了该算法的隐私和错误保证明显优于局部模型。

### Toward privacy in IoT mobile devices for activity recognition

Antoine Boutet, Théo Jourdan and Carole Frindel

#### 摘要
用于个人医疗保健的无线传感器的最新进展允许移动设备识别人类的实时活动。从健康的角度来看，对这些数据流进行分析可以带来很多好处，但是通过暴露高度敏感的信息，也可能导致隐私威胁。在本文中，我们提出了一种用于活动识别的隐私保护框架。该框架依靠一种机器学习技术来有效识别用户活动模式，这对个人医疗保健监控很有用，同时限制了从表征每个人的生物特征模式重新识别用户的风险。为实现这一目标，我们在时域和频域均依赖精心的特征提取方案，并对导致用户重新识别的特征应用基于归纳的方法。我们使用参考数据集广泛评估了我们的框架：结果显示了准确的活动识别（87％），同时限制了重新识别率（33％）。与最新的基准相比，这表示实用性略有下降（9％），而隐私权得到了大幅改善（53％）。

#### 背景和动机
IoT和移动设备广泛发展，本文基于用于医疗领域的识别人类活动模式的移动设备的背景。要防止根据活动模式来**反向重新识别个体（user re-identification）**的风险，以防隐私泄露。

#### 工作
设计一种用于上述背景的**物联网**隐私保护框架，在准确度下降不明显的情况下，较大地提高了隐私保护程度。（通过模糊化和处理在重新识别个体中贡献度高的特征）

### CHET: Compiler and Runtime for Homomorphic Evaluation of Tensor Programs 

Roshan Dathathri, Olli Saarikivi, Hao Chen, Kim Laine, Kristin Lauter, Saeed Maleki, Madanlal Musuvathi and Todd Mytkowicz

#### 摘要
**全同态加密（FHE）**提供了对加密数据执行任意计算而无需解密密钥的承诺。FHE使新颖的隐私敏感型机器学习方案成为了可能。但是，由于两个挑战，如今对于非FHE专家来说，**对FHE应用进行编程非常困难**。首先，要达到实际性能，需要执行特定于FHE的优化，包括最大化基础FHE方案的矢量化/批处理功能。其次，FHE方案涉及对加密参数的谨慎选择，这些加密参数需要权衡安全性以确保正确性，性能和消息膨胀（message bloat）。本文提出了CHET，一种用于同态评估张量程序的编译器和运行环境。给定一个指定为高级张量电路的神经网络，CHET将该电路优化并编译到称为同态指令集体系结构（HISA）的接口，然后可以将该接口定向到不同的加密库。CHET自动选择加密参数和布局，以针对给定的安全性和精度要求最大化性能。结果，CHET生成的代码比专家优化的实现要快。

#### 背景和动机
FHE技术在未来机器学习领域很重要，但存在一些技术难点（参数调节，优化等）使非FHE专家难以将其灵活应用到具体问题。

#### 工作
设计一种用于张量程序的同态评估的编译器和运行环境。这套框架使非FHE专家能够FHE技术用于机器学习模型（张量程序），并在性能上超过人类专家。

### Learning Representations for Utility and Privacy: An Information-Theoretic Based Approach  

Martin Bertran, Natalia Martinez, Afroditi Papadaki, Qiang Qiu, Miguel Rodrigues and Guillermo Sapiro

#### 摘要
在公开相关信息（功能）的同时保护秘密是众所周知的隐私领域的挑战。用户和服务提供商都可以并且应该合作保护隐私，本文将探讨这种范例。在这里，我们分析了**信息理论隐私**的局限性，并使用这些限制来设计公开数据X的数据驱动的隐私保护表示形式，该表示形式**最大程度地公开了功能变量U**，而**最小程度地公开了秘密变量S**。我们考虑一种重要的常见情况，即功能提供商愿意，至少，部分地在清理过程（sanitization process）进行协作的情况。在这种情况下，我们将可能的清理功能限制为保留空间的转换（space-preserving transformation），在该空间中，可以使用相同的算法来推断清理和未清理数据上的功能变量。我们通过两个用例说明了这种方法。subject-withinsubject，我们解决的问题是拥有一个仅适用于同意的用户子集的身份检测器（来自面部图像）；以及emotion-and-gender，我们解决隐藏自变量的问题，例如在保留情感检测的同时隐藏性别的情况。

#### 背景和动机
数据X相关于两个潜变量空间U和S。**U为功能潜变量**，**S为秘密潜变量**。希望尽可能多地传递U的同时，尽可能少的暴露S。

#### 工作
提出一种基于**信息论**的框架解决上述问题。用两类例子证明其实用性和合理性。

### Slalom: Fast, Verifiable and Private Execution of Neural Networks in Trusted Hardware 

Florian Tramer and Dan Boneh

#### 摘要
随着机器学习（ML）应用于安全性至关重要或敏感的领域，对外包ML计算的完整性和私密性的需求日益增长。实用的解决方案来自**受信任的执行环境（TEE）**，该环境使用硬件和软件保护来将敏感计算与不受信任的软件堆栈隔离开。但是，与不受信任的替代方案相比，这些隔离保证是以**性能**为代价的。本文通过在受信任和不受信任的设备之间**有效划分DNN计算**，开始研究TEE中的深度神经网络（DNN）的高性能执行。我们基于有效的矩阵乘法外包方案，提出了Slalom，这是一个框架，可将DNN中所有线性层的执行安全地从TEE（例如Intel SGX或Sanctum）委托到更快但不受信任的同地协作（co-located）处理器。我们通过在英特尔SGX安全区中运行DNN来评估Slalom，该区域选择性地将工作委托给不受信任的GPU。对于规范的DNN （VGG16，MobileNet和ResNet变体），对于可验证的推理，我们因此将吞吐量提高6倍至20倍，对于可验证和私密推理则因此将吞吐量提高4倍至11倍。

#### 背景和动机
机器学习所以运算都基于受信任的执行环境的话，保证了安全，但性能差。

#### 工作
提出一种用于**DNN**的执行框架，对需要的**计算进行划分**，有效在**不暴露隐私**的情况下将一部分计算由受信任的执行环境转移到不受信任的执行环境。以提高运算性能。

### Three Tools for Practical Differential Privacy 
Koen Lennart van der Veen, Ruben Seggers, Peter Bloem and Giorgio Patrini

#### 摘要
对现实世界数据进行满足差分隐私的学习给标准的机器学习实践带来了挑战：隐私保证难以解释，对私密数据进行超参数调整会减少隐私预算（privacy budget），并且经常需要临时隐私攻击来测试模型隐私。 我们引入了三种**工具**来使满足差分隐私的机器学习更加实用：（1）简单的健全性检查（sanity checks），可以在训练之前以集中方式进行;（2）引入自适应的限制界线，以减少可调整的私密参数的数量;以及（3）我们证明了大批量训练可以提高模型性能。

#### 背景和动机
差分隐私的实现在机器学习中非常重要，但大多数现有的工作都是在保证性能和私密性中一者达到某一目标的情况下，尽可能提高另一者。但少有工作研究满足差分隐私的机器学习在实际应用中的一些**准则**，例如对于给定任务需要多大程度的隐私，如何优化参数和超参数等。

#### 工作
提出三种通用**工具**用于开发满足差分隐私的机器学习。

### How to Profile Privacy-Conscious Users in Recommender Systems 

Fabrice Benhamouda and Marc Joye

#### 摘要
矩阵分解是一种构建推荐系统的流行方法。在这样的系统中，现有用户和物品与称为**简况（profile）**的低维向量相关联。通过用户和物品的简况向量。可以（通过内积）计算来预测某个用户对某个商品的评价。这种系统的一个重要问题是所谓的冷启动问题：如何允许用户刻画她的个人简况，以便随后获得准确的建议？
如果用户愿意对精心挑选的商品进行评分和/或提供补充属性或人口统计信息（例如性别），则可以计算很好的简况，但已知可以通过此附加信息，从而使推荐系统的分析师可以推断出更多个人敏感信息。我们设计了一个协议，以使**注重隐私的用户（Privacy-Conscious Users）**可以在保留其隐私的同时受益于基于矩阵分解的推荐系统。更准确地说，我们的协议使用户能够刻画他的个人简况，而无需用户透露任何个人信息。该协议在标准模型中针对**半诚实的对手（semi-honest adversaries）**是安全的。

#### 背景和动机
推荐系统的冷启动问题=》用户不给出个人信息则推荐系统初期对其效果不好，给出个人信息则有被恶意的分析师推理出个人敏感信息的风险

#### 工作
提出一种在一定限制下可以在用户不暴露个人信息的情况下，为推荐系统完成个人简况的刻画。限制包括：半诚实的对手、标准模型、注重隐私的用户。


### Privacy Amplification by Iteration

Vitaly Feldman, Ilya Mironov, Kunal Talwar and Abhradeep Thakurta

#### 摘要
许多常用的学习算法通过在每次迭代中使用一个或几个数据点**迭代**更新中间解决方案来工作。针对此类算法的差分隐私的分析通常涉及确保每个步骤的隐私，然后对算法的累积隐私成本进行推理。这可以通过差分隐私的合成定理来实现，这些定理允许发布所有中间结果。在这项工作中，我们证明了对于压缩迭代，不发布中间结果会极大地**保密增强（privacy amplification）**保证。
我们描述了这种新的分析技术通过噪声随机梯度下降（noisy stochastic gradient descent.）解决**凸优化问题**的几种应用。例如，我们证明了来自相同分布的少量的非私密数据点可用于缩小私密和非私密凸优化之间的差别。此外，我们证明，我们可以实现 与使用**采样保密增强技术（privacy-amplification-by-sampling technique）**获得的保证 类似的保证，在无法应用这种技术的几种自然环境中。

#### 背景和动机
**保密增强（privacy amplification）**对于管理隐私预算（privacy budget）很重要。采样保密增强（privacy amplification by sampling）是现有**唯一的**在机器学习领域对这一问题的系统研究，即这方面的研究很少。（采样保密增强证明：an ε-differentially private mechanism applied to a secretly sampled p fraction of the input satisfies O(pε)-differential privacy.）


#### 工作
在一定背景下（noisy stochastic gradient descent for a smooth and convex objective），提出一种新的关于保密增强的基于迭代的论据。为相关研究提供更多的理论基础。

### Learning rate adaptation for differentially private stochastic gradient descent

Antti Koskela and Antti Honkela

#### 摘要
我们提出了一种**自适应的调节随机梯度下降（SGD）的学习率**的算法，该算法**无需使用验证集**。自适应的思想来自于外推法（extrapolation）：要获得SGD的梯度流的误差估计，我们将一整步和两个半步的结果进行比较。该算法在两个单独的框架中应用：**联邦学习（（federated learning）**和**差分隐私学习**。通过使用深层神经网络的示例，我们从经验上表明，对于满足差分隐私的训练，自适应算法与手动使用常用优化方法来调节相比具有竞争力。我们还表明，与常用的优化方法不同，它在联合学习的情况下运行稳定（robustly）。

#### 背景和动机
**SGD**和其变种算法在机器学习和深度学习中使用广泛。这些算法对**学习率**很敏感，实际往往需要**大量的尝试**。这种为了调节超参数而进行的反复学习和验证集的多次使用对于**差分隐私学习**很不利，因为这会造成额外的隐私损失。类似的，**联邦学习**也不支持验证集的多次使用。

#### 工作
提出一种**自适应的调节随机梯度下降的学习率**的算法，该算法**无需使用验证集**，用于**联邦学习**和**差分隐私学习**之中。

### Subsampled Renyi Differential Privacy and Analytical Moments Accountant 

Yu-Xiang Wang, Borja Balle and Shiva Kasiviswanathan

#### 摘要
我们研究了差分隐私（DP）中的**二次采样（subsampling）**问题，该问题是许多成功的差分隐私机器学习算法背后的核心。具体来说，我们为以下算法提供了严格的**Rényi差异隐私（Rényi Differential Privacy）**（Mironov，2017）参数上限：（1）对数据集进行二次采样，然后（2）根据以下参数对子采样应用随机机制M： M的RDP参数和二次采样概率参数。 我们的结果概括了由Abadi等人为高斯机制开发的**时刻会计（moments accounting）**技术，适用于任何二次采样的RDP机制。

#### 背景和动机
**二次采样（subsampling）**是设计DP算法时实现隐私增强的重要工具，但为二次采样机制**计算对应的RDP参数**不容易。

#### 工作
分析在**二次采样机制**下的**RDP增强**，即二次采样对于实现RDP的作用。得到在这种机制下，对应**RDP参数的严格上限**。发现新的有研究意义的理论参数。

### A generic framework for privacy preserving deep learning

Theo Ryffel, Andrew Trask, Morten Dahl, Bobby Wagner, Jason Mancuso, Daniel Rueckert and Jonathan Passerat-Palmbach

#### 摘要
我们详细介绍了用于保护深度学习的隐私的新框架，并讨论了其有益之处。该框架非常重视数据的所有权和数据的安全处理，并基于指令和张量链（chains of commands and tensors）引入了有价值的表示形式。这种抽象允许人们实施复杂的隐私保护构造，例如联邦学习（Federated Learning），安全多方计算（Secure Multiparty Computation）和差分隐私，同时仍然向终端用户展示熟悉的深度学习API。 我们报告了早期在波士顿房价和皮马印第安人糖尿病数据集上的结果。尽管除差分隐私之外的隐私特征不会影响预测准确性，但该框架的当前实现会造成大量的性能开销，这将在开发的后续阶段解决。我们认为，这项工作是一个重要的里程碑，它引入了第一个可靠的，**通用的隐私保护深度学习框架**。

#### 背景和动机
**安全多方计算（Secure Multiparty Computation）**越来越多地用于不信任环境中。机器学习中也用此来让多节点共同训练模型，一个典型例子就是**联邦学习（Federated Learning）**。但被证明通过反向工程攻击仍可以从模型中提取敏感信息。另一系列方法，被称为**差分隐私（DP）**方法，可以有效保护数据和隐私问题。简单来说，这三项技术很重要并且相互弥补，希望能在一个通用框架下共同实现。

#### 工作
提出一种**通用的隐私保护深度学习框架**（基于新提出的**协议**），使pytorch使用者能够通过直观的接口来应用**SMPC、FL和DP**。
