#### 小白也能轻松搞定的极空间docker安装/数据库与博客
 **拉取镜像提示**
> 推荐使用1.2.1 php7.4版本，其他版本，主题适配较少，不推荐使用，
> 最新版的nightly在极空间docker上有一些小bug，会修的可以用。(反正我不会)

> 这里需要拉取mysql和typecho，
> 为了方便管理强烈推荐安装mysql，图床等工具大部分也都需要，不如一步到位。
> 轻度用户不安装mysql也行，可以直接在博客页面选择sqlite数据库，会在博客目录下新建一个db后缀的数据库文件。
> sqlite除了不方便管理和修改以外别的都还行，有些插件不支持选这个，会server error。

> 既然装了mysql当然需要一个图形管理系统，不然总是在ssh上敲代码很麻烦。
> 所以可以拉取下面三个，
> 分别是 typecho博客本体， mysql5.7.44数据库， adminer图形管理
> mysql选择5.7是因为，高版本容易踩坑，5.7版本教程多，大部分都适配，不需要额外设置什么。
> 同时如果将来需要迁移也很方便，或者从宝塔迁移过来之类的也很容易，因为宝塔默认就是5.7.44版本。
> 想要迁移的时候，用typecho的mysql迁移插件来一键备份迁移，
> 如果版本不同或者编码不同还需要转码一次，用户多或是插件多的时候很麻烦，详情去百度查吧

### 拉取镜像
> [!IMPORTANT]
 `docker pull joyqi/typecho:1.2.1-php7.4-apache`
` docker pull mysql:5.7.44`
`docker pull adminer:latest`

> 在极空间中
> 选择 镜像 - 仓库 - 自定义拉取 - joyqi/typecho:1.2.1-php7.4-apache
> 同理 自定义拉取 - mysql:5.7.44 adminer:latest

**极空间如果没有配置代理，可能会拉取失败，可以多尝试几次，失败了就点重新拉取即可。**

> [!IMPORTANT]
>  部署容器
打开本地镜像可以看到刚刚下载好的三个镜像
选中镜像点击添加到容器即可部署

----------------------------------------

### 部署mysql容器
在本地镜像中选择 mysql 点击 部署到容器

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-53-53_e32b5820d7db9.png"  alt=""/>
</a></p>

给容器命名并勾选 极空间开机后自动启动此容器
<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-54-04_81fb27456474f.png"  alt=""/>
</a></p>

选择文件夹路径，随便选个你喜欢的文件夹，
（当你后面需要修改数据库文件的时候，推荐不要直接拿这里面文件动手，容易出错。特别是不要手动删除数据库文件。强烈推荐使用接口+管理面板来管理数据库，比如：Adminer图形化管理面板）

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-54-15_d2253e64b61c3.png"  alt=""/>
</a></p>

打开端口列表并将3306转发到3306，33060转发到33060。

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-54-23_4d32c2e9783d1.png"  alt=""/>
</a></p>

添加一行环境变量 MYSQL_ROOT_PASSWORD 并将值设置为你的密码。这一条是root账户的密码，如果不设置会无法启动容器无限重启。

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-54-30_f9d3c38e97539.png"  alt=""/>
</a></p>

勾选 -it 选项，（我发现不勾好像也不影响使用但还是推荐勾上吧，保险起见。）

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-54-37_84360d3533740.png"  alt=""/>
</a></p>

把容器权限全打开（同样是保险起见，除了监控类型的别的还是都打开吧，不然总是出些幺蛾子毛病）

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_11-54-42_2abcce0dfd1bf.png"  alt=""/>
</a></p>

------------------------------------

#### 部署adminer容器
这个部署不需要改太多，绑定端口后将权限全打开就行
选择本地镜像adminer后点部署，8080端口绑定的本地端口设置为 3305
打开全部权限，同mysql。
点击部署。

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-03-11_cd284bfa5d07f.png"  alt=""/>
</a></p>

进入浏览器，打开 http://你的极空间局域网ip:3305 示例： http://192.168.0.103:3305/
进入后可以看到如下

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-03-16_8e9652c7588c9.png"  alt=""/>
</a></p>

系统选择mysql
服务器输入你的极空间地址+端口3306,这个输入的是mysql的服务器，也就是刚才部署的mysql容器的端口。
用户名是root，
密码是上面部署mysql的时候，环境变量里添加的那个。
数据库可以不填，勾上保持登陆，点登陆。

--------------------------------------

#### 通过adminer图形管理面板新建数据库
进入adminer后台，在选择数据库的下方，点击 创建数据库 ，然后数据库名填写 typecho ，类型选校对即可，点击保存。

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-03-24_c195a1cf5f6eb.png"  alt=""/>
</a></p>

可以选择在typecho数据库新建一个用户，也可以不新建用户直接使用root管理员用户。
新建方式：返回数据库列表 - 选择刚刚新建的typecho数据库 - 点击上方‘权限’ - 点击创建用户
创建完成后需要勾选权限才可使用。
总之我比较懒，而且数据库只有我自己用，所以我就不新建用户了，直接用root来。

--------------------------------------

#### 未安装adminer新建数据库的方式
选择mysql容器，点击ssh按钮，然后点连接。

<p align="center">
<a href="https://github.com/anuraghazra/github-readme-stats">
    <img height=500 src="https://pic2.ziyuan.wang/user/0w0/2025/10/Snipaste_2025-10-27_12-08-53_841c41e551be0.png"  alt=""/>
</a></p>

后台输入 mysql -u root -p 然后回车
回车后，输入第一步里mysql环境变量设置的密码，然后再回车，登陆进mysql。
输入 CREATE DATABASE typecho; 回车， 新建数据库，
这里注意最后需要有 ; 符号，我第一次用数据库的时候踩过坑，研究了几个小时都新建不成功，回车之后没反应，这种犯蠢的时候感觉别人也会
有，所以顺便说一下。
（当然这也是为啥最后决定用adminer图形管理系统的原因，我太萌新了不想敲指令）

-----------------------------------------------

#### 部署typecho容器
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
>  博客至此部署完成，
>  整体还是挺简单的，一共就4大步
>  部署数据库，部署博客
>  再往后就是添加插件和主题了，这部分自行研究或者后面我会分享一些主题或插件推荐。