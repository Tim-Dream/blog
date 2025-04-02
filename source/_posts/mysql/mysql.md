---
title: Github上部署Hexo
date: 2024-11-26 13:06:06
index_img: /img/hexo.png
categories:
- Hexo
tags:
- 服务器部署
---

### 前期准备

- 安装node.js
- 安装Hexo
  
```shell
  npm install -g hexo-cli
```

### 新建项目

- 在GitHub上新建一个项目，项目名称为`xxx`，并同步项目到本地
- 移动项目中的`.git`文件夹，以及`README.md`文件到其他地方
- 在文件夹下执行
  
```shell
hexo init
```

- 将`.git`文件夹，以及`README.md`文件移动回当前目录
- 新建`.github\workflows\pages.yml`文件
  
```yml
name: Pages

on:
  push:
    branches:
      - main # default branch

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          # If your repository depends on submodule, please see: https://github.com/actions/checkout
          submodules: recursive
      - name: Use Node.js 20
        uses: actions/setup-node@v4
        with:
          # Examples: 20, 18.19, >=16.20.2, lts/Iron, lts/Hydrogen, *, latest, current, node
          # Ref: https://github.com/actions/setup-node#supported-version-syntax
          node-version: "20"
      - name: Cache NPM dependencies
        uses: actions/cache@v4
        with:
          path: node_modules
          key: ${{ runner.OS }}-npm-cache
          restore-keys: |
            ${{ runner.OS }}-npm-cache
      - name: Install Dependencies
        run: npm install
      - name: Build
        run: npm run build
      - name: Upload Pages artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public
  deploy:
    needs: build
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4

  ```
- 修改`_config.yml`文件中的,`url: https://你的GitHub名称.github.io/你的项目名称/`
	- 就是把URL改成部署后的访问路径，可以等部署成功后再改（不改会导致项目无法加载css和js）
- 同步文件到GitHub

### 部署项目到GitHub

- 在GitHub项目下，选择`Settings`，选择`Pages`
- 在`Source`下面选择`GitHub Actions`并保存
- 等几分钟就可以访问你的blog网站了

