#### 指定远程仓库：.git/config

~~~~
[remote "origin"]
        url = https://github.com/huang-qing/github-huangqing.github.io.git
        fetch = +refs/heads/*:refs/remotes/origin/*
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