![](https://github.com/Jeremyczhj/FashionAI_Tianchi_2018/blob/master/datasets/3.jpg)
---
* 天池大数据竞赛——FashionAI全球挑战赛—服饰属性标签识别
* FashionAI Global Challenge—Attributes Recognition of Apparel
* 记录一下在比赛过程中踩过的坑，比赛最终成绩为决赛21名
---
### 环境
* ubuntu16.04/windows10
* python 3.6.2
* keras 2.1.6
* tensroflow 1.8.0
* opencv-python 3.4
* imgaug 0.2.5

### 使用
* 因为懒，代码写完就跑，跑完就算，没封装得多好
* config.py——配置了样本目录等信息
* Multitask_train.py——训练脚本
* Multitask_predict——预测脚本
* dataset.py——数据预处理脚本
* cal_std_mean.py——计算数据集的std与mean
* inceptionv4.py——模型API

### 思路分享
* 迁移学习+多任务学习+模型融合
* 分别设计了两个多任务模型结构如下：
    * 长度类别多输出模型：
![](https://github.com/Jeremyczhj/FashionAI_Tianchi_2018/blob/master/datasets/1.png)
    * 领子类别多输出模型：
![](https://github.com/Jeremyczhj/FashionAI_Tianchi_2018/blob/master/datasets/2.png)
* 融合Inceptionv4与Inceptionresnetv2，分别进行预测再对结果做平均
* 对测试集样本进行增广

### 提高分数的技巧
* shuffle
* 合适的图像增广，推荐使用imgaug，功能强大
* 图像标准化，计算本数据集的std与mean，而不是直接用imagenet的std与mean
* finetune，算力允许的前提下finetune整个模型
* 使用Adam先快速收敛，再用SGD慢慢调效率会比较高
* 模型融合
* 对测试集进行增广，本例选择了镜像，加上旋转5、10、15度进行预测，最后再取平均。

      
