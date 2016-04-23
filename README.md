# 多账户的git配置
----
## git配置基础

首先安装好git，接下来就可以对git进行设置了。通过如下命令配置git用户信息。用户名和邮箱对应你在各git平台(github/gitlab/oschina等)注册的信息

    git config user.name "[用户名]"
    git config user.email [邮箱]

配置变量存储于如下三个文件中

1. /etc/gitconfig 文件: 包含系统上每一个用户及他们仓库的通用配置。 使用如下命令配置
    
        git config --system

2. ~/.gitconfig 文件：只针对当前用户。 使用如下命令配置
    
        git config --global

3. 当前使用仓库的 Git 目录中的 config 文件（就是 .git/config）：针对该仓库。在仓库路径下使用不带参数的命令进行配置

        git config
        
更多内容请参考[git官方文档](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE)

#多账户配置
##同一邮箱多个平台
由于ssh生成的密钥对是针对邮箱的，那么同一个邮箱生成的密钥对可以应用于不同平台，只需生成一次，把公钥设置到不同平台即可。

##不同邮箱
这个时候，方法就是把一个邮箱设置为global，另一个在具体的git项目中设置具体用户。具体而言：

    #先设置global用户，这一步一般在安装git后就完成了，如果已经设置过，不需要重复
    git config --global user.name "[用户名1]"
    git config --global user.email [邮箱1]
    ＃进入到另一个用户的git项目路径
    cd [用户2的某git项目路径]
    git config user.name "[用户名2]"
    git config user.email [邮箱2]
    
##生成密钥对
需针对每一个邮箱生成一个密钥对，生成方法如下：

    ssh-keygen -t rsa -C "[邮箱]" 
