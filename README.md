# Stable-Diffusion_Learning-Record

## 简介
[**Stable-Diffusion**](https://github.com/CompVis/stable-diffusion)简称(SD)，Stable Diffusion是一个文本到图像的潜在扩散模型，由[CompVis](https://github.com/CompVis)、[Stability AI](https://github.com/Stability-AI)等研究人员和工程师创建。其使用来自LAION-5B数据库子集的512x512图像进行训练。本次学习中，主要参考B站的一个Up主，[Nenly同学](https://space.bilibili.com/1814756990)的视频，感谢这位大佬的教学。

## 配置要求
对于Stable-Diffusion这个模型，跑动它需要有一定的配置，下面配置表是参考[Nenly同学](https://space.bilibili.com/1814756990)的课程
|                    | **最低配置**               | **推荐配置**                     |
| ------------------ | ------------------------------ | -------------------------------- |
| **操作系统**       | 无硬性要求                | Windows 10 64 位                |
| **CPU**                | 无硬性要求                | 支持64位的多核处理器    |
| **显卡**             | GTX 1660Ti及同等性能显卡 | RTX 3060Ti及同等性能显卡  |
| **显存**             | 6GB                            | 8GB                              |
| **内存**             | 8GB                            | 16GB                             |
| **硬盘空间**       | 20G可用                      | 100~150G可用                   |
| **生图时间及其分辨率** | 1~2分钟一张，可绘制512\*512像素 | 10~30秒一张，可绘制1024\*1024像素 |

## 安装教程
由于本人连最低配的电脑都没有，所以并未尝试安装过。

## 提示词(prompts)

### 什么是prompts
提示词分为两种，一种为prompts(正向提示词)，一种为Negative prompts(反向提示词)，顾名思义，prompts的词是让模型更趋向于它，而Negative prompts则是使模型尽量不出现改内容。

### prompts的格式
在Stable-Diffusion中，prompts最好是英文
