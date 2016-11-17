#### 指定远程仓库：

直接修改.git/config文件
~~~~
[remote "origin"]
        url = https://github.com/huang-qing/github-huangqing.github.io.git
        fetch = +refs/heads/*:refs/remotes/origin/*
~~~~

修改命令 
~~~~
git remte origin set-url https://github.com/huang-qing/github-huangqing.github.io.git
~~~~

删除后重新添加
~~~~
git remote rm origin 
git remote add origin https://github.com/huang-qing/github-huangqing.github.io.git
~~~~




#### 指定分支节点：.git/config
~~~~
[branch "master"]
	remote = origin
	merge = refs/heads/master
~~~~

#### fatal: refusing to merge unrelated histories

~~~~
git pull origin master --allow-unrelated-histories
~~~~