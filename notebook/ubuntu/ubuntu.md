# ubuntu 命令行

## 系统管理

### 用户管理

```shell
cat /etc/passwd #查看系统已存在用户
sudo adduser newusr #建立新用户， 该命令可以添加新用户同时建立相应目录
sudo adduser newusr sudo #将新用户添加到指定组中使其拥有相应组的权限
```

### 文件管理

#### 修改文件所有者信息

```shell
sudo chown newusr:newusr file_path #单个文件修改, 同时修改所有者和所在组信息
sudo chown -R newusr:newusr file_path #目录递归修改, 同时修改所有者和所在组信息
sudo chgrp -R gropname file_path #只修改文件所在组信息
```

#### 设置共享文件夹

利用samba实现ubuntu系统和Windows系统文件共享功能。

```shell
sudo vim /etc/samba/smb.conf #设置samba的配置文件，指定共享文件地址，他人访问权限等
sudo systemctl restart smbd #重启samba服务
sudo /etc/init.d/samba restart #另一种重启samba服务的命令，该命令更加好用
sudo smbpasswd -a username #为已存在用户添加访问共享文件时需要提供的密码
```

```shell
[wucw_SSD] #与共享文件夹的名称一致
   comment = Shared Folder require password
   path = /home/usrname/share/wucw_SSD
   public = yes
   writable = yes #共享者是否可以修改文件
   create mask = 0775 #访问者建立文件时，文件属性
   directory mask = 0775 # 访问者建立目录时，文件夹属性
   #force user = nobody #访问者建立文件时，文件所有者信息
   #force group = nogroup #访问者建立文件时，文件所在组信息
   available = yes
   browseable = yes
   valid users = usrname #允许访问者的名字
```

#### 挂载硬盘

```shell
sudo mount /dev/sda1 /home/lpadas2/share/HDD 
#            硬盘         挂载地址
```

#### 链接文件

```shell
ln -s /home/lpadas2/share/HDD/wucw_HDD /home/wucw/share/HDD
#                源文件                    链接产生的新文件
```



### 安装软件

#### 离线安装python软件

- 在线安装

  pip工具进行在线安装

- 离线安装

  当电脑无法直接上网时，可以先到PyPI网站中找到软件包相关源代码，进行安装. 一般源文件安装包内均会有setup.py文件。

  ```shell
  python setup.py install
  ```


#### anaconda软件安装

python安装环境需要很多依赖包，可以使用anaconda软件来负责管理这些包。安装的时候可以选择软件给设置环境变量，否则自己还要设置。需要设置3个目录。anaconda、Script、Library\bin。

 

## 应用命令行

### git

``` shell
git init #在工作目录下执行该命令，可以执行初始化操作
git remote add origin git_url #将远程仓库网址利用origin表示，使用ssh连接github时，git_url需要是ssh连接
git remote set-url origin new_url #修改origin表示的远程网址
```

### shadowsocks
```shell
sslocal -c ~/shadow.json #打开本地代理接口
```











