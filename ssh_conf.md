## github配置ssh pub key
1、 查看是否已经存在创建的ssh key
> 打开 git bash here
>  cd ~/.ssh & ls
> 如果存在 id_rsa 和 id_rsa.pub 则说明已经创建过了

2、 如果不存在，则生成ssh key
> 使用 git bash 执行命令 ssh -keygen -t rsa -C "yyy@mail.com"

3、 查看public key
> cd ~/.ssh
> cat id_rsa.pub

4、 复制public key到 github 里
