## 开题报告

### 论文题目
YOLO在焊点检测的应用

### 项目简介
YOLO（YOU ONLY LOOK ONCE）是目标检测神经网络中比较著名的一个，有着优于其他网络的速度和令人满意的精度。焊点检测是机器人焊接过程中确定焊点的过程。在本文所涉及的项目中，机器人需要确定金属架横杆与立柱的焊接位置。由于工件本身精度不高，所以需要视觉补偿误差，又由于金属件本身存在生锈，镜面反光，形状不规则等特点，传统机器视觉的检测方案无论是灰度匹配还是边缘匹配都无法达到检测要求，因此需要引入深度学习的方案。
本文将使用YOLO神经网络根据实际拍摄图片，在原生darknet或pytorch框架下进行训练，生成具有定位焊点能力的模型验证可行性，然后通过剪枝的方法在基本不影响精度的情况下缩小模型，提高推理速度，最后寻找合适的方式部署在Jetson Nano上，进行性能测试。

### 已经完成的部分
可行性验证已完成
![](https://github.com/zhengli233/yolo_for_welding/raw/master/开题报告/images/predictions.jpg)

![](https://github.com/zhengli233/yolo_for_welding/raw/master/开题报告/images/predictions1.jpg)

![](https://github.com/zhengli233/yolo_for_welding/raw/master/开题报告/images/predictions2.jpg)

![](https://github.com/zhengli233/yolo_for_welding/raw/master/开题报告/images/predictions3.jpg)

![](https://github.com/zhengli233/yolo_for_welding/raw/master/开题报告/images/predictions4.jpg)

### 未完成的部分
1. YOLO与其他网络模型的比较
2. 剪枝。但已有现成剪枝工具
3. 不同剪枝后的比较
4. 部署，难点在于充分发挥硬件的性能。硬件已有，但具体使用什么框架，cpu与gpu数据交互优化还需要尝试

### 创新点
1. 将YOLO用在焊点检测勉强算一个，在知网上初步查了一下，中文文献非常少，只有3篇
2. 在应用上，剪枝是常见优化方法，但学术界一般不会为了一个具体应用走到这一步，那3篇其中一篇考虑到了运算时间，但做的是网络结构的精简，而非剪枝
3. Jetson Nano硬件于去年年底上市，有一块arm cortex-a57 cpu和一块有128cuda核心的gpu，用的人应该不多，虽然社区比较活跃，但没有中文社区，知网上没有相关文献。这个硬件我最初是买来玩的，但后来公司的一个子公司似乎做了将YOLO网络部署在这个硬件上的尝试，因为它相比于工控机，实在便宜太多了，1000块不到。因此部署在这个硬件上既新又有可行性。

### 文献
[1]裴泽中. 汽车门板焊接部件和焊点识别算法研究[D].华南理工大学,2019.

[2]何智成,王振兴. 基于改进YOLOv2的白车身焊点检测方法[J/OL]. 计算机工程:1-11.https://doi.org/10.19678/j.issn.1000-3428.0056446.

[3]曾健. 基于深度学习的汽车门板焊点识别算法研究及应用[D].华南理工大学,2019.