<div align="center">
  <img width="600" src="media/logo.png" alt="awesome-vit">
  <br>
  <img src=https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg>
</div>


--------------------------------------------------------------------------------

 [English](README.md) | 简体中文



Vision Transformer 论文精选列表和总结。

你可以使用思维导图软件打开 [思维导图源文件](media/Vision-Transformer_zh-CN.xmind)，如果你只想浏览图片，则可以下载 [思维导图高清图](media/Vision-Transformer_zh-CN.png)



## 目录

<!-- toc -->

- [总结](#总结)
  - [图像分类](#图像分类)
    - [Attention-based](#Attention-based)
      - [训练策略](#训练策略)
      - [模型改进](#模型改进)
        - [Token 化模块](#Token-化模块)
        - [位置编码模块](#位置编码模块)
        - [注意力模块](#注意力模块)
        - [FFN 模块](#FFN-模块)
        - [Normalization 模块位置](#Normalization-模块位置)
        - [分类预测模块](#分类预测模块)
        - [其他](#其他)
    - [MLP-based](#MLP-based)
    - [ConvMixer-based](#ConvMixer-based)
    - [通用架构分析](#通用架构分析)
    - [其他](#其他)
  - [目标检测](#目标检测)
  - [语义分割](#语义分割)

- [论文列表](#论文列表)
  - [Transformer 原论文](#Transformer-原论文)
  - [ViT 原论文](#ViT-原论文)
  - [图像分类](#图像分类)
    - [2020](#2020)
    - [2021](#2021)
    - [2022](#2022)
  - [目标检测](#目标检测)
  - [语义分割](#语义分割)

<!-- tocstop -->



## 总结

每个类别中仅列出典型算法



### 图像分类

中文博客链接

- [Vision Transformer 必读系列之图像分类综述(一)：概述](https://zhuanlan.zhihu.com/p/459828118)
- [Vision Transformer 必读系列之图像分类综述(二): Attention-based](https://zhuanlan.zhihu.com/p/461700507)
- [Vision Transformer 必读系列之图像分类综述(三): MLP、ConvMixer 和架构分析](https://zhuanlan.zhihu.com/p/462463183)


#### Attention-based

![image](https://user-images.githubusercontent.com/17425982/150126580-11f75810-e4da-4c38-a0fd-ee6a8c7a0a18.png)

##### 训练策略

- [**DeiT**] Training data-efficient image transformers & distillation through attention (ICML 2021-2020.12) [[Paper](https://arxiv.org/abs/2012.12877)]
- [**Token Labeling**] All Tokens Matter: Token Labeling for Training Better Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.10858)]



##### 模型改进



###### Token 化模块

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150126295-2aa4055a-b9b6-465e-89ba-5fde441d5f29.png)

Image to Token 包括：

- **非重叠 Patch Embedding**
  
  -  [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**TNT**] Transformer in Transformer (NeurIPS 2021-2021.3) [[Paper](https://arxiv.org/abs/2103.00112)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  
- **重叠 Patch Embedding**

  - [**T2T-ViT**] Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet (2021.1) [[Paper](https://arxiv.org/abs/2101.11986)]

  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]

  - [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]

  - [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]

  - [**PS-ViT**] Vision Transformer with Progressive Sampling (2021.8) [[Paper](https://arxiv.org/abs/2108.01684)]

    

Token to Token 包括：

- **固定采样窗口 Token 化**
  -  [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
- **动态采样 Token 化**
  - [**PS-ViT**] Vision Transformer with Progressive Sampling (2021.8) [[Paper](https://arxiv.org/abs/2108.01684)]
  - [**TokenLearner**] TokenLearner: What Can 8 Learned Tokens Do for Images and Videos? (2021.6) [[Paper](https://arxiv.org/abs/2106.11297)]



###### 位置编码模块

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150076359-5259dc0c-ef37-4a33-8139-63553aa85c09.png)

显式位置编码包括：

- 绝对位置编码
  - [**Transformer**] Attention is All You Need] (NIPS 2017-2017.06) [[Paper](https://arxiv.org/abs/1706.03762)]
  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]
- 相对位置编码
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]



隐式位置编码包括：

- [**CPVT**] Conditional Positional Encodings for Vision Transformers (2021.2) [[Paper](https://arxiv.org/abs/2102.10882)]
- [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]
- [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]
- [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]



###### 注意力模块

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150076656-db44a11a-a98f-479c-86c3-23119083923e.png)

仅包括全局注意力包括：

- 标准多头注意力模块

  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]

- 减少全局注意力计算量

  - [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]

  - [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]
  - [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]
  - [**P2T**] P2T: Pyramid Pooling Transformer for Scene Understanding (2021.6) [[Paper](https://arxiv.org/abs/2106.12011v3)]
  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]
  - [**MViT**] Multiscale Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.11227)]
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]

- 广义线性注意力

  - [**T2T-ViT**] Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet (2021.1) [[Paper](https://arxiv.org/abs/2101.11986)]



引入额外局部注意力包括：

- 局部窗口计算模式
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]
  - [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]
  - [**GG-Transformer**] Glance-and-Gaze Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.02277)]
  - [**Shuffle Transformer**] Shuffle Transformer: Rethinking Spatial Shuffle for Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.03650)]
  - [**MSG-Transformer**] MSG-Transformer: Exchanging Local Spatial Information by Manipulating Messenger Tokens (2021.5) [[Paper](https://arxiv.org/abs/2105.15168)]
  - [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]



- 引入卷积局部归纳偏置
  - [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]
  - [**ELSA**] ELSA: Enhanced Local Self-Attention for Vision Transformer (2021.12) [[Paper](https://arxiv.org/abs/2112.12786)]
- 稀疏注意力
  - [**Sparse Transformer**] Sparse Transformer: Concentrated Attention Through Explicit Selection [[Paper](https://openreview.net/pdf?id=Hye87grYDH)]



###### FFN 模块

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150076776-30b210c3-d71d-4e97-bf24-7f19554ec2e6.png)

通过 Conv 局部信息提取能力，提升性能包括：

- [**LocalViT**] LocalViT: Bringing Locality to Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.05707)]
- [**CeiT**] Incorporating Convolution Designs into Visual Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.11816)]



###### Normalization 模块位置

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150076857-39e23911-81c2-4796-9da7-1c77722de622.png)

- Pre Normalization
  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]

- Post Normalization
  - [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]



###### 分类预测模块

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150076961-049f5031-f5ad-4cb6-aac9-091cc3316c78.png)

- Class Tokens
  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**CeiT**] Incorporating Convolution Designs into Visual Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.11816)]

- Avgerage Pooling
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**CPVT**] Conditional Positional Encodings for Vision Transformers (2021.2) [[Paper](https://arxiv.org/abs/2102.10882)]
  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]



###### 其他

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150126405-cacdf828-669b-4cb1-894c-894f21b31873.png)

**(1) 如何输出多尺度特征图**

- Patch Merging
  - [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]
  - [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]
  - [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]
  - [**MetaFormer**] MetaFormer is Actually What You Need for Vision (2021.11) [[Paper](https://arxiv.org/abs/2111.11418)]

-  Pooling Attention 
  - [**MViT**] Multiscale Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.11227)][**Imporved MViT**] 
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]

- 空洞卷积
  - [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]



**(2) 如何训练更深的 Transformer**

- [**Cait**] Going deeper with Image Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.17239)]
- [**DeepViT**] DeepViT: Towards Deeper Vision Transformer (2021.3) [[Paper](https://arxiv.org/abs/2103.11886)]



#### MLP-based

![image](https://user-images.githubusercontent.com/17425982/150077191-a40b77a4-8397-4bc1-ba17-15e3b5588439.png)

- [**MLP-Mixer**] MLP-Mixer: An all-MLP Architecture for Vision (2021.5) [[Paper](https://arxiv.org/abs/2105.01601)]

- [**ResMLP**] ResMLP: Feedforward networks for image classification with data-efficient training (CVPR2021-2021.5) [[Paper](https://arxiv.org/abs/2105.03404)]

- [**gMLP**] Pay Attention to MLPs (2021.5) [[Paper](https://arxiv.org/abs/2105.08050)]

- [**CycleMLP**] CycleMLP: A MLP-like Architecture for Dense Prediction (2021.7) [[Paper](https://arxiv.org/abs/2107.10224)]

  

#### ConvMixer-based

- [**ConvMixer**] Patches Are All You Need [[Paper](https://openreview.net/pdf?id=TVHS5Y4dNvM)]

  

#### 通用架构分析

![image](https://user-images.githubusercontent.com/17425982/150077586-bd3e18f6-2360-4586-892a-f1756984356b.png)

- Demystifying Local Vision Transformer: Sparse Connectivity, Weight Sharing, and Dynamic Weight (2021.6) [[Paper](https://arxiv.org/abs/2106.04263)]
- A Battle of Network Structures: An Empirical Study of CNN, Transformer, and MLP (2021.8) [[Paper](https://arxiv.org/abs/2108.13002)]
- [**MetaFormer**] MetaFormer is Actually What You Need for Vision (2021.11) [[Paper](https://arxiv.org/abs/2111.11418)]
- [**ConvNeXt**] A ConvNet for the 2020s (2022.01) [[Paper](https://arxiv.org/abs/2201.03545)]



#### 其他



### 目标检测



### 语义分割

**[⬆ 回到顶部](#目录)**



## 论文列表



### Transformer 原论文

- [**Transformer**] Attention is All You Need] (NIPS 2017-2017.06) [[Paper](https://arxiv.org/abs/1706.03762)]



### ViT 原论文

- [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]



### 图像分类



#### 2020

- [**DeiT**] Training data-efficient image transformers & distillation through attention (ICML 2021-2020.12) [[Paper](https://arxiv.org/abs/2012.12877)]
- [Sparse Transformer] Sparse Transformer: Concentrated Attention Through Explicit Selection [[Paper](https://openreview.net/pdf?id=Hye87grYDH)]



#### 2021

- [T2T-ViT] Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet (2021.1) [[Paper](https://arxiv.org/abs/2101.11986)]
- [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]
- [**CPVT**] Conditional Positional Encodings for Vision Transformers (2021.2) [[Paper](https://arxiv.org/abs/2102.10882)]

- [TNT] Transformer in Transformer (NeurIPS 2021-2021.3) [[Paper](https://arxiv.org/abs/2103.00112)]
- [**Cait**] Going deeper with Image Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.17239)]
- [**DeepViT**] DeepViT: Towards Deeper Vision Transformer (2021.3) [[Paper](https://arxiv.org/abs/2103.11886)]

- [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
- [CeiT] Incorporating Convolution Designs into Visual Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.11816)]
- [LocalViT] LocalViT: Bringing Locality to Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.05707)]
- [**MViT**] Multiscale Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.11227)]
- [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]

- [**Token Labeling**] All Tokens Matter: Token Labeling for Training Better Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.10858)]
- [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]
- [**MLP-Mixer**] MLP-Mixer: An all-MLP Architecture for Vision (2021.5) [[Paper](https://arxiv.org/abs/2105.01601)]
- [**ResMLP**] ResMLP: Feedforward networks for image classification with data-efficient training (CVPR2021-2021.5) [[Paper](https://arxiv.org/abs/2105.03404)]
- [gMLP] Pay Attention to MLPs (2021.5) [[Paper](https://arxiv.org/abs/2105.08050)]
- [MSG-Transformer] MSG-Transformer: Exchanging Local Spatial Information by Manipulating Messenger Tokens (2021.5) [[Paper](https://arxiv.org/abs/2105.15168)]
- [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]
- [TokenLearner] TokenLearner: What Can 8 Learned Tokens Do for Images and Videos? (2021.6) [[Paper](https://arxiv.org/abs/2106.11297)]
- **Demystifying Local Vision Transformer: Sparse Connectivity, Weight Sharing, and Dynamic Weight (2021.6)** [[Paper](https://arxiv.org/abs/2106.04263)]
- [P2T] P2T: Pyramid Pooling Transformer for Scene Understanding (2021.6) [[Paper](https://arxiv.org/abs/2106.12011v3)]
- [GG-Transformer] Glance-and-Gaze Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.02277)]
- [Shuffle Transformer] Shuffle Transformer: Rethinking Spatial Shuffle for Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.03650)]
- [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]
- [**CycleMLP**] CycleMLP: A MLP-like Architecture for Dense Prediction (2021.7) [[Paper](https://arxiv.org/abs/2107.10224)]
- [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]
- [**PS-ViT**] Vision Transformer with Progressive Sampling (2021.8) [[Paper](https://arxiv.org/abs/2108.01684)]
- **A Battle of Network Structures: An Empirical Study of CNN, Transformer, and MLP (2021.8)** [[Paper](https://arxiv.org/abs/2108.13002)]
- [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]
- [**MetaFormer**] MetaFormer is Actually What You Need for Vision (2021.11) [[Paper](https://arxiv.org/abs/2111.11418)]
- [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]
- [**ELSA**] ELSA: Enhanced Local Self-Attention for Vision Transformer (2021.12) [[Paper](https://arxiv.org/abs/2112.12786)]
- [**ConvMixer**] Patches Are All You Need [[Paper](https://openreview.net/pdf?id=TVHS5Y4dNvM)]



#### 2022

- [**ConvNeXt**] A ConvNet for the 2020s (2022.01) [[Paper](https://arxiv.org/abs/2201.03545)]



### 目标检测



### 语义分割

**[⬆ 回到顶部](#目录)**



后续会持续更新，欢迎提 PR！



