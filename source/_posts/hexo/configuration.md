---
title: Configuration
date: 2023-04-15 15:07:00
categories:
  - [hexo, configuration]
tag:
  - hexo
  - configuration
---

# 配置（客制化）Customize

![配置的图片](https://github.com/Nulllance/PicturePlace/blob/main/hexo/5941.jpeg?raw=true)

​ 配置一些文件，将文件放置在合适的地方，加上几个命令即可完成对网站的建立。

## 前置知识

​ 在配置之前需要对 [markdown](https://www.markdownguide.org/getting-started/#how-does-it-work) 格式和 [yaml](https://yaml.org/spec/1.2.2/#chapter-2-language-overview) 格式有所了解，这两个都相对容易，就不多介绍。

### \*.md 文件的一点小改动(Front-matter)

​ 在每个 md 文章的最上面应该添加以下的代码：

```yaml
---
# 该文件的标题
title: Configuration
# 这篇文章的作者
author: lanceWu
# 分类类别
categories:
	- hexo
# 标签
tag:
	- hexo
---
```

`如果文章有公式，需要下载 hexo-filter-mathjax 插件，并引用它`

[hexo-filter-mathjax github 地址](https://github.com/next-theme/hexo-filter-mathjax)

```bash
$ npm install hexo-filter-mathjax
$ hexo clean
```

#### Usage

```yaml
---
mathjax: true
---
```

### \_config.yml 修改

​ 文件里面大多数都看得懂，可以先不修改，具体内容看[官方文档](https://hexo.io/docs/configuration)

## 文件设置

​ 将 md 文章放在 source/\_post 文件夹里面

#### 生成 Generate

```bash
$ hexo generate
```

#### 提供服务 Server

```bash
$ hexo server
```

​ 到这里文档就可以基本生成了。

## Theme

​ 骚骚的主题是程序员的最爱，特别是拗不过女朋友的强烈要求要改个好看的主题的时候，就得修改一下主题，主题的修改也是很简单的，但是要注意的是主题要找到最新的版本。

#### 搜索主题

在[github](https://github.com/)搜索 hexo-theme，也可在[官网主题](https://hexo.io/themes/)，但是特别注意，官网主题里面的某些主题文档里面的操作步骤可能过时，不能成功布置，最好是在官网上面预览，然后在 GitHub 中搜索

<img src="https://github.com/Nulllance/PicturePlace/blob/main/hexo/image-20230415120505750.png?raw=true" alt="image-20230415120505750" style="zoom: 33%;" />

#### 下载主题

在 github 下载后，将压缩包放置 themes 文件夹下面，然后解压缩，改名，一般去掉 Hexo-theme-即可,这个名字修改成什么都无所谓，重要的是\_config.yml 文件要一样。

安装必要的插件

**BTY**，此外，也可通过 npm 下载。但是下载完主题是在 node_modules 文件夹下的，

#### 主题修改位置

主题配置文件的修改，可以在主路径下的\_config.landscape.yml 修改，如果你的主题是 fluid，那就是 \_config.fluid.yml 下面修改，如果没有这个文件就自己创建一个。

#### 进阶，修改主题的样式

如果你对主题的布局或者样式有自己的想法，那就得把主题文献下载到 themes 文件夹下面自行更改里面的代码。

#### 修改 \_config.yml

```
# 找到这个theme，默认是landscape主题，改为和themes文件夹下相同名字的主题
theme: landscape

```

至此，重新 执行 hexo g 和 hexo s 命令，刷新页面即可
