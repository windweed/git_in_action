# 多个KEY

首先，key是按邮箱生成的。  
即生成key时要指定邮箱。  
生成key时，要指定不同的名称。如`id_rsa_1`, `id_rsa_2`

查看系统ssh-key代理
```bash
$ ssh-add -l
```
如果输出  
`The agent has no identities.`  
则说明没有代理，有则可以通过 `$ ssh-add -D` 删除。

然后依次将不同的ssh添加代理：
```bash
$ ssh-add ~/.ssh/id_rsa1
Identity added: .....
$ ssh-add ~/.ssh/id_rsa2
Identity added: .....
```

如果提示以下信息:  
`Could not open a connection to your authentication agent.`

那么运行：
```bash
$ eval `ssh-agent -s`
Agent pid 5123
```
OR
```bash
$ ssh-agent bash
```
再运行`ssh-add`

创建~/.ssh/config
```bash
Host github.com
HostName github.com
User git
IdentityFile C:/Users/username/.ssh/id_rsa
 
# aysee (company_email@mail.com)
Host github-aysee
HostName github.com
User git
IdentityFile C:/Users/username/.ssh/aysee

```
未加入配置文件的网站会自动使用id_rsa



后续配置单独项目时这样添加：
```bash
$ git remote add test git@github-aysee:ay-seeing/test.git 
```
而不能直接使用`git@github.com`

测试SSH
```bash
$ ssh -T git@github.com
Hi xxx! You've successfully...
```

proj/.git/config
```
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
[user]
    name = czy
    email = ziijchen@163.com
[remote "github"]
    url = git@github-zii:windweed/HSUTILS.git
    fetch = +refs/heads/*:refs/remotes/github/*
[branch "main"]
    remote = github
    merge = refs/heads/main

```

