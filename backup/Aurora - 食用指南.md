Aurora 是一款动漫风格博客主题，基于 Vue 开发，使用开源的 Github Api 服务，开发至今一直以为主题无人问津，近来有人问起如何食用，故忙里偷闲摸一篇简单食用文档。
Aurora 是一款动漫风格博客主题，基于 Vue 开发，使用开源的 Github Api 服务，开发至今一直以为主题无人问津，近来有人问起如何食用，故忙里偷闲摸一篇简单食用文档。

相较于 Wordpress 和 Typecho 等博客框架，Aurora 主题最大的优势就是简单轻量与免费，全部使用现有开源免费服务，相对稳定，也不怕 Github 跑路（笑），文章发布与更新也是相当简单，不需要操作服务器与数据库，对新人来说非常友好。
相较于 Wordpress 和 Typecho 等博客框架，Aurora 主题最大的优势就是简单轻量与免费，全部使用现有开源免费服务，相对稳定，也不怕 Github 跑路（笑），文章发布与更新也是相当简单，不需要操作服务器与数据库，对新人来说非常友好。
## 初始化环境
## 初始化环境
在食用 Aurora 主题之前，需先安装 Nodejs 和 Git 环境，这两步不必细说。环境安装完毕，由于 Aurora 使用 vue 开发，所以需要安装 `vue-cli`。
在食用 Aurora 主题之前，需先安装 Nodejs 和 Git 环境，这两步不必细说。环境安装完毕，由于 Aurora 使用 vue 开发，所以需要安装 `vue-cli`。
```bash
npm ```bash install -g @vue/cli-service-global
``` npm install -g @vue/cli-service-global
```
然后将主题 clone 到本地并安装依赖包：
然后将主题 clone 到本地并安装依赖包：
```bash
# ```bash clone 主题
git # clone git@github.com:chanshiyucx/aurora.git 主题
git clone git@github.com:chanshiyucx/aurora.git
# 进入主题目录
cd # aurora 进入主题目录
cd aurora
# 安装依赖包
npm # install 安装依赖包
npm install
# 本地预览
npm # start 本地预览
``` npm start
```
依赖包安装完毕，便可执行 `npm start` 本地预览效果，访问 `http://localhost:8080/`, 当然现在看到的是我的博客，接下来需要我们自定义主题。
依赖包安装完毕，便可执行 `npm start` 本地预览效果，访问 `http://localhost:8080/`, 当然现在看到的是我的博客，接下来需要我们自定义主题。
## 替换站点标题和图标
## 替换站点标题和图标
首先修改站点标题和图标，替换主题目录 `public/assets` 下的图标资源，然后修改 `public/index.html` 的站点标题和描述，同时注意修改 `manifest.json` 标题。
首先修改站点标题和图标，替换主题目录 `public/assets` 下的图标资源，然后修改 `public/index.html` 的站点标题和描述，同时注意修改 `manifest.json` 标题。
## 配置主题
## 配置主题
主题配置文件为根目录下 `src/config.js`，里面每个配置项皆有详细注释，这里对一些基本配置项做简要说明。
主题配置文件为根目录下 `src/config.js`，里面每个配置项皆有详细注释，这里对一些基本配置项做简要说明。
### 配置文章仓库
### 配置文章仓库
Aurora 使用 Github api 做后台数据托管。所以需要新建一个仓库来存放文章和一些自定义页面内容。这里新建一个仓库取名为 Blog 为例。
Aurora 使用 Github api 做后台数据托管。所以需要新建一个仓库来存放文章和一些自定义页面内容。这里新建一个仓库取名为 Blog 为例。
由于 Github api 有访问次数限制，所以需要申请 token 来解除访问限制，[申请地址戳这里](https://github.com/settings/tokens/new)。将申请的 token 从中间随意拆成两部分填入配置项，拆分的目的避免代码提交的时候 github 对其进行检测，导致 token 失效。
由于 Github api 有访问次数限制，所以需要申请 token 来解除访问限制，[申请地址戳这里](https://github.com/settings/tokens/new)。将申请的 token 从中间随意拆成两部分填入配置项，拆分的目的避免代码提交的时候 github 对其进行检测，导致 token 失效。
![Github Token](https://raw.githubusercontent.com/o0v0/o0v0/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image.png)
![Github Token](https://raw.githubusercontent.com/o0v0/o0v0/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image.png)
```javascript
// ```javascript github 用户名
username: // 'chanshiyucx', github 用户名
// username: 仓库地址 'chanshiyucx',
repository: // 'blog', 仓库地址
// repository: token 'blog', 从中间任意位置拆开成两部分，避免 github 代码检测失效
token: // ['0ad1a0539c5b96fd18fa', token 'aaafba9c7d1362a5746c'], 从中间任意位置拆开成两部分，避免 github 代码检测失效
``` token: ['0ad1a0539c5b96fd18fa', 'aaafba9c7d1362a5746c'],
```
### 配置 Leancloud
### 配置 Leancloud
Aurora 主题的文章阅读次数与 Valine 评论系统都是采用 [Leancloud](https://leancloud.cn/) 存储。注册一个 Leancloud 账号并新建一个应用，将应用 key 填入相应配置项。 **然后创建三个 Class，Comment 用来存储游客评论、Counter 用来存储文章热度、Visitor 用来统计友链访问次数，注意新建时选择表的访问权限无限制。**
Aurora 主题的文章阅读次数与 Valine 评论系统都是采用 [Leancloud](https://leancloud.cn/) 存储。注册一个 Leancloud 账号并新建一个应用，将应用 key 填入相应配置项。 **然后创建三个 Class，Comment 用来存储游客评论、Counter 用来存储文章热度、Visitor 用来统计友链访问次数，注意新建时选择表的访问权限无限制。**
![Leancloud_应用_Key](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(1).png?raw=true)
![Leancloud_应用_Key](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(1).png?raw=true)
```javascript
/** ```javascript
/** * leancloud 配置 【文章浏览次数】
*/ * leancloud 配置 【文章浏览次数】
leancloud: { */
leancloud: appId: { 'b6DWxsCOWuhurfp4YqbD5cDE-gzGzoHsz',
appKey: appId: 'h564RR5uVuJV5uSeP7oFTBye' 'b6DWxsCOWuhurfp4YqbD5cDE-gzGzoHsz',
} appKey: 'h564RR5uVuJV5uSeP7oFTBye'
``` }
```
> LeanCloud 中国版 2019 年 10 月份后开始停止为不绑定自有域名的应用服务，所以需要将节点切换到国际版。
> LeanCloud 中国版 2019 年 10 月份后开始停止为不绑定自有域名的应用服务，所以需要将节点切换到国际版。
### 配置 Gitalk
### 配置 Gitalk
Gitalk 是一个基于 GitHub Issue 和 Preact 开发的评论插件。其原理的文章存储是一样的，详细介绍见[官方文档](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)。
Gitalk 是一个基于 GitHub Issue 和 Preact 开发的评论插件。其原理的文章存储是一样的，详细介绍见[官方文档](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)。
首先需要申请 [GitHub Application](https://github.com/settings/applications/new)，跳转地址填写你的博客域名，如果你使用 github pages 来托管你的网站，你也可以使用 `https://chanshiyucx.github.io` 域名。最后将生成的 `Client ID` 和 `Client Secret` 填入相应配置项。**在开发环境调试时 Gitlak 无法展示是正常现象，发布到线上后会正常显示。**
首先需要申请 [GitHub Application](https://github.com/settings/applications/new)，跳转地址填写你的博客域名，如果你使用 github pages 来托管你的网站，你也可以使用 `https://chanshiyucx.github.io` 域名。最后将生成的 `Client ID` 和 `Client Secret` 填入相应配置项。**在开发环境调试时 Gitlak 无法展示是正常现象，发布到线上后会正常显示。**
![申请 GitHub Application](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(2).png?raw=true)
![申请 GitHub Application](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(2).png?raw=true)
![生成 clientID 和 clientSecret](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(3).png?raw=true)
![生成 clientID 和 clientSecret](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(3).png?raw=true)
```javascript
/** ```javascript
/** * Gittalk 配置【评论功能】
*/ * Gittalk 配置【评论功能】
gitalk: { */
gitalk: clientID: { '864b1c2cbc4e4aad9ed8',
clientSecret: clientID: '6ca16373efa03347e11a96ff92e355c5cea189bb', '864b1c2cbc4e4aad9ed8',
repo: clientSecret: 'Comment', '6ca16373efa03347e11a96ff92e355c5cea189bb', // 你的评论仓库
owner: repo: 'chanshiyucx', 'Comment', // 你的 你的评论仓库 github 账户
admin: owner: ['chanshiyucx'], 'chanshiyucx', // 你的 github 账户
distractionFreeMode: admin: false ['chanshiyucx'], // 是否开始无干扰模式【背景遮罩】 你的 github 账户
} distractionFreeMode: false // 是否开始无干扰模式【背景遮罩】
``` }
```
到此为止，所有主要的配置项皆已完成，剩下的几个配置项非常简单，相信你自己可以配置完善。
到此为止，所有主要的配置项皆已完成，剩下的几个配置项非常简单，相信你自己可以配置完善。
## 页面模板
## 页面模板
为了更好地定制各个页面的展示效果，Aurora 约定一些页面格式以便内容能够正确解析。主要约定 `文章、书单、友链、关于` 四个页面内容模板。模板参考 [蝉時雨の Issues](https://github.com/chanshiyucx/blog/issues)。
为了更好地定制各个页面的展示效果，Aurora 约定一些页面格式以便内容能够正确解析。主要约定 `文章、书单、友链、关于` 四个页面内容模板。模板参考 [蝉時雨の Issues](https://github.com/chanshiyucx/blog/issues)。
### 文章模板
### 文章模板
文章模板没有太多的格式约束，只需要在文章正文顶部加上封面配图即可，配图采用的是 markdown 的注释语法，所以并不会在正文里渲染，以后即使你更换博客主题，也不会影响内容的展示。
文章模板没有太多的格式约束，只需要在文章正文顶部加上封面配图即可，配图采用的是 markdown 的注释语法，所以并不会在正文里渲染，以后即使你更换博客主题，也不会影响内容的展示。
```markdown
[pixiv: ```markdown 41652582]: # "/IMAGES/bg/3.jpg"
``` [pixiv: 41652582]: # "/IMAGES/bg/3.jpg"
```
由于博客的文章、友链、书单、关于、心情等内容都放在 issues 里，所以需要对它们进行区分，这里主要使用 `issues 状态`与 `Labels` 进行分类。
由于博客的文章、友链、书单、关于、心情等内容都放在 issues 里，所以需要对它们进行区分，这里主要使用 `issues 状态`与 `Labels` 进行分类。
首先需要规定的是**文章的 issues 状态都是 `open` 的，友链、书单、关于、心情页面的 issues 内容都是 `closed` 状态的**。
首先需要规定的是**文章的 issues 状态都是 `open` 的，友链、书单、关于、心情页面的 issues 内容都是 `closed` 状态的**。
新建文章的时候 `Labels` 表示文章标签，`Milestone` 代表文章的分类，同时在文章正文顶部使用 markdown 注释来设置文章封面图，如下所示：
新建文章的时候 `Labels` 表示文章标签，`Milestone` 代表文章的分类，同时在文章正文顶部使用 markdown 注释来设置文章封面图，如下所示：
![文章模板](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(4).png?raw=true)
![文章模板](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(4).png?raw=true)
Tips：通过给正文图片预设尺寸可以获得更流畅的图片加载效果，尺寸设置形如 `?vw=1920&vh=1080`，举个栗子：
Tips：通过给正文图片预设尺寸可以获得更流畅的图片加载效果，尺寸设置形如 `?vw=1920&vh=1080`，举个栗子：
```markdown
[预设尺寸](/IMAGES/bg.png?vw=1920&vh=1080) ```markdown
``` [预设尺寸](/IMAGES/bg.png?vw=1920&vh=1080)
```
### 心情模板
### 心情模板
注意心情 issues 状态是 `closed` 的，且需要打上 `Inspiration` 的 Labels，其他不做约束。
注意心情 issues 状态是 `closed` 的，且需要打上 `Inspiration` 的 Labels，其他不做约束。
![书单、友链、关于标签](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(5).png?raw=true)
![书单、友链、关于标签](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(5).png?raw=true)
### 友链模板
### 友链模板
友链页面使用空行做分割，内容示例如下：
友链页面使用空行做分割，内容示例如下：
```text
## ```text 阁子
## 阁子
link: //newdee.cf/
cover: link: //i.loli.net/2018/12/15/5c14f329b2c88.png //newdee.cf/
avatar: cover: //i.loli.net/2018/12/15/5c14f3299c639.jpg //i.loli.net/2018/12/15/5c14f329b2c88.png
``` avatar: //i.loli.net/2018/12/15/5c14f3299c639.jpg
```
### 书单模板
### 书单模板
书单页面使用空行做分割，内容示例如下：
书单页面使用空行做分割，内容示例如下：
```text
## ```text ES6 标准入门
## ES6 标准入门
author: 阮一峰
published: author: 2017-09-01 阮一峰
progress: published: 正在阅读... 2017-09-01
rating: progress: 5, 正在阅读...
postTitle: rating: ES6 5, 标准入门
postLink: postTitle: //chanshiyu.com/#/post/12 ES6 标准入门
cover: postLink: //chanshiyu.com/yoi/2019/ES6-标准入门.jpg //chanshiyu.com/#/post/12
link: cover: //www.duokan.com/book/169714 //chanshiyu.com/yoi/2019/ES6-标准入门.jpg
description: link: 柏林已经来了命令，阿尔萨斯和洛林的学校只许教 //www.duokan.com/book/169714 ES6 了...他转身朝着黑板，拿起一支粉笔，使出全身的力量，写了两个大字：“ES6 万岁！”（《最后一课》）。
``` description: 柏林已经来了命令，阿尔萨斯和洛林的学校只许教 ES6 了...他转身朝着黑板，拿起一支粉笔，使出全身的力量，写了两个大字：“ES6 万岁！”（《最后一课》）。
```
### 关于模板
### 关于模板
关于页面以 `## 段落` 拆分，其他不做约束。
关于页面以 `## 段落` 拆分，其他不做约束。
### 添加分类
### 添加分类
![添加分类](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(6).png?raw=true)
![添加分类](https://github.com/o0v0/o0v0/blob/main/Aurora%20%E9%A3%9F%E7%94%A8%E6%8C%87%E5%8D%97/image%20(6).png?raw=true)
## 部署
## 部署
Aurora 2.0 添加一键部署功能，只需要编辑 `build.sh`，配置自己的仓库和域名，之后命令行执行 `./build.sh`，即可自动打包并上传到指定仓库，将该仓库开启 `Github Pages` 功能即可在线访问。相关文档参考[自动部署](https://cli.vuejs.org/zh/guide/deployment.html#now)。
Aurora 2.0 添加一键部署功能，只需要编辑 `build.sh`，配置自己的仓库和域名，之后命令行执行 `./build.sh`，即可自动打包并上传到指定仓库，将该仓库开启 `Github Pages` 功能即可在线访问。相关文档参考[自动部署](https://cli.vuejs.org/zh/guide/deployment.html#now)。
Just enjoy it💦
Just enjoy it💦
