# Git学习笔记

## Git的工作区和版本库

> 工作区就是我们写代码的地方 说白了 也就是我们 git init 的地方
>
> 版本库就是**Git**帮忙管理版本的区域了
>
> 其中 版本库分为两个部分
>
> - 暂存区(stage/index)
>
>   > 说白了 git add <files> 就是把文件暂时存储在这里的
>
> - 分支(由HEAD指针指向)
>
>   > 说白了就是 git commit 把暂存区的修改提交到的地方
>   >
>   > 这个地方也是我们本地的最终版本库

<p align="center">
  <img src="https://raw.githubusercontent.com/SsageParuders/HQ_Notes/master/img/202109171820182.png" />
</p>

## 增添文件到暂存区

```shell
git add <files> # 可以是单个文件 也可以是某个文件夹
```

## 提交暂存区到本地分支

```shell
git commit -m "xxx" # 提交暂存区全部的修改到本地分支 "xxx"是对这个版本的说明注释
```

## 查看Git状态

```shell
git status # 查看状态
```

## 查看Git历史版本

```shell
git log # 查看git分支的历史版本
git log --pretty=oneline # 查看git分支的历史版本的简洁模式 -- 单行显示
```

## 查看Git命令记录

```shell
git reflog # 查看历史git命令
```

## Git回退版本

```shell
git reset -- hard (HEAD) # HEAD可以省略不写 此时将暂存区的内容重新覆盖入工作区 
#如工作区没有内容 则相当于rm -rf 拿空内容替工作区
git reset -- hard HEAD^ # 回退一个版本 回退两个版本就是两个^^ 三个版本就是^^^ 以此类推
git reset -- hard <commit id> # 回退指定版本 需要填写对应版本的 commit id
#
# commit id 可以通过 git log 查看 
# 每个分支版本对应的 id 都是不一样的 是一个 SHA1 计算出来的独特数字 
# 在填写这个 id 的时候 不需要输入全部的值 只需要输入 4+ 位 git 会去自动识别版本 直到输入的精确度能准确识别唯一版本
#
```

## Git查看修改内容

```shell
git diff # 查看工作去和暂存区的文件差异
# 工作区和暂存区有差异的的地方 git diff 会显示出来
# 但是 git diff 不显示工作区与分支的区别差异
```

## Git本地库关联远程库

```shell
git remote add origin https://github.com/SsageParuders/HQ_Python_Study.git 
# 关联本地的版本库同步远程GitHub仓库
# git remote 是命令
# origin 是远程库的名字 一般情况下默认为 origin 方便理解 也可以自行定义其他个性化远程库名 随意
# 后面的URL是由 GitHub 提供的仓库地址 在关联时 切记换为个人的仓库地址
# 地址有 http 协议的 也有 ssh 协议的 http 较慢于 ssh 实际使用中 看情况决定两种协议
```

## 本地库推送至远程库

```shell
git push -u origin master # 推送本地的 master 分支到 名为 origin 的远程库上去
# 如果 分支不是 master 而是自定义的名称 请对应修改指令  origin远程库名也是同理
# -u 参数是第一次推送的时候才需要设置的 目的是为了 将本地的 master 分支和远程的 master 分支关联起来
git push origin master
# 后续的推送都省略 -u 参数
```

## 删除远程库

```shell
# 此删除远程库 只是取消本地库和远程库的关联 但是实际上远程库依然在云端 需要去云端手动删除
git remote rm <name> # <name> 就是远程库名
```

## 查看远程库信息

```shell
git remote -v
# 返回实例:
# origin  https://github.com/SsageParuders/HQ_Python_Study.git (fetch)
# origin  https://github.com/SsageParuders/HQ_Python_Study.git (push)
```







