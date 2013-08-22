gitTutorials
============

git简明操作

```
总则：多使用分支操作，体会git强大的分支功能。
1.在创建代码仓库的时候，默认会创建一个master分支，这个分支做为一个稳定分支，只合并稳定的代码。
2.另外创建一个dev分支，这个分支做为日常的开发测试使用，dev分支测试稳家后，方合并到master分支去。
3.如果需要开发计划外的功能时，可基于当前的开发分支，创建一个feature分支，完成后如果需要则合并到dev分支，如无需再使用则可删除。
4.如果遇到bug需要紧急修复，则可基于master分支创建fixed分支，修复完成测试通过，则合并到master分支，删除fixed分支。
```

## 本地操作
* 初始化：git init
* 添加所有修改文件到git仓库：git add .
* 添加某单个文件到git仓库：git add 文件件
* 确认修改内容：git commit -m "修改内容叙述"

## 与服务器相连
* 克隆一个仓库：git clone 远端地址
* 查看连接的远端地址：git remote -v
* 连接到远端服务器：git remote add origin 远端地址
* 与远端服务器断开连接：git remote rm origin
* 将远端代码合并到本地：git pull origin master
* 将本地代码上传到远端服务器：git push origin master

## 分支与合并
* 查看分支：git branch -a
* 基于当前分支创建分支并切换到新的分支：git checkout -b 分支名
* 当前在master分支，将dev分支合并到master：git merge dev
* 删除本地分支：git branch -d 分支名
* 删除远端分支：1.git push origin --delete 分支名  2.git push origin :分支名 //用空分支覆盖远端分支方式 
* 克隆远端某个分支：git checkout --track -b foobar origin/foobar
* 提交本地的test分支到远端的master分支：git push origin test:master
* 提交本地的test分支作为远端的test分支：git push origin test:test

## 查看状态
* 查看当前哪些文件更改了而没有添加到仓库跟踪：git status
* 查看历史提交记录：git log

## 版本回溯
**为了安全起见，最好基于所在分支创建一个分支，回到历史版本，找到需要的代码，然后再删除该分支。**

1. 在当前分支新建分支：git checkout -b 分支名
2. 查看历史提交记录，找到提交记录id：git log
3. 回到需要的历史版本：git checkout commitId
4. 找到需要的代码，复制出来，切换回原分支，删除该分支
