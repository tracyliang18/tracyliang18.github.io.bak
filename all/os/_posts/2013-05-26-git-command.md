---
layout: post
title: git-command
---

<p>
git 版本控制命令

1. git checkout -b iss53

      等价与两条命令：git branch iss53 //先创建分支        

                   git checkout iss53 

2. git commit -a -m '修改的说明'

      等价于两条命令：git add ***.***  //

                   git commit -m '修改的说明'

3. git branch //显示有哪些分支

4. git checkout master //切换到master分支

5. git merge **** //合并分支

6. git status //显示信息

7. git fetch origin //同步远程服务器上的数据到本地

8. git push origin serverfix //将serverfix的分支上传到origin中，格式：git push （远程仓库名） （分支名）

9. git push origin serverfix:serferfix //上传我本地的 serverfix 分支到远程仓库中去，仍旧称它为 serverfix 分支

10. git push origin serverfix:awesomebranch //你可以把本地分支推送到某个命名不同的远程分支，可以把远程分支称之为 awesomebranch

11.上传code的步骤：

            （1） git clone jessica@githost:simplegit.git

            （2） git commit -a -m ‘变化的信息’

            （3） git push origin master

                 当push出错时：

                 git fetch origin //更新资源

                 git merge origin/master //合并分支

                 git push master

12.本地的分支是master，服务器的分支名是origin/master

13.git log //显示提交历史

      等价与gitk

14.git diff 13432 23hu //比较两次提交的不同 

      其中图形化安装方法：
      （1）下载P4Merge：

                           http://www.perforce.com/perforce/downloads/component.html

                      
      （2） 在/usr/local/bin/目录下新建一个extMerge的脚本：

                               $ sudo vim /usr/local/bin/extMerge

                           在脚本中输入以下内容：

                               #!/bin/sh

                               /home/amlogic/p4v-2011.1.428988/bin/p4merge $*

                       (3) 在/usr/local/bin/目录下新建一个extDiff的脚本：

                              $ sudo vim /usr/local/bin/extDiff 

                           脚本输入以下内容：

                              #!/bin/sh

                              [ $# -eq 7 ] && /usr/local/bin/extMerge "$2" "$5"

                       （4）确认这两个脚本是可执行的：

                              $ sudo chmod +x /usr/local/bin/extMerge 

                              $ sudo chmod +x /usr/local/bin/extDiff

                       （5）现在来配置使用你自定义的比较和合并工具吧。这需要许多自定义设置：merge.tool通知 Git 使用哪个合并工具；mergetool.*.cmd规定命令运行的方式；       

                           mergetool.trustExitCode 会通知 Git 程序的退出是否指示合并操作成功；diff.external通知 Git 用什么命令做比较。因此，你能运行以下4条配置命令：

                             $ git config --global merge.tool extMerge

                             $ git config --global mergetool.extMerge.cmd \

                               'extMerge "$BASE" "$LOCAL" "$REMOTE" "$MERGED"'

                             $ git config --global mergetool.trustExitCode false

                             $ git config --global diff.external extDiff

                           或者直接编辑~/.gitconfig文件如下：

                             [merge]

                                  tool = extMerge

                             [mergetool "extMerge"]

                              cmd = extMerge "$BASE" "$LOCAL" "$REMOTE" "$MERGED"

                              trustExitCode = false

                             [diff]

                                  external = extDiff

                        （6） 设置完毕后，运行diff命令：

                             $ git diff 32d1776b1^ 32d1776b1
</p>
