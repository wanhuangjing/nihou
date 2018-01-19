#### 1.安装vagrant

#### 2.安装virtualbox

#### 导入box

\`vagrant box add laravel/homestead\`

![](/assets/20180118225040.png)

##### 根据虚拟机的不同，这里选择virtualbox

![](/assets/20180118225750.png)

##### 但是由于国内网速太慢，下载失败，所以可以考虑先下载你需要的box后再来添加

##### 首先在\[hashicorp\]\([https://app.vagrantup.com/laravel/boxes/homestead\)](https://app.vagrantup.com/laravel/boxes/homestead%29,再在链接后面加上), 再在链接后面加上 \*\*版本号/providers/虚拟机类型.box\*\* 即可获得下载链接[http://www.baidu.com](http://www.baidu.com "baidu")

##### 如我们要下载最新版本为 \*\*5.0.1\*\* 的virtualbox版的box，链接即为:\[[https://atlas.hashicorp.com/laravel/boxes/homestead/versions/5.0.1/providers/virtualbox.box\]\(https://atlas.hashicorp.com/laravel/boxes/homestead/versions/5.0.1/providers/virtualbox.box](https://atlas.hashicorp.com/laravel/boxes/homestead/versions/5.0.1/providers/virtualbox.box]%28https://atlas.hashicorp.com/laravel/boxes/homestead/versions/5.0.1/providers/virtualbox.box%29%29\)

##### 新建一个homestead的文件夹，然后将下载的box重命名为homestead.box，然后在此文件夹内运行如下命令

\`\`\`\`

vagrant box add laravel/homestead homestead.box

\`\`\`\`

![](/assets/20180118225904.png)

##### 接着运行

\`\`\`\`

vagrant box list

\`\`\`\`

![](/assets/20180118230038.png)

##### 发现这个box已经添加进来就可以了

#### 下载官方homestead配置

##### 参照官方laravel5.5的\[官方文档\]\([http://laravelacademy.org/post/7658.html\](http://laravelacademy.org/post/7658.html%29\)

##### 按照文档的说明首先运行\(必须本地先安装git\)



