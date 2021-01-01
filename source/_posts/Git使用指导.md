---
title: Git使用指导
date: 2021-01-01 16:54:48
tags: 教程
---
记录一些使用遇到的坑和填坑方法，先行推荐一个网站：[OhShitGit](https://ohshitgit.com/zh)。

## 1. 同步的时候总需要验证？

多半是~~装的~~你使用了https进行克隆和同步，可以在文件夹中git bash后用以下命令查看：

``` bash
git remote -v
```

确定之后就可以用以下代码使用ssh方式替换https进行同步。

``` bash
git remote set-url origin [url]
```

具体方法参考网上的教程

## 2. 有两个SSH要选着用？

不要慌，在/.ssh文件夹中创建一个新的文件命名为“config”，在其中输入以下内容：

``` bash
Host [url]
    User git
    IdentityFile [ssh文件位置]
    IdentitiesOnly yes
Host [url]
    User git
    IdentityFile [ssh文件位置]
    IdentitiesOnly yes
```

其中：[url]部分填写你库所在的网址，如果是gitee就填[gitee.com](https://gitee.com)，User表示是哪个命令使用这个配置，在这里就是git命令配置成功后，你就可以对在不同网站托管的库使用不同的ssh密钥了。
