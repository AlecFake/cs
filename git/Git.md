# Git

## Git Commit

Git 仓库中的提交记录保存的是目录下所有文件的快照，就像是把整个目录复制，然后再粘贴一样，但是更加优雅。



Git希望提交记录尽可能**轻量**，因此每次提交时，不会盲目复制整个目录，而是将当前版本与上一个版本进行对比，并且将所有差异打包到一起作为一个提交记录。



Git保存了提交记录的历史，可以**快速**的在不同的提交记录之间进行切换。



`git commit -m <description>`



## Git Branch

Git 的分支简单指向某个提交记录，因此也很轻量。



分支相当于：基于这个提交以及其所有的父提交进行新的工作。



> 早建分支！多用分支！



为什么呢？

* 分支不会造成存储或者内存上的开销。
* 按照逻辑分解工作到不同的分支比维护那些特别臃肿的分支简单多了。



`git branch <branch>`

## Git Checkout

`git chekcout <branch>`： 切换分支到branch

`git checkout -b <branch>`:  创建并切换到branch分支



## Git Merge





## Appendix

[1] : [Learn Git Branching](https://learngitbranching.js.org/)