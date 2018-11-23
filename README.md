# git_branch_test
Git分支演练

## Git的基本操作

```javascript
1、从远程仓库克隆到本地
    git clone 远程仓库地址

2、更改本地代码之后提交相关操作
    git status 查看本地仓库的状态

    git add . 把更改的添加到暂存区

    git commit -m "注释" 提交到本地仓库

3、把本地的代码推送到服务器
    git push origin master -u xxx
```

## 有关分支

1. 当我们创建一个远程仓库的时候，就会默认有一个主分支【创建仓库就会自带的】
2. 我们把远程仓库，克隆到本地之后，本地也有一个master分支【通过git branch查看】
3. 主分支【master】主要用于我们主线代码的开发
4. 新建分支的目的是为了，保证我们主分支继续执行的情况下，做一些其它的事情【比如bug修复或是难题攻克】


## Git分支操作
```javascript
1、查看本地有哪些分支
    git branch
    
2、切出一个新分支
	git checkout -b v1.0_bugfix_branch
    
3、把新分支推动远程仓库，做一个备份
	git push origin v1.0_bugfix_branch
    
4、切回主分支，并且把 v1.0_bugfix_branch 已经修复的代码合并会主分支
	git checkout master
    git merge v1.0_bugfix_branch
    
    做完这一步，本地的master已经拥有修改之后的代码
    
5、把本地的master的代码推送远程仓库的master
	git push origin master

```

