---
title: Hexo quick start
description: hexo intro quick start
date: 2023-04-15 20:43:00
author: lanceWu
language: zh-CN
categories:
  - [hexo, quick start]
tags:
  - hexo
  - quick start
---

# Hexo 快速启动

![backgroundImage](https://github.com/Nulllance/PicturePlace/blob/main/hexo/1892.jpeg?raw=true)

### 介绍

​ [Hexo](https://hexo.io/zh-cn/) 是一个快速生成个人博客网页的模板工具生成器，通过对 Hexo 的简单使用，我们可以将 [markdown](https://www.markdownguide.org/getting-started/#how-does-it-work) 格式的文件生成博客网页。和其他的生成工具不同，例如：[sphinx](https://www.sphinx-doc.org/en/master/)， Hexo 生态更为完善，结构设计更为合理，支持多语言的学习，官网内容更容易看懂。为了能暂时跳过教程，快速生成网页（其实看官网只需要花 3 小时，但是有很多功能暂时不需要用到），接下来，我将通过更加直观详细而非官方的教学步骤进行记录。让初学者都能快速建立自己的第一个博客网页。如果需要深入学习可以结合我的教程看官方文件。

### 超快配置

​ Hexo 通过命令可以超快生成一个默认的博客框架，在安装好 [nodejs]() 和 [git](https://git-scm.com/) 工具后，你可以直接通过下面指令快速生成。

​ [nodejs 安装教程](../Software_Setting/node_installation.md) [ git 安装教程]()

​ window： win 键+r 键打开对话框， 输入 cmd，回车，依次输入以下命令。mac 打开终端，同理。

```bash
# 利用npm 工具安装 hexo-cli 工具，该工具也叫 hexo 手脚架，是快速开发的工具。
npm install hexo-cli -g
# 初始新建一个 blog 名字的文件夹并将模板文件放入
hexo init blog
# 进入 blog 文件中
cd blog
# 安装相应依赖包
npm install
# 启动服务，点击链接即可看到模板 blog
hexo server
```

​ 以上命令就可以初步生成一个模板 blog ，接着我们只需要对一些文件进行配置就可以生成我们想要的博客。

​ 以下图片展示一些实际操作和效果图

---

#### 命令效果图

![image-20230414112715652](https://github.com/Nulllance/PicturePlace/blob/main/hexo/image-20230414112715652.png?raw=true)

#### 生成页面

![image-20230414112809611](https://github.com/Nulllance/PicturePlace/blob/main/hexo/image-20230414112809611.png?raw=true)

#### 文件目录结构

![image-20230414122759794](https://github.com/Nulllance/PicturePlace/blob/main/hexo/image-20230414122759794.png?raw=true)

---

​ 接下来就要客制化我们想要的网页，请看[下一章](configuration.md)
