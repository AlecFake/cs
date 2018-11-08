# Git

## 基础篇

### 1.Git Commit

------



命令：`git commit -m <description>`



Git 仓库中的提交记录保存的是目录下所有文件的快照，就像是把整个目录复制，然后再粘贴一样，但是更加优雅。



Git希望提交记录尽可能**轻量**，因此每次提交时，不会盲目复制整个目录，而是将当前版本与上一个版本进行对比，并且将所有差异打包到一起作为一个提交记录。因此每个提交都有一个父节点。



Git保存了提交记录的历史，可以**快速**的在不同的提交记录之间进行切换。

示例：

![](https://github.com/guokaide/cs/blob/master/git/gitcommit1.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitcommit2.PNG)


### 2.Git Branch

------

命令：`git branch <branch>`



Git 的分支简单指向某个提交记录，因此也很轻量。



分支相当于：基于这个提交以及其所有的父提交进行新的工作。



> 早建分支！多用分支！



为什么呢？

* 分支不会造成存储或者内存上的开销。
* 按照逻辑分解工作到不同的分支比维护那些特别臃肿的分支简单多了。

示例：

![](https://github.com/guokaide/cs/blob/master/git/gitbranch1.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitbranch2.PNG)


### 3.Git Checkout

------

命令：

`git chekcout <branch>`： 切换分支到branch

`git checkout -b <branch>`:  创建并切换到branch分支

示例：

![](https://github.com/guokaide/cs/blob/master/git/gitcheckout.PNG)


### 4.Git Merge

------



分支与合并：新建一个分支，在分支上开发某个功能，开发完成后再合并回主线。



第一种合并方法：`Git Merge`



在Git中合并2个分支时会产生1个特殊的 提交记录， 它有2个父节点。即将2个父节点本身以及它们所有祖先都包含进来。

示例：

![](https://github.com/guokaide/cs/blob/master/git/gitmerge1.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitmerge2.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitmerge3.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitmerge4.PNG)

练习：

如图，从C1出发到C4。

![](https://github.com/guokaide/cs/blob/master/git/gitmerge.PNG)

```java
git branch bugFix
git checkout bugFix
git commit -m "C2"
git checkout master
git commit -m "C3"
git merge bugFix
```



### 5.Git Rebase

------

第二种合并方法：`Git Rebase`



Rebase 实质上是取出一系列的提交记录，“复制”它们，然后在另外一个地方逐个放下去。



Rebase 的优势就是可以创造更加线性的提交历史。

示例：

![](https://github.com/guokaide/cs/blob/master/git/gitrebase1.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitrebase2.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitrebase3.PNG)

![](https://github.com/guokaide/cs/blob/master/git/gitrebase4.PNG)


练习：
如图，从C1出发到C2'。

![](https://github.com/guokaide/cs/blob/master/git/gitrebase.PNG)

```java
git checkout -b bugFix
git commit -m "C2"
git checkout master
git commit -m "C3"
git checkout bugFix
git rebase master   // 将bugFix合并到master
```



## 高级篇

### 1. 分离HEAD

------

**HEAD**: 总是指向当前分支上最近一次提交记录。通常情况下，指向分支名（如bugFix）。在提交时，改变了bugFix的状态，这一变化通过HEAD变得可见。



**分离的HEAD**:让其指向了某个具体的提交记录而不是分支名。即从分支中分离出HEAD.



示例：



练习：从bugFix分支分离出HEAD

```java
git checkout C4（fed2da64c0efc5293610bdd892f82a58e8cbc5d8）  // C4其实是提交记录哈希值
git checkout fed2 // Git可以识别唯一标识提交记录的前几个字符
```



### 2. 相对引用

------

**相对引用**：

* `^` ：向上移动1个提交记录
* `~<num>`: 向上移动多个提交记录，如`~3`

**强制修改分支位置**：

使用`-f`选项让分支指向另一个提交。例如：`git branch -f master HEAD~3`。这个命令将master 分支强制指向HEAD的第3级父提交。



示例1：`^`



练习1：

```java
git checkout bugFix^
```



示例2：`~<num>`



练习2：

```java
git checkout HEAD^
git branch -f bugFix HEAD^
git branch -f master C6
```



### 3. 撤销变更

------

**撤销变更**：由底层部分（暂存区的独立文件或者片段）和上层部分（变更到底是通过哪种方式撤销）组成。



**两种方法**：`git reset`  和 `git revert`



示例1：



示例2：



练习：

```java
git reset local^
git checkout pushed
git revert pushed
```









## Appendix

[1] : [Learn Git Branching](https://learngitbranching.js.org/)
