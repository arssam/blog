---
title: git 拉取远程tag，并给该tag打补丁
date: 2018-09-26 15:57:46
tags: 'git'
---

## 1. 获取tag版本
```
  git tag
```
## 2. 切换某一tag版本
```
  git checkout tagName
```
## 3. 切出补丁分支
```
  git checkout newBranch -b
```
## 4. 修改具体内容并提交到具体分支