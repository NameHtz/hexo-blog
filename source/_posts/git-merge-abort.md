---
title: 如何撤消有冲突的git merge
tags: git
date: 2020-09-23 10:33:15
---

[How to undo a git merge with conflicts](https://stackoverflow.com/questions/5741407/how-to-undo-a-git-merge-with-conflicts)

最新的Git:
```shell script
git merge --abort
```
将会把当前工作空间重置到合并之前的状态，这意味着，如果有未提交的代码，将会丢失

1.7.4：
```shell script
git reset --merge
```
功能和<b class="bgc-e4e6e8">git merge --abort</b>相同

1.6.2之前：

```shell script
git reset --hard
```
删除所有未提交的更改，包括未提交的合并