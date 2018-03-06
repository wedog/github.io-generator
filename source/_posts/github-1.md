---
title: 如何将github上fork的开源项目的更改合入自己的项目
tags: github、fork
categories: github
date: 2018-03-06 17:20:57
---

**如何将github上fork的开源项目的更改合入自己的项目（解决遇到冲突的情况**

例如他人开源项目：https://github.com/quasarframework/quasar.git;本人fork后的项目：https://github.com/wedog/quasar.git</p>

**在自己的项目中执行：**

1. 新建本地分支：`git checkout -b quasarframework-dev dev`
1. pull他人的分支代码：`git pull https://github.com/quasarframework/quasar.git dev`

**解决冲突（如果有）**

1. 切换到dev分支：`git checkout dev`
1. 合入quasarframework-dev的代码到dev分支：`git merge --no-ff quasarframework-dev`
1. 提交dev分支到远程分支：`git push origin dev`