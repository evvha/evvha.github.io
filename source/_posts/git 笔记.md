---
title: Git笔记
date: 2019-09-18 01:51:30
updated: 2019-09-23 21:02:03
categories: 
- web前端
tags:
- git
- bash
---
## 常用指令
命令|注解
:---|:---
ssh-keygen -t rsa -C "邮箱地址"|生成SSH证书
cat ~/.ssh/id_rsa.pub|查看SSH证书
gitk|启动图形化界面
git remote add 远程仓库名 远程仓库地址|添加远程仓库地址
git remote rm 远程仓库名|删除远程仓库
git remote set-url 远程仓库名 远程仓库地址	|修改远程仓库地址
git checkout 文件名|还原文件到上一个版本

## bash常见命令

```bash
pwd (Print Working Directory) 查看当前目录
cd (Change Directory) 切换目录
ls (List)查看当前目录下的内容
mkdir (Make Directory)创建目录
touch 创建文件,如 touch index.html
cat 查看全部文件内容,如 cat index.html
rm (remove) 删除文件,删除空文件夹,如 rm index.html , rm Blog
rm -rf 强制删除文件夹,非空文件夹也可以删除
rmdir (Remove Directory) 删除文件夹,只能删除空文件夹
mv (move) 移动文件或重命名,如 mv index.html ./demo/index.html
cp (copy) 复制文件,如 cp index.html ./demo/index.html
head 查看文件前几行,如 head -5 index.html
history 查看操作历史
whoami 查看当前用户
```
## 资料文件
- [如何优雅地使用 Git - 掘金](https://juejin.im/post/5a54386af265da3e3b7a6317)
- [优雅的提交你的 Git Commit Message - 掘金](https://juejin.im/post/5afc5242f265da0b7f44bee4)
- [如何使用 GitHub？ - 知乎](https://www.zhihu.com/question/20070065/answer/79557687)
- [Git飞行规则 - GitHub](https://github.com/k88hudson/git-flight-rules/blob/master/README_zh-CN.md)
- [Git的奇技淫巧 - Github](https://github.com/521xueweihan/git-tips)
- [猴子都能懂的GIT入门 - 贝格乐（Backlog）](https://backlog.com/git-tutorial/cn/)
- [10 分钟学会Linux常用 bash命令 - Savorboard - 博客园](https://www.cnblogs.com/savorboard/p/bash-guide.html)
## Git Gui
- [Sourcetree](https://www.sourcetreeapp.com/)
- [TortoiseGit](https://tortoisegit.org/)
## 参考文献
- [史上最浅显易懂的Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)
- [Pro Git v2 - Scott Chacon](https://git-scm.com/book/zh/v2)
- [玩转Git三剑客 - 极客时间](https://time.geekbang.org/course/intro/100021601)
