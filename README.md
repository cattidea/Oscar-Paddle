# Oscar-Paddle

基于[paddle](https://github.com/PaddlePaddle/Paddle)框架的[Oscar: Object-Semantics Aligned Pre-training for Vision-Language Tasks](https://arxiv.org/abs/2004.06165)实现

## 一、简介

本项目使用[paddle](https://github.com/PaddlePaddle/Paddle)框架复现[Oscar](https://arxiv.org/abs/2004.06165)模型。该模型借助目标类别`Object Tags`来实现更好的视觉和文本的跨模态对齐。作者引入`Object Tags`并基于此提出了两个损失函数进行大规模的预训练，使得能够学习到文本和图像区域的语义对齐表征。实验表明，作者在多个 vision-language 任务上得到了有效的提升。

**注: AI Studio项目地址: [https://aistudio.baidu.com/aistudio/projectdetail/2609611](https://aistudio.baidu.com/aistudio/projectdetail/2609611).**

**您可以使用[AI Studio](https://aistudio.baidu.com/)平台在线运行该项目!**

**论文:**

* [1] X. Li, X. Yin, C. Li, and et. al, "Oscar: Object-Semantics Aligned Pre-training for Vision-Language Tasks", ECCV, 2020.

**参考项目:**

* [Oscar](https://github.com/microsoft/Oscar) [官方实现]

## 二、复现精度

> 本项目验证其在图文检索`Image-Text Retrieval`下游任务中的性能，所使用的数据集为[COCO2014](https://cocodataset.org/)，复现精度如下（参考原论文Table 2）。

<table>
    <tr align="center">
        <td></td>
        <td colspan="3" >Text Retrieval</td> 
        <td colspan="3">Image Retrieval</td>
    </tr>
    <tr align="center">
        <td></td>
        <td>R@1</td>
        <td>R@5</td>
        <td>R@10</td>
        <td>R@1</td>
        <td>R@5</td>
        <td>R@10</td>
    </tr>
    <tr align="center">
        <td>原论文</td>
        <td>89.8</td>
        <td>98.8</td>
        <td>99.7</td>
        <td>78.2</td>
        <td>95.8</td>
        <td>98.3</td>
    </tr>
    <tr align="center">
        <td>复现精度</td>
        <td>89.8</td>
        <td>98.8</td>
        <td>99.7</td>
        <td>78.2</td>
        <td>95.8</td>
        <td>98.3</td>
    </tr>
</table>

## 三、数据集

本项目所使用的数据集为[COCO2014](https://cocodataset.org/)。该数据集共包含123287张图像，每张图像对应5个标题。训练集、验证集和测试集分别为113287、5000、5000张图像及其对应的标题。本项目使用预提取的`bottom-up`特征，可以从[这里](https://biglmdiag.blob.core.windows.net/oscar/datasets/coco_ir.zip)下载得到。


## 四、环境依赖

* 硬件：CPU、GPU

* 软件：
    * Python 3.7
    * PaddlePaddle-GPU == 2.2.1
    * PaddleNLP==2.2.1

## 五、快速开始

### step1: clone 

```bash
# clone this repo
git clone https://github.com/cattidea/Oscar-Paddle.git
cd Oscar-Paddle
```

### step2: 安装环境及依赖

```bash
pip install -r requirements.txt
```

### step3: 下载数据

```bash
# 下载数据集及特征
bash ./download_dataset.sh
```

### step4: 训练

### step5: 测试

### 使用预训练模型进行预测

## 六、代码结构与详细说明

```bash
├── config                    # 默认配置文件夹
│   └── default.py            # 默认配置参数
├── configs                   # 指定配置文件夹
│   └── retrieval_train.yaml  # 训练配置文件
│   └── retrieval_test.yaml   # 测试配置文件
├── datasets
│   └── retrieval_dataset.py  # 数据加载
├── models
│   └── bert.py               # bert模型
│   └── oscar.py              # oscar模型
├── solvers
│   └── optimizer.py          # 优化器
│   └── scheduler.py          # 学习率策略
├── tests                     # 测试文件
├── tools
│   └── train_retrieval.py    # 训练脚本
│   └── test_retrieval.py     # 测试脚本
└── requirement.txt           # 依赖包
```

## 七、模型信息

关于模型的其他信息，可以参考下表：

|   信息   |                             说明                             |
| :------: | :----------------------------------------------------------: |
|  发布者  |                           fuqianya                           |
|   时间   |                           2022.01                            |
| 框架版本 |                         Paddle 2.2.1                         |
| 应用场景 |                            多模态                            |
| 支持硬件 |                           GPU、CPU                           |
| 下载链接 | [预训练模型](https://drive.google.com/file/d/19gbGuVm9hgVPm_XzAUrTpeDmObr5ZAv3/view?usp=sharing) \| [训练日志](https://drive.google.com/file/d/1hwXfZUy3V2YnsBKQkQADvACTyXYqvLFa/view?usp=sharing) |