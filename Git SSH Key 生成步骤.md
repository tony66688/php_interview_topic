# Git SSH Key 生成步骤

> Git 是分布式的代码管理工具，远程的代码管理是基于 SSH 的，所以要使用远程的 Git 则需要 SSH 的配置。
> github 的 SSH 配置如下：

##### 一、设置 Git 的 user name 和 email：

```php
$ git config --global user.name "fanxiao2"

$ git config --global user.email "admin@fanxiao2.net"
```

##### 二、生成 SSH 密钥过程：

###### 1. 查看是否已经有了 ssh 密钥：cd ~/.ssh

如果没有密钥则不会有此文件夹，有则备份删除

###### 2. 生存密钥：

```php
$ ssh-keygen -t rsa -C "admin@fanxiao2.net"
```

按 3 个回车，密码为空。

```php
Your identification has been saved in /home/tekkub/.ssh/id_rsa.
Your public key has been saved in /home/tekkub/.ssh/id_rsa.pub.
The key fingerprint is:
………………
```

最后得到了两个文件：id_rsa 和 id_rsa.pub

###### 3. 添加密钥到 ssh：ssh-add 文件名

需要之前输入密码。

###### 4. 在 github 上添加 ssh 密钥，这要添加的是 “id_rsa.pub” 里面的公钥。

打开 https://github.com/ ，登陆 DevonChina，然后添加 ssh。

###### 5. 测试：ssh git@github.com

```php
The authenticity of host 'github.com (207.97.227.239)' can’t be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added ‘github.com,207.97.227.239′ (RSA) to the list of known hosts.
ERROR: Hi tekkub! You’ve successfully authenticated, but GitHub does not provide shell access
Connection to github.com closed.
```

##### 三、 开始使用 github

###### 1. 获取源码：

```php
$ git clone git@github.com:billyanyteen/github-services.git
```

###### 2. 这样你的机器上就有一个 repo 了。

###### 3.git 于 svn 所不同的是 git 是分布式的，没有服务器概念。所有的人的机器上都有一个 repo，每次提交都是给自己机器的 repo

仓库初始化：

```php
git init
```

生成快照并存入项目索引：

```php
git add
```

文件，还有 git rm,git mv 等等…
项目索引提交：

```php
git commit
```

###### 4. 协作编程：

将本地 repo 于远程的 origin 的 repo 合并，
推送本地更新到远程：

```php
git push origin master
```

更新远程更新到本地：

```php
git pull origin master
```

补充：
添加远端 repo：

```php
$ git remote add upstream git://github.com/pjhyett/github-services.git
```

重命名远端 repo：

```php
$ git://github.com/pjhyett/github-services.git为“upstream”
```

每一天都要进步一点点！