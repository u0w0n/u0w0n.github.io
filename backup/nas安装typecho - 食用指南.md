<!-- ##{"script":"<script src='https://blog.meekdai.com/Gmeek/plugins/GmeekTOC.js'></script><script src='https://blog.meekdai.com/Gmeek/plugins/lightbox.js'></script>"}## -->


Typecho 是一个轻量级的博客平台，旨在提供简洁高效的写作体验。它的程序体积小于500KB，功能齐全，适合个人博客和技术博客使用。Typecho 的官方网站提供了详细的文档和资源，用户可以通过简单的步骤快速搭建自己的博客。此外，还有许多主题和插件可供选择，以便用户根据自己的需求进行定制。对于新手用户，有多种教程可帮助他们在不同环境下部署 Typecho 博客

### 拉取镜像
> [!IMPORTANT]
> docker pull joyqi/typecho:1.2.1-php7.4-apache

#### 部署typecho容器
在本地镜像中选择点击 部署到容器
typecho部署就容易很多，大部分和mysql差不多。第一次部署typecho的话，记得随时进后台备份数据，防止折腾崩了你的文章就白写了。

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=1000 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-30-40_80c5436981497.png"  alt=""/>
</a></p>

这里的博客端口我设置的是9040，忘了为啥是这个了，好像是以前部署的时候看的哪一篇教程就是这个，那会儿太萌新了，怕操作错了，完全照着
教程来的。
最后需要把能力一栏，把所有权限都勾上。 习惯全勾，也是因为以前部署容器的时候踩过坑。
最后点击应用，之后就可以通过内网ip+端口来访问了。

-----------------

#### 安装typecho
浏览器输入 http://你的极空间局域网ip:博客端口/install.php 例如： http://192.168.0.103:9040/install.php
进入欢迎页面直接点下一步。
然后填写数据库信息

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-32-08_cb0aa56c1c260.png"  alt=""/>
</a></p>

数据库一栏可以选择原生mysql或者pdo驱动mysql，原作者推荐pdo那就pdo吧，
选择sqlite的话不需要mysql，但容易出毛病，不知道咋解决所以还是推荐mysql。
之后点击 确认，开始安装
如果提示error的话，检查数据库地址，可以查看mysql容器里的网络，然后尝试直接填写172.17.0.X格式的地址，
之后再检查密码，
检查数据库ssl关没关，
还是有问题的话，去mysql容器检查是否开启成功，重启mysql容器之类的也行。
成功后画面如下

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-33-04_a921e10143672.png"  alt=""/>
</a></p>

进入这个页面后就说明数据库构建很成功不用去管了，
用户名和密码和邮箱都是后台的个人信息，用来登陆用的，
网站地址可以先填上你的域名，也可以先默认的放着，反正现在填了也没用会恢复默认的。
点击继续安装
成功后可以通过 极空间局域网ip+博客端口 访问博客页面，例如 http://192.168.0.103:9040/

#### 总结
> [!IMPORTANT]
>  博客至此部署完成
>  整体还是挺简单的