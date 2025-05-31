#  linux 使用经验集锦
## 说明  
曾经网络上有很多linux相关的各种经验,笔者印象深刻的是陈绪写的<Linux 一句话精彩问答>,但是很多文档都是一次性的,缺少类似wiki那样更新,本页面归纳本人日常使用中的问题.


## 日常使用相关
### <font color=blue>Q:我同时使用不同的发行版,各个发行版有不同的安装软件的命令,不容易记忆,怎么办?</font>

A:使用Sysget：给主流的包管理器加个前端,参考 :http://ju.outofmemory.cn/entry/373299
### <font color=blue>Q:如何使用snap安装软件包?</font>
A:snap相关指令： 

    sudo dnf install snapd  
    sudo snap find gimp  
    sudo snap install gimp  
    sudo snap refresh gimp //update GIMP  
    sudo snap refresh //update all  
    sudo snap remove gimp  
    sudo dnf install gnome-software-snap //Installing with Snap: GUI edition 

### <font color=blue>Q:man 文档太复杂,没有示例,怎么办?</font>

A:安装 TLDR （too long didn't read)客户端:

    sudo npm install -g tldr  
　　tldr --update //一旦安装了此终端实用程序，最好在尝试之前更新其缓存  
　　tldr <commandname> //阅读任何 Linux 命令的 TLDR 页面  

### <font color=blue>Q:如何安装和使用flatpak ?</font>
A: flatpak安装和使用命令参考如下，如下安装的是 octave 软件：  

    sudo apt-get install flatpak  
    sudo add-apt-repository ppa:alexlarsson/flatpak //add PPA  
    sudo apt-get update //update after add PPA  
    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo //add the Flathub repository  
    flatpak search octave  
    flatpak install flathub org.octave.Octave  
    sudo apt-get install gnome-software-plugin-flatpak //Install Software through Flatpak using the Software Manager UI  

### <font color=blue>Q:如何防止linux桌面自动锁屏?</font>
A:想象一下你在 Youtube 上看视频或阅读一篇新文章，突然你的 Ubuntu 锁屏了，我知道它很烦人。我们很多人都会遇到这种情况，所以咖啡因是一个阻止 Ubuntu 锁屏或屏幕保护程序的工具。
咖啡因指示器是一个轻量级的工具，它添加图标到通知栏，你可以在那里轻松的激活或禁止它。不需要额外的设置。

    $ sudo add-apt-repository ppa:eugenesan/ppa
    $ sudo apt-get update
    $ sudo apt-get install caffeine -y

### <font color=blue>Q:出现top中 kswapd0 的cpu占用率太高怎么办？</font>
A：参考 https://www.linuxuprising.com/2018/08/how-to-use-swap-file-instead-of-swap.html 配置一个交换分区文件。

### <font color=blue>Q：如何关闭密钥环？</font>
A：参考 https://jingyan.baidu.com/article/454316ab0ebb25f7a7c03af6.html

### <font color=blue>Q：高分辨率屏幕的linux电脑的相关问题 -开机GRUB字体太小的问题</font>
A：参考 http://blog.wxm.be/2014/08/29/increase-font-in-grub-for-high-dpi.html  
  不过有的发行版(如ubuntu中文版)的GRUB带中文字符，所以我改用了中文字体：  

    sudo grub-mkfont --output=/boot/grub/fonts/NotoSansCJK-Regular32.pf2 \
    --size=32 /usr/share/fonts/opentype/noto/NotoSansCJK-Regular.ttc

### <font color=blue>Q：高分辨率屏幕的linux电脑的相关问题 -wine的windows程序的DPI太小，看不清楚怎么办？</font>
A：下载winetricks，然后在“运行wine配置程序”（即winecfg）后，设置显示DPI改大，比如我改到200（我的笔记本分辨率是3K x 2K）。

### <font color=blue>Q：[debian系]报错:could not get lock /var/lib/dpkg/lock -open</font>
 A:解决方法：输入以下命令    

    sudo rm /var/cache/apt/archives/lock  
    sudo rm /var/lib/dpkg/lock
之后再安装想装的包，即可解决。


### <font color=blue>Q：git如何放弃本地修改，直接覆盖之</font>

A：    

    git fetch --all    
    git reset --hard origin/master


### <font color=blue>Q：如何调整显示的对比度？</font>
A：调整显示的对比度命令如下：   

     xgamma -gamma 0.70

其中数值的范围为：0-10.00                        

但该命令重启后就会失效，因此需要在用户变量下添加该命令，即在用户目录下任意含有“.bash”字样的文本内添加命令，如下操作：

vi /home/username/.bash   在尾部添加：xgamma -gamma 0.70


### <font color=blue>Q：firefox 浏览器的同步有国内和国外2个服务器？容易造成混乱。</font>

A：firefox浏览器的同步在中国有两套服务器,所以经常让人搞错,简单的办法是:  
在浏览器地址栏输入about:config ,然后搜索account,如果是国内服务器,则域名是带.cn的,否则就是firefox国际服务器.因为linux上都是使用firefox国际服务器,所以国内linux用户都建议使用firefox国际版本(国内安卓手机市场下载的apk都是使用国内服务器的).所以,如果手机要使用firefox国际版的,不能用google play市场的话,你就考虑用APKPure 来下载国际版的firefox.



## 编程相关
### <font color=blue>Q：cmake 如何可视化地查看编译的情况</font>
A：cmake 可以可视化地查看编译的结构：

    cmake  --graphviz=test.dot

然后用xdot工具可以查看生成的test.dot 文件

