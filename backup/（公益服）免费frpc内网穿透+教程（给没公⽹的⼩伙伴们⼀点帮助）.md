特别申明此项⽬为爱心发电，不提供售后服务。

* * *

以下操作，我使用1panel完成

选装系统，安装docker，然后使用docker 部署容器
~~~
# docker run：部署创建容器
docker run -d \
     --name wxchat \
     --restart=always \
     -p 42021:80 \
     ddsderek/wxchat:latest

# docker compose:部署创建容器

version: '3.3'services:
    wxchat:
        container_name: wxchat
        restart: always
        ports:
            - '9980:80'-
        image: 'ddsderek/wxchat:latest'
~~~
部署完成后使用上面 docker 部署的端口     

42021 \ 9980

<mark>使用服务器 IP 加上面端口，即可查看是否部署完成</mark>

使用这两个端口查看是否部署完成端口可以根据自己想要的修改端口号

* * *

#### 有问题可去极空间最新⽤户交流群找我 I D：2 1

如有用在MP微信消息通知的，信任IP人用的多了一以后，TX会限制使用，限制使用后我会换最新的连接地址，发现不能用了后去最新群找我

首先去网盘：https://pan.xunlei.com/s/VOJ8I1mJWBvSgHbgUsGHOnutA1?pwd=m2d8

找到FRPC内⽹穿透⽂件夹 s下载 nowdreamtech_frpc_latest.tar 和 frpc.toml 文件

（这⾥需要注意的是转成P DF格式后，地址你复制的时候可能会有空格，⾃⼰复制完检查⼀下）

1.先在本地你放 docker 文件的地方新建个 frpc 文件夹,然后打开frpc.toml 文件，并修改其中内容与你实际情况匹配 ，随后放⼊⽂件夹。

在nas部署一个frpc的docker 容器，在 docker 容器目录里创建下列frpc.toml文件并将目录映射到docker目录里创建即可

需要注意的一点是根据下列提示，修改自己的配置信息
~~~css
#### frpc.toml文件
transport.tls.enable = true 
#### 从 v0.50.0版本开始，transport.tls.enable的默认值为 true
serverAddr = "47.239.143.139" 
####云服务器ip
serverPort = 7000 
#### 公网云服务器端通信端口

auth.token = "token123456" 
#### 1panel的参数token令牌，与公网服务端保持一致

[[proxies]]
name = "test-http"
type = "tcp" # 不用改
localIP = "127.0.0.1" # 需要暴露的服务的IP(如果使用的是 host 模式，就不用改)
localPort = 3000  # mp的端口
remotePort = 8085# 自己改的暴露服务的公网入口
~~~
下列为参考项
~~~
[common]
server_addr=168.138.163.229
server_port =7000
authentication_method = token
token = 123456789
#### 上面都不要改 

[xxxxxxxx]
#### xxxxxxxx这里自已起个名字，不少于8个字符，复杂点，和别人冲突了你就不能用，名字对你后续并无实际作用，如果报错就尝试改 这里xxxxxxxx必须改掉，别傻乎乎的不改，碰到好几个傻孩子了

type = tcp
#### 不用改
 1oca1_ip = 192.168.0.0
#### 需要在公网上暴露端口的局域网设备IP地址（一般这里都是用在极空间上，就是极空间的局域网IP地址） 
local_port = 5055 
####局域网设备要用的端口，比如QBTRMP等等，你想放哪个就写哪个端口 自己想一个要用的端口，从30001-39999选一个，如果报错连不上有可能和别人冲突，自己再改一个 
remote_port = 30001 
#### 上面2个端口的关系是指用168.138.163.229：30001访间你局域网192.168.0.0：5055这样解释能明白了吧。
仅限转要 盗源有限 谢谢理解
~~~

# 2.打开 DOCKER 导入镜像 snowdreamtech_frpc_latest.tar
# 3.导入后选中并添加到容器
4.文件夹路径按图设置（左边为第1步你所建立文件夹的路径）右边为固定路径。

如果路径出现问题，那么就用这个路径<mark>**文件/文件夹选择你 docker 目录下的 fpc 目录**</mark>

<mark>**这个是装载路径/etc/frp**</mark>
![](https://pic2.ziyuan.wang/user/0w0/2025/02/Snipaste_2025-02-27_13-49-21_74eb9df9c57eb.png)
# 5.网络为 HOST
# 6.点应用创建，并查看日志是否连接成功，一般这样显示就算成功了。
应⽤场景举例：⽐如MP的微信通知，各个DOCKER的公⽹访问，你本地项⽬的外⽹访问，请合理使⽤，如果异常使⽤ BAN之

# **企业微信通知**

mp在通知渠道里，将微信添加进去，相应配置填好确认应用保存即可正常使用

#### http://服务端ip: 8085# 暴露服务的公网入口/api/v1/message/?token=mp的API令牌

部署完成之后，最后获得上列链接，将其填入企业微信自己创建的机器人api 接收信息里，提示成功则步署完成 

饿饿饭饭修改











