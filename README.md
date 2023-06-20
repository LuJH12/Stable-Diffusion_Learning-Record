# Stable-Diffusion_Learning-Record

## 简介
[**Stable-Diffusion**](https://github.com/CompVis/stable-diffusion)简称(SD)，Stable Diffusion是一个文本到图像的潜在扩散模型，由[CompVis](https://github.com/CompVis)、[Stability AI](https://github.com/Stability-AI)等研究人员和工程师创建。其使用来自LAION-5B数据库子集的512x512图像进行训练。本次学习笔记中，主要参考B站的一个Up主，[Nenly同学](https://space.bilibili.com/1814756990)的视频，感谢这位大佬的教学。

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

## 参数介绍

### Prompts(提示词)

#### 什么是Prompts
提示词分为两种，一种为prompts(正向提示词)，一种为Negative prompts(反向提示词)，顾名思义，prompts的词是让模型更趋向于它，而Negative prompts则是使模型尽量不出现改内容。

#### Prompts的格式
在Stable-Diffusion中，prompts的书写最后保持这几个原则，这会让模型更容易读懂你想要什么。
- prompts最好是英文
- 每个prompts尽量是一个个词组，而非一段话
- 在描述整幅图不同的地方时，分段写，如描写人物特征一段，场景一段，天气一段等。(一般分这几段进行编写：主体+细节+标签+参数)
- 尽量也书写Negative prompts

#### Prompts的权重
一般来说，越靠前的prompts的权重越高。但也可以通过下面的方法来改变prompts的权重。
| **形式**    | **demo**               | **描述**                                                      |
| --------- | ------------------ | ------------------------------------------------------------ |
| **括号+数字** | (white flower:1.5) | 提高white flower这个提示词的权重为原来的1.5倍 |
| **套括号** | (((white flower))) | 增强，一层在原来基础上1.1倍，这里则增强1.1\*1.1\*1.1=1.331倍 |
| **套括号** | {{{white flower}}} | 增强，一层在原来基础上1.05倍，这里则增强1.15倍 |
| **套括号** | \[\[\[white flower\]\]\] | 削弱，一层在原来基础上0.9倍，这里则是削弱0.729倍 |

### Step
这个参数一般设置为20，因为超过20后，效果提升不大，没必要浪费算力，当然太小了，也会导致生成一些奇奇怪怪的图。

### Seed(随机种子)
随机种子，默认为-1(这代表每次画图都是具有随机性的)。这个参数可以用在，当你画出了一张较为满意的图，但需要进行微调一部分时可以用到。比如我画了一张图，它的随机种子为2584684，而我可以保持这个随机种子不变，并加上一些需要修改的prompts，这样就对该图进行微调了。

## 文生图
这个比较简单，一般就是按格式输入prompts和Negative prompts，选择合适的参数，即可生成自己想要的图片。当然，一般来说，prompts越多，描述的越详细，生成的图片就会越符合。
以下是例子：

![image](https://github.com/LuJH12/Stable-Diffusion_Learning-Record/blob/main/Picture/00044-1503880058-SFW%2C%201girl%2C%20walking%2C%20forest%2C%20path%2C%20sun%2C%20sunshine%2C%20shining%20on%20body%2C%201dog%2C_blue%20skirt%20and%20white%20t-shirt%2C%20blonde%20hair%2C%20short%20hair%2C.png)

**Prompts**
SFW, 1girl, walking, forest, path, sun, sunshine, shining on body,
blue skirt and white t-shirt, blonde hair, short hair,
trees, bush, ((white flower)), path, outdoor,
(masterpiece:1,2), best quality, masterpiece, highres, original, extremely detailed wallpaper, perfect lighting,(extremely detailed CG:1.2), drawing, paintbrush,

**Negative Prompts**
Negative prompt: NSFW, (worst quality:2), (low quality:2), (normal quality:2), lowres, normal quality, ((grayscale)), skin spots, acnes, skin blemishes, age spot, (ugly:1.331), (duplicate:1.331), (morbid:1.21), (mutilated:1.21), (tranny:1.331), mutated hands, (poorly drawn hands:1.5), blurry, (bad anatomy:1.21), (bad proportions:1.331), extra limbs, (disfigured:1.331), (missing arms:1.331), (extra legs:1.331), (fused fingers:1.61051), (too many fingers:1.61051), (unclear eyes:1.331), lowers, bad hands, missing fingers, extra digit,bad hands, missing fingers, (((extra arms and legs))),

其他参数暂时没找到，找到后更新

第二张是生成了一只可爱小狗，但是还是存在很多问题，生成得不够好（技术不过关，而非Stable-Diffusion的问题）。

![image](https://github.com/LuJH12/Stable-Diffusion_Learning-Record/blob/main/Picture/00049-3688003120-SFW%2C%20(((1smalldog_1.5)))%2C%20%20running%2C%20forest%2C%20path%2C%20sun%2C%20face%20forward%2C%20_happy%2C%20cute%2C%20white%2C%20Tugou%2C%20samll%2C%20%20spot%20color%2C%20_trees%2C%20bus.png)

**Prompts**
SFW, (((1smalldog:1.5))), running, forest, path, sun, face forward,
happy, cute, white, Tugou, samll, spot color,
trees, bush, (((white flower))), path, outdoor,
(masterpiece:1,2), best quality, masterpiece, highres, original, extremely detailed wallpaper, perfect lighting,(extremely detailed CG:1.2), drawing, paintbrush,

**Negative Prompts**
Negative prompt: Negative prompt: NSFW, (worst quality:2), (low quality:2), (normal quality:2), lowres, normal quality, ((grayscale)), acnes, skin blemishes, age spot, (ugly:1.331), (duplicate:1.331), (morbid:1.21), (mutilated:1.21), (tranny:1.331), mutated hands, (poorly drawn hands:1.5), blurry, (bad anatomy:1.21), (bad proportions:1.331), extra limbs, (disfigured:1.331), (missing arms:1.331), (extra legs:1.331), (fused fingers:1.61051), (too many fingers:1.61051), (unclear eyes:1.331), lowers, bad hands, missing fingers, extra digit,bad hands, missing fingers, (((extra arms and legs))),

**Other parameter**
Steps: 25, Sampler: DPM++ 2M Karras, CFG scale: 8, Seed: 3688003120, Size: 512x512, Model hash: 038ba203d8, Model: AbyssOrangeMix2_sfw, Clip skip: 2, ENSD: 31337
Saved: 00049-3688003120-SFW, (((1smalldog_1.5))), running, forest, path, sun, face forward, _happy, cute, white, Tugou, samll, spot color, _trees, bus.png

## 图生图
图生图的话，要学习比较多的，目前只是简单试了下，效果如下：

![image](https://github.com/LuJH12/Stable-Diffusion_Learning-Record/blob/main/Picture/img2img_test.png)

由于使用的是我朋友的原图，这里就打码了:stuck_out_tongue_winking_eye:，在图生图的过程中，如果你生成了一张较为满意的图片，你就可以固定`随机种子`的数值保持不变，然后通过修改提示词等方式对图片进行调整。调整的方法有很多，如：修改提示词，放大修复(图片变清晰)，局部重绘等。

## 放大修复
放大修复主要有三种，分别为：文生图-高清修复，图生图-SD放大，生成后处理-附加功能。下面将分别介绍这几种功能。

**1. 文生图-高清修复(打回重画，再来一幅)**
- 分两步处理图像，先生成一个低分辨率版本，再根据它与指定的放大算法，再生成一个高分辨率版本，从而在不更改图的情况下丰富细节。(特点：效果较好，但多次生成，费算力，且电脑配置较差的话，仍然不能生成分辨率较大的图片)
- `Denoising`一般0.3~0.5，网友推荐的放大算法：`R-ESRGAN 4X+，R-ESRGAN Anime6B(二次元)`。

**2. 图生图-SD放大(分几块画，拼在一起)**
- 根据指定的放大倍数，将图生图的图像拆分成若干小块按固定的逻辑进行重绘，再拼成一张大图，可以实现在低显存下绘制大尺寸图片。(特点：效果也较好，但是多图拼接可能会出现问题-->需要合适的Tile overlap)
- 一般来说，`Tile overlap`(图像重叠的像素)越大效果越好(但是对算力有要求)，假设你设置的`Tile overlap = 64`，则图片分辨率也要增加`64`。

**3. 生成后处理-附加功能(简单放大，随时可用)**
- 利用各种放大算法，在图像生成后对其进行单独的放大处理，使之拥有更高的分辨率尺寸(特点：方便简单，但效果不太好)

## 局部重绘
待更新。。。

## 模型介绍

**1. AbyssOrangeMix**
- 各方面均衡，对新手较友好(有专门的VAE)

