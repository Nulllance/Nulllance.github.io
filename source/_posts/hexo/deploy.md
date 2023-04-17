---
title: Deploy
author: LanceWu
date: 2023-04-15 20:43:00
categories:
  - [hexo, deploy]
tags:
  - hexo
  - deploy
---

# Deploy (部署)

![imageDeploy](https://github.com/Nulllance/PicturePlace/blob/main/hexo/image.png?raw=true)

> 部署是将网站发布到服务器上的过程，这里使用的是 [Github Pages](https://pages.github.com/) 作为服务器。

[官方文档](https://hexo.io/docs/github-pages)有详细介绍，这里不再赘述，只是补充一下官方文档中没有提到的一些问题。

如果你之前没有在 github 上面部署过项目，那么下面是一些你需要注意的点。

## github 上传文件

推荐先在 GitHub 上面创建一个仓库，然后将仓库克隆到本地，然后在文件夹中将 hexo 生成的所有文件放入其中，然后将文件夹上传到 GitHub 上面。

```bash
$ git add .
$ git commit -m "first commit"
$ git push
```

## github pages.yml

pages.yml 文件是用来配置 github pages 的，简单来说这个是用来自动化部署的，当你在本地修改了文件，然后 push 到 github 上面，github pages 会自动帮你部署到服务器上面。

在本地相关路径（具体路径见下文）创建一个 pages.yml 文件，然后将下面的代码复制到 pages.yml 文件中。

```yaml
.github/workflows/pages.yml
name: Pages

on:
  push:
    branches:
      - main  # default branch

jobs:
  pages:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v3
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          # If your repository depends on submodule, please see: https://github.com/actions/checkout
          submodules: recursive
      - name: Use Node.js 16.x
        uses: actions/setup-node@v2
        with:
          node-version: '16'
      - name: Cache NPM dependencies
        uses: actions/cache@v2
        with:
          path: node_modules
          key: ${{ runner.OS }}-npm-cache
          restore-keys: |
            ${{ runner.OS }}-npm-cache
      - name: Install Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

> **Attention!** 创建后，应该再次 add , commit, push 一下，这样 github pages 才会自动帮你部署到服务器上面。
