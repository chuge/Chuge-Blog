title: hexo 使用问题
date: 2016-02-22 11:15:23
tags:
---

### 执行hexo d，报如下错误

The file will have its original line endings in your working directory.
Permission denied (publickey).
fatal: Could not read from remote repository.

	eval `ssh-agent -s`

把自定义名字的私有key加入ssh

	ssh-add ~/.ssh/github_rsa

测试

	ssh -T git@github.com