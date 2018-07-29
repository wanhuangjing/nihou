1. 下载easyBCD 


2. 下载ubuntu16.04LS 


3. 安装easyBCD，安装好之后打开 

![](/assets/18-7-29-1.png)
选择“添加新条目”，然后选择“NeoGrub”，点击“安装”

![](/assets/18-7-29-2.png)

然后点击配置，将menu.lst文件的内容替换成一下文本：
```

title Install Ubuntu

root (hd0,0)

kernel (hd0,0)/vmlinuz.efi boot=casper iso-scan/filename=/ubuntu-14.04-desktop-amd64.iso locale=zh_CN.UTF-8

initrd (hd0,0)/initrd.lz

title reboot

reboot

title halt

halt
```

说明：
* hd0表示c盘所处的硬盘号，一般电脑只有一个，所以都是hd0；如果有多个硬盘，则根据情况改为hd0、hd1等。

* hd0后面的数字表示C盘在硬盘中的分区顺序，每个人的系统不大一样，不知道的可以在磁盘管理里面看一下，本人c盘是第三个分区，因此写为（hd0,2），如果是第一个，写为（hd0,0）即可。

* Ubuntu 32位的ISO包解压后casper文件夹下内核文件为vmlinuz，而64位解压后casper文件夹下内核文件为vmlinuz.efi。用EasyBCD创建的引导文件中内核文件所用名字为vmlinuz，所以如果是64位，可以将vmlinuz.efi改名为vmlinuz即可解决。

4. 将下载好的ubuntu16.04解压，进入解压目录下找到casper，进入casper文件夹initrd.lz和vmlinuz.efi复制到c 盘根目录：

![](/assets/18-7-29-3.png)

5. 重启电脑，多了一个启动选择项目NeoGrub引导加载器，选择并进入新的启动项目中。

6. 刷完后就进入一个小系统，别以为这就装好了，此时最重要的一步，通过快捷键ctrl+alt+T打开终端，输入：sudo umount -l /isodevice 
注意空格和小写的L，执行后就可以双击安装图标进行安装了
![](/assets/18-7-29-4.png)

