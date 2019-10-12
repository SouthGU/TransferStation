# Git教程

## 一、环境搭建

```
git init
git add readme.md
git commit -m "备注"
git commit -am "备注" (同步执行)
```



## 二、仓库状态

```
git status
git diff readme.md (查看修改的具体内容)
```



## 三、版本回退

```
git log -pretty=oneline
git reset --hard HEAD^ (返回上一个快照)
cat readme.md
git reset --hard 362816XXX
git relog (查看历史命令，以便确定返回到哪个版本)
```



## 四、工作区和暂存区

```
git checkout -- readme.md (丢弃工作区的修改)
git reset HEAD readme.md (由暂存区返回到工作区)
```

![图片对比](.\img\1.jpg)



## 五、删除文件

```
rm readme.md (将本机的文件删除，会导致工作区和版本库不一致：删除版本库文件 或者 恢复文件)
git rm readme.md (将版本库的文件删除，多了git命令)
git checkout -- readme.md (删错本机文件，将暂存区的文件恢复至最新版本)
```



## 六、远程仓库

```
Github创建远程仓库
git remote add origin https://giuhub.com/SouthGU/SSH.git (关联)
git push -u origin master (推送到远程仓库)
git clone https://github.com/SouthGU/CloneTest.git (克隆)
```



## 七、分支管理

````
git branch
````

<img src=".\img\2.png" style="zoom: 150%;" />



```
git checkout -b dev (创建并切换，相当于 git branch dev 和git checkout dev)
```

<img src=".\img\3.png" style="zoom:150%;" />



```
vi readme.md (修改)
git commit -am "dev分支上修改内容"
git checkout master (切换回master，但还未合并，所以readme.md显示的是master原本的内容)
```

<img src=".\img\4.png" style="zoom:150%;" />



````
git merge dev (在master上合并merge分支)
````

<img src=".\img\5.png" style="zoom:150%;" />



```
git branch -d dev (删除dev分支)
git branch (删除后重新查看只剩下master)
```

<img src="./img/5.png" style="zoom:150%;" />



## 八、解决冲突

```
git checkout -b feature (创建新分支，修改readme.md文件后重新提交)
git checkout master (切换回master分支修改文件后提交)
git merge feature (在master上试图合并，显示冲突)
git status (显示冲突文件，必须手动修改后重新提交)
git log --graph --pretty=oneline --abbrev-commit (查看历史分支)
```



## 九、Feature分支

```
git checkout -b feature-vulcan (开发代号为vulcan的新功能)
git branch -d feature-vulcan (功能弃用-->删除失败)
git branch -D feature-vulcan (强行删除成功)
```



## 十、多人协作

```
git remote -v (查看远程仓库的信息)
git push origin master (把该主分支上的所有本地信息提交到远程仓库)
git push orgin dev (推送其他分支)

git clone git@github.com:SouthGU/SSH.git (小伙伴克隆你的远程仓库代码，但只有master分支)
git checkout -b dev origin/dev (若想要分支上开发，需创建远程origin的dev分支到本地)
git commit -m "小伙伴的dev分支提交代码" (这时候小伙伴上传了代码，导致远程仓库代码与 本人dev分支代码不同)

git commit -m "本人dev分支提交上传" (显示冲突，Github提示需要下载并修改代码)
git pull origin dev --allow-unrelated-histories (不能直接下载，需要指定本地dev分支与远程origin/dev分支的链接)
git branch --set-upstream-to=origin/dev dev (设置链接)
git pull (下载最新代码，显示冲突后手动解决即可)
```

