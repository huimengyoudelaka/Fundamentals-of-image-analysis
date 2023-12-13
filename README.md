

# 图像分析基础大作业

本次实验提出了Sigmoid和Pow两种Theta Schedule对[IR-SDE](https://github.com/Algolzw/image-restoration-sde)进行改进。

 
## 目录

- [上手指南](#上手指南)
  - [环境配置](#环境配置)
  - [文件目录说明](#文件目录说明)
  - [数据集下载](#数据集下载)
  - [参数配置](#参数配置)
  - [模型训练](#模型训练)
  - [模型测试](#模型测试)
  - [模型下载](#模型下载)

## 上手指南

### 环境配置

1. cuda: 9.1
2. python 3.7
3. pytorch 1.7

### 文件目录说明

```
IR-SDE
│  README.md
│  
├─codes
│  ├─config
│  │  └─denoising-sde
│  │      │  inference.py
│  │      │  options.py
│  │      │  test.py
│  │      │  test.sh #测试脚本
│  │      │  train.py
│  │      │  train.sh #训练脚本
│  │      │  
│  │      ├─models
│  │      │  │  base_model.py
│  │      │  │  denoising_model.py
│  │      │  │  lr_scheduler.py
│  │      │  │  networks.py
│  │      │  │  optimizer.py
│  │      │  │  __init__.py
│  │      │  │  
│  │      │  └─modules
│  │      │          DenoisingNAFNet_arch.py
│  │      │          DenoisingUNet_arch.py
│  │      │          loss.py
│  │      │          module_util.py
│  │      │          __init__.py
│  │      │          
│  │      └─options
│  │          ├─test
│  │          │      ir-sde.yml #测试配置
│  │          │      
│  │          └─train
│  │                  ir-sde.yml #训练配置
│  │                  
│  ├─data
│  │      BokehLQGT_dataset.py
│  │      BokehLQ_dataset.py
│  │      data_sampler.py
│  │      GT_dataset.py
│  │      LQGT_dataset.py
│  │      LQ_dataset.py
│  │      StereoLQGT_dataset.py
│  │      StereoLQ_dataset.py
│  │      util.py
│  │      __init__.py
│  │      
│  └─utils
│          deg_utils.py
│          file_utils.py
│          img_utils.py
│          sde_utils.py
│          __init__.py
│          
├─dataset #数据集
├─experiments #模型保存
└─results #实验结果


```
### 数据集下载
训练集由DIV2K、Flickr2K、BSD500以及Waterloo Explore四个数据集中采集的高质量图像进行整合得到（图像放到同一文件夹下即可）,训练完成的模型在McMaster、Kodak24以及CBSD68三个数据集上进行测试,这7个数据集可从[SWinIR](https://github.com/JingyunLiang/SwinIR#training)下载。
### 参数配置
 - 训练参数可在./codes/config/denoising-sde/options/train/ir-sde.yml进行修改。

 - 测试参数可在./codes/config/denoising-sde/options/test/ir-sde.yml进行修改。

 - sde训练和测试的参数（如schedule）应保持一致。
### 模型训练

直接运行train.sh脚本即可开始训练，学习率、gpu以及训练集等配置在[参数配置](#参数配置)中修改。

训练脚本
 - 多卡并行训练

```
python -m torch.distributed.launch --nproc_per_node=2 --master_port 66666  train.py -opt './options/train/ir-sde.yml' --launcher pytorch
```
 - 单卡训练
```
python train.py -opt './options/train/ir-sde.yml'
```
### 模型测试
直接运行test.sh脚本即可开始测试，测试集等配置在[参数配置](#参数配置)中修改。

测试脚本
```
python test.py -opt './options/test/ir-sde.yml'
```
### 模型下载
训练好的模型可通过[谷歌云盘](https://drive.google.com/drive/folders/1ly96E24_w-2C5z6BxSSVgNyh7QUNK5sG?usp=sharing)下载。
