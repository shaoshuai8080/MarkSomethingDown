

# git clone 时直接 rename

```shell
git clone git@github.com:moooofly/aaa.git bbb
```


----------



# 基于本地项目创建 github repo

```shell
cd /path/to/project/dir/
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:moooofly/your_project_name.git
(git pull origin master)
git push -u origin master
```

> 注1：在执行 `git remote add xxx` 前，需要先在 github 上创建一个名为 your_project_name 的 repo ；
> 
> 注2：上面用小括号括起来的命令的使用场景为：若在 github 上新建 repo 的时候，顺带创建了 README 或 .gitignore 或 LICENSE 等文件时，则需要先将上述文件拉取到本地；
> 
> 注3：上面的 git@github.com:moooofly/rabbitmq-server-3.6.1.git 可以换成 https://github.com/moooofly/rabbitmq-server-3.6.1.git ，还可以使用 https://github.com/moooofly/rabbitmq-server-3.6.1


# 本地新建分支后 push 到 github repo


创建并切换分支

```shell
git checkout -b new_branch
```
此时分支信息仅在本地存在；

执行下面的命令后，就可以将新建的本地 new_branch 分支中的内容 push 到 github 上对应的 new_branch 分支中，并建立跟踪关系；

```shell
git push -u
```

之后就可以在 github 页面中看到对应分支内容了；

下面命令的适用场景为：github 上已经存在 new_branch ，本地想要建立跟踪信息；

```shell
git branch --set-upstream-to=origin/new_branch new_branch
```


# fork 别人项目后如何同步其后续更新

先从自己的 github 中 clone 一份内容
```shell
git clone git@github.com:moooofly/sre.git
```

此时只有名为 origin 的 remote
```shell
git remote -v
```

新增名为 eleme_sre 的 remote ，即当前 repo 的始祖；
```shell
git remote add eleme_sre https://github.com/eleme/sre.git
```

再次查看时，已经增加了名为 eleme_sre 的 remote ；
```shell
git remote -v
```

从 eleme_sre 的 master 分支上拉取内容到本地；
```shell
git pull eleme_sre master
```

将拉取到本地的内容推到名为 origin 的 master 分支，即推到自己的 github 仓库中；
```shell
git push
```





