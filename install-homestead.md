#### 1.安装vagrant

#### 2.安装virtualbox

#### 导入box

`vagrant box add laravel/homestead`

![](/assets/20180118225040.png)

##### 根据虚拟机的不同，这里选择virtualbox

![](/assets/20180118225750.png)

##### 但是由于国内网速太慢，下载失败，所以可以考虑先下载你需要的box后再来添加

##### 首先在[hashicorp](https://app.vagrantup.com/laravel/boxes/homestead),再在链接后面加上, 再在链接后面加上 **版本号/providers/虚拟机类型.box**，即可获得下载链接

##### 如我们要下载最新版本为5.0.1的virtualbox版的box，链接即为:[https://atlas.hashicorp.com/laravel/boxes/homestead/versions/5.0.1/providers/virtualbox.box](https://atlas.hashicorp.com/laravel/boxes/homestead/versions/5.0.1/providers/virtualbox.box)

##### 新建一个homestead的文件夹，然后将下载的box重命名为homestead.box，然后在此文件夹内运行如下命令

```
vagrant box add laravel/homestead homestead.box
```

![](/assets/20180118225904.png)

##### 接着运行

```
vagrant box list
```

![](/assets/20180118230038.png)

##### 发现这个box已经添加进来就可以了

#### 下载官方homestead配置

##### 参照官方laravel5.5的[官方文档](http://laravelacademy.org/post/7658.html)

##### 按照文档的说明首先运行\(必须本地先安装git\)

```
git clone https://github.com/laravel/homestead.git Homestead
```

##### 克隆完成后，你需要检查Homestead的版本标签，因为`master`分支不会总是稳定版本，你可以在[GitHub Release Page](https://github.com/laravel/homestead/releases)查找最新稳定版本然后在本地将其检出
```
cd Homestead
git checkout v7.0.1
```
##### 接下来，在Homestead目录下运行bash init.sh来创建Homestead.yaml
```
//Mac/Linux...
bash init.sh

//Windows
ini.bat
```

#### Homestead.yaml

* provider: 表示Vagrant的提供者(`vistualbox`、`vmware_fushion`、`vmware_workstation`或`parallels`)

* folders: 列出了所有主机和Homestead虚拟机共享的文件夹,可以配置多个共享文件夹
 ```
 folders:
   - map: ~/code
     to: F:/vagrant/code
  ```
* sites:将“域名”映射到 Homestead 虚拟机的指定目录,可以配置多个站点
  ```
  sites:
    - map: homestead.test
      to: /home/vagrant/code/public
  ````
  把 Nginx 站点配置中的域名添加到本地机器上的 hosts 文件中，该文件会将对本地域名的请求重定向到 Homestead 虚拟机，在 Mac 或 Linux上，该文件位于 /etc/hosts，在 Windows 上，位于 C:\Windows\System32\drivers\etc\hosts，添加方式如下：
  ```
  192.168.10.10 homestead.app
  ```
##### 修改Homestead.yaml,之后需要执行`vagrant reload --provision` 更新虚拟机上的 Nginx 配置。


#### 启动homestea
##### 配置好 Homestead.yaml 文件后，在 Homestead 目录下运行`vagrant up`

#### 登陆、关闭和销毁虚拟机
##### 登陆要登录到该虚拟机，使用 `vagrant ssh` 命令；
##### 关闭该虚拟机，可以使用 `vagrant halt` 命令；
##### 销毁该虚拟机，可以使用 `vagrant destroy --force` 命令。

#### 连接Mysql数据库
##### 主机 IP： 127.0.0.1，端口号是 33060，用户名/密码是 homestead/secret

#### 更新Homestead
* 使用 vagrant box update 命令更新 Vagrant 盒子：
 ```
 vagrant box update
 ```
* 更新 Homestead 源码在克隆仓库的地方运行 git pull origin master 即可。

#### 问题
##### 如果出现`Check your Homestead.yaml file, the path to your private key does not exist.`
##### 解决办法：
```
//git将会生成密钥文件和私钥文件 id_rsa,id_rsa.pub
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

