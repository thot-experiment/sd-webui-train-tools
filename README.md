# sd-webui-train-tools

The stable diffusion webui training aid extension helps you quickly and visually train models such as Lora.

一个 stable-diffusion-webui 的训练辅助扩展，可以帮助你快速、直观地训练 Lora 等模型。

English (TODO)

## 预览

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/home.jpg?raw=true">

## 安装

在 stable-diffusion-webui 的 Extensions 页面中安装：

在 URL for extension's git repository 中填入: https://github.com/liasece/sd-webui-train-tools

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/sd-webui-install-this-extensions.png?raw=true">

安装完成后，重启 stable-diffusion-webui。可以看到多一个标签页 Train Tools ：

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/tab_name.png?raw=true">

## 创建工程和版本

由于一个 Lora 的训练可能会经过很多过程，会不断地调整训练参数，所以要有管理的概念。

### 工程

工程名字就是你的 Lora 的名字，通常是一个主题，或者一个画风，或者一个人物。

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/create_project.png?raw=true">

1. 如果你觉得你的数据落后了，或者你刚刷新了网页但是没有重启 stable-diffusion-webui ，你应该点击刷新按钮确保你页面上的数据是最新的。

2. 点击创建工程按钮，输入工程名字，点击确定。

### 版本

版本是工程的一个子集，你可以在一个工程中创建多个版本，每个版本都有自己的训练参数。

创建版本步骤和创建工程类似。

## 训练数据准备

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/created_project_version.png?raw=true">

1. 该区域为系统接受到的训练数据，和你上传的文件可能会有区别，因为训练的数据会经过处理。

2. 该区域是你上传训练数据并且设置处理参数的区域。

每个每个工程的每个版本的训练数据都是独立的，你可以在一个工程中创建多个版本，每个版本都可以使用不同的训练数据。

你可以一次性选择多张图片上传：

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/upload_dataset.png?raw=true">

数据上传完成之后，需要进行一些处理。这里有一些处理的参数，你可以根据自己的需要进行调整。默认参数已经可以满足一般情况。

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/config_dataset_and_apply.png?raw=true">

你上传的数据源文件会被保留，但是不会真正用于训练。真正被用到训练中的是左边展示的数据。

## 训练

准备好训练数据，确认待训练数据窗口中的数据是你想要的之后，就可以开始训练了。

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/after_upload_dataset.png?raw=true">

1. 这个区域显示了真正会用于训练的数据。

2. 这个区域是训练的参数设置区域。

这里有一些训练的参数，你可以根据自己的需要进行调整。默认参数已经可以满足一般情况。Train base model 很重要，一个好的基础模型很大程度影响你的训练效果。

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/begin_train.png?raw=true">

1. 训练配置区域。

2. 预览参数配置区域。因为训练结束后可以自动预览训练结果，所以这里有一些预览的参数可以一并配置。参考 [预览训练结果](#预览训练结果) 。

3. 训练完成后自动运行预览图生成。

4. 开始训练。

第一次训练时，会去下载一些模型，你可以在命令行中看到下载进度。

<img width="512" alt="" src="https://github.com/liasece/sd-webui-train-tools/blob/main/doc/training.png?raw=true">

在 stable-diffusion-webui 的运行命令行中可以看到训练的过程及进度。

## 预览训练结果

不同的训练数据/训练参数/训练次数都会导致训练的效果不一样。你可以在这里预览训练结果。方便地挑选较好的结果。

预览域也有一些参数，这些参数和 txt2img 中的含义基本一致。

关键词中会自动添加每个训练检查点的 lora:xx:xx ，你不用手动添加。

你在这里输入的其他 Lora 将无效，因为这会污染你的判断。

这里还有一些类似于 txt2img 中 xyz plot 的功能，默认值已经可以满足一般情况。这里的部分值是可以多选的，值之间用 "," 分隔。

## 保存训练结果

目前没有在 UI 中提供下载模型的功能，你可以去你 stable-diffusion-webui > output > train_tools > 工程名 > versions > 版本名 > checkpoints 中找到你训练好的模型。

## 本工具使用问题

### 为什么我点上传数据集后没有反应？

上传数据集后，如果你的一些预处理参数需要下载额外模型，那么网页上会有一段时间没有反应，这是正常的。你可以在命令行中看到进度。

### 为什么我点开始训练后没有反应？

训练时间是很长的，这个过程可能会导致网页没响应，你可以在命令行中看到进度。

### 为什么我点预览训练结果后没有反应？

预览生成图片的过程可能会导致网页没响应，你可以在命令行中看到进度。或者如果预览信息太大图片太多导致网页失去相应的话，你需要刷新 UI 或者重启 stable-diffusion-webui。

### 我网页上的数据好像不是最新的？

你可以点击工程或者版本后面的刷新按钮，这会从服务器重新拉取页面数据。包括图片。刷新网页可能不会解决问题，需要点击工程或者版本后面的刷新按钮。

## 训练问题

### 为什么我上传的训练数据有一部分被丢弃了？

检查图片格式，可能是图片格式不支持。目前支持 .png .jpg .jpeg .bmp .webp

### 为什么我训练的人物图片，生成的图片都是一些奇怪的东西？

1. 提高你的训练图片质量。检查你的训练数据，可能是你的训练数据中有一些奇怪的东西。比如你的训练数据中有一些奇怪的图片，或者你的训练数据中有一些奇怪的文字。

2. 如果是训练图片中的对象，而不是画风，在处理数据时勾选 "Use BLIP for caption" 或者 "Use deepbooru for caption"。进阶：想要取得好的效果，你要对这个处理后得到的提示文本进行修剪，默认情况下，这个文本会生成到 `outputs\train_tools\projects\[project]\versions\[version]\dataset\processed\[dataset]\[image name].txt` ，你可以手动修改这个文件，将当中你想保留的特征*去除*（⚠️ 是在这些文本中去除你想保留的特征。如果你想为你的 Lora 保留关键字，那就在这个文本中留下这个关键字），然后重新训练。(这种功能应该集成在工具中，待开发)

3. 判断是不是训练次数不足，提高训练配置中的 "Number of epochs"。

4. 提高训练配置中的 "Batch size"。这对显存容量的要求很高。24G 显存的显卡可以最高选到 10 左右。

### 为什么我的训练很慢？

训练过程需要的时间大致等于：

(n \* [Number of epochs]) / ([Batch size] \* i)

其中：

n: 训练数据集图片数量 "Train number of repetitions" （-1 时表示训练图片数为（上传图片数\*4））。大多数情况下你不需要修改默认值，你可以改成你上传的图片数量的 k 倍

i: 你的显卡性能

所以，如果想要提高训练速度，你可以：

1. 提高 "Batch size"。这对显存容量的要求很高。24G 显存的显卡可以最高选到 10 左右。

2. 降低 "Number of epochs"。这会导致训练效果变差。

3. 降低 "Train number of repetitions"。这会导致训练效果变差。

4. 买个算力更高的显卡。
