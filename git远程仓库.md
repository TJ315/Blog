[TOC]



##1、 Git是什么？

Git是目前世界上最先进的分布式版本控制系统。



##2、 Git指令



###2.1  查看文件状态

 查看文件状态 ,可以查看哪些文件在本次修改了，以便我们清楚在下一步应该提交哪些文件 

```
git status 
```



###2.2 文件提交到暂存区

```
git add <filePath>   此命令是将file文件提交到暂存区，此命令是单个文件提交
 
git add . 			他会监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。

git add -u 			他仅监控已经被add的文件（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）

git add -A 			是上面两个功能的合集（git add --all的缩写）

```



###2.3 文件提交到版本库

```
git commit -m "提交的描述信息"  			从暂存区提交到版本库

git commit -a -m "提交的描述信息" 			从工作区直接提交到版本库，跳过git add

```



###2.4 文件推送到远程主机

```
git push <远程主机名> <本地分支名>:<远程分支名>

```

**示例**
```
 git push origin master
 
 git push git@github.com:TJ315/playback.git master
```
上面命令表示，将本地的master分支推送到origin主机的master分支。如果master不存在，则会被新建。如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。



**其它示例**

1.推送本地分支`lbranch-1`到新大远程分支`rbranch-1`：

```
$ git push origin lbranch-1:refs/rbranch-1

```

2.推送`lbranch-2`到已有的`rbranch-1`，用于补充`rbranch-1`：

```
$ git checkout lbranch-2
$ git rebase rbranch-1
$ git push origin lbranch-2:refs/rbranch-1

```

3.用本地分支`lbranch-3`覆盖远程分支`rbranch-1`：

```
$ git push -f origin lbranch-2:refs/rbranch-1

```

或者 -

```
$ git push origin :refs/rbranch-1   //删除远程的rbranch-1分支
$ git push origin lbranch-1:refs/rbranch-1

```

###2.5 分支合并

git pull命令用于从另一个存储库或本地分支获取并集成(整合)。git pull命令的作用是：取回远程主机某个分支的更新，再与本地的指定分支合并，它的完整格式稍稍有点复杂。

```
$ git pull <远程主机名> <远程分支名>:<本地分支名>

```
比如，要取回origin主机的next分支，与本地的master分支合并，需要写成下面这样 
```
 $ git pull origin next:master
```
如果远程分支(next)要与当前分支合并，则冒号后面的部分可以省略。上面命令可以简写为：
```
$ git pull origin next
```
上面命令表示，取回origin/next分支，再与当前分支合并。实质上，这等同于先做git fetch，再执行git merge。

```
$ git fetch origin
$ git merge origin/next
```


### 2.6 存储库克隆 

命令将存储库克隆到新目录中。 
```
$ git clone <版本库的网址>
```
