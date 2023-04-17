---
title: autocrlf
date: 2020-05-26 16:00:00
tags: [git]
categories: [git]
---

# autocrlf

![autocrlfImg](https://github.com/Nulllance/PicturePlace/blob/main/git/autocrlfImg.png?raw=true)

## 0.0 前言

如果不想懂原理，直接按照下面的步骤操作即可。

- windows 系统下，git config --global core.autocrlf true
- linux/Mac 系统下，git config --global core.autocrlf input

## 1. 什么是回车与换行

在了解这个参数含义之前我们需要了解什么是回车和换行。

### 1.1 由来

在计算机还没有出现之前，有一种叫做电传打字机（Teletype Model 33）的机械打字机，每秒钟可以打 10 个字符。但是它有一个问题，就是打完一行换行的时候，要用去 0.2 秒，正好可以打两个字符。要是在这 0.2 秒里面，又有新的字符传过来，那么这个字符将丢失。

于是，研制人员想了个办法解决这个问题，就是在每行后面加两个表示结束的字符。一个叫做“回车”，告诉打字机把打印头定位在左边界，不卷动滚筒；另一个叫做“换行”，告诉打字机把滚筒卷一格，不改变水平位置。

这就是“换行”和“回车”的由来。

### 1.2 使用

后来，计算机发明了，这两个概念也就被般到了计算机上。那时，存储器很贵，一些科学家认为在每行结尾加两个字符太浪费了，加一个就可以。于是，就出现了分歧。

回车 \r 本义是光标重新回到本行开头，r 的英文 return，控制字符可以写成 CR，即 Carriage Return

换行 \n 本义是光标往下一行（不一定到下一行行首），n 的英文 newline，控制字符可以写成 LF，即 Line Feed

符号 ASCII 码 意义

\n 10 换行 NL

\r 13 回车 CR

在不同的操作系统这几个字符表现不同，比如在 WIN 系统下，这两个字符就是表现的本义，在 UNIX 类系统，换行\n 就表现为光标下一行并回到行首，在 MAC 上，\r 就表现为回到本行开头并往下一行，至于 ENTER 键的定义是与操作系统有关的。通常用的 Enter 是两个加起来。

不同操作系统下的含义：

\n: UNIX 系统行末结束符

\r\n: window 系统行末结束符

\r: MAC OS 系统行末结束符

我们经常遇到的一个问题就是，Unix/Mac 系统下的文件在 Windows 里打开的话，所有文字会变成一行；而 Windows 里的文件在 Unix/Mac 下打开的话，在每行的结尾可能会多出一个^M 符号。

### 1.3 软回车和硬回车

再扩展一下回车的一些知识。

硬回车就是普通我们按回车产生的，它在换行的同时也起着段落分隔的作用。

软回车是用 Shift + Enter 产生的，它换行，但是并不换段，即前后两段文字在 Word 中属于同一“段”。在应用格式时你会体会到这一点。

软回车能使前后两行的行间距大幅度缩小，因为它不是段落标记，要和法定的段落标记——硬回车区别出来。硬回车的 html 代码是<p>..</p>，段落的内容就夹在里面，而软回车的代码很精悍：<br>。网页的文字如果复制到 word 中，则硬回车变为弯曲的箭头，软回车变为向下的箭头。

## 2. 什么是 autocrlf

假如你正在和其他人合作，他们在 Windows 上编程，而你却在其他系统上，在这些情况下，你可能会遇到行尾结束符问题。这是因为 Windows 使用回车和换行两个字符来结束一行，而 Mac 和 Linux 只使用换行一个字符。虽然这是小问题，但它会极大地扰乱跨平台协作。

Git 可以在你提交时自动地把行结束符 CRLF 转换成 LF，而在签出代码时把 LF 转换成 CRLF。用 core.autocrlf 来打开此项功能，如果是在 Windows 系统上，把它设置成 true，这样当签出代码时，LF 会被转换成 CRLF：

```bash

git config --global core.autocrlf true

```

表示要求 git 在提交时将 crlf 转换为 lf，而在检出时将 crlf 转换为 lf。

Linux 或 Mac 系统使用 LF 作为行结束符，因此你不想 Git 在签出文件时进行自动的转换；当一个以 CRLF 为行结束符的文件不小心被引入时你肯定想进行修正，把 core.autocrlf 设置成 input 来告诉 Git 在提交时把 CRLF 转换成 LF，签出时不转换：

```bash
$ git config --global core.autocrlf input
```

表示在提交时将 crlf 转换为 lf，而检出时不转换 。
这样会在 Windows 系统上的签出文件中保留 CRLF，会在 Mac 和 Linux 系统上，包括仓库中保留 LF。

如果你是 Windows 程序员，且正在开发仅运行在 Windows 上的项目，可以设置 false 取消此功能，把回车符记录在库中：

```bash
$ git config --global core.autocrlf false
```

表示在提交时不转换，检出时也不转换。

## 3. CRLF 、CR 和 LF 详解

- CR：Carriage Return，对应 ASCII 中转义字符\r，表示回车
- LF：Linefeed，对应 ASCII 中转义字符\n，表示换行
- CRLF：Carriage Return & Linefeed，\r\n，表示回车并换行

其中，CRLF 是 Windows 系统中的换行符，LF 是 Unix/Linux/Mac OS X 系统中的换行符，CR 是 Macintosh 系统中的换行符。
