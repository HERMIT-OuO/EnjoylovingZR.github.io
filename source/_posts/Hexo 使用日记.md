---
title: Hexo 使用日记（一）
date: 2018-02-08 17:59:47
description: Hexo + GitHub Pages 搭建个人博客教程
urlname: Hexo_Diary
tags:
 - 教程
 - Hexo
---

## Hexo 是什么 

> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

Hexo 是一款基于Node.js的静态博客框架，可直接部署在 GitHub 上。GitHub Pages 服务目前提供免费的 1 GB 文件存储空间和每月 100 GB 的流量。Hexo 是非常适合搭建个人博客的框架之一。

> GitHub Pages sites are subject to the following usage limits:
>
> - GitHub Pages source repositories have a [recommended limit of 1GB](https://help.github.com/articles/what-is-my-disk-quota/#file-and-repository-size-limitations) .  
> - Published GitHub Pages sites may be no larger than 1 GB.
> - GitHub Pages sites have a *soft* bandwidth limit of 100GB per month.
> - GitHub Pages sites have a *soft* limit of 10 builds per hour.



## 为什么使用 Hexo 来搭建 Blog

Blog 有多种搭建方式，Hexo + GitHub Page 无疑是最合适的方案之一。下面阐述原因：

1. GitHub Page 由 GitHub 提供，用于托管个人、组织或项目页面。这意味着无需再在云服务器上花费时间和精力，可直接通过 Git[^1] 将本地的文件部署至 GitHub 存储库，即可完成网站的推送。
2. Hexo 仅依赖于 Node.js，易于安装。
3. Hexo 官网文档对中文支持十分友好，且有数以千计的主题、插件供使用。




## 搭建步骤 

1. 在 GitHub 上创建个人仓库
2. 配置 Git、Node.js 环境
3. 配置 Hexo
4. 推送网站
5. 申请、绑定个人域名
6. 写作
7. 个性化设置
8. 其他

在搭建开始前请仔细阅读 [Hexo 官方文档](https://hexo.io/zh-cn/docs/) 。  

###  在 GitHub 上创建个人仓库

- 登陆 [GitHub](https://github.com/) （若无账号请注册）
- 点击 `New repository` 创建新仓库[^2]

### 配置 Git

Git 是目前世界上最先进的分布式版本控制系统（没有之一）。通过 Git 可将本地搭建好的网站直接部署到刚刚创建的 GitHub 存储库里。

#### 安装

- Windows：下载并安装 [git](https://git-scm.com/download/win).
- Mac：使用 [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/) ：`brew install git`;或下载 [安装程序](http://sourceforge.net/projects/git-osx-installer/) 安装。
- Linux (Ubuntu, Debian)：`sudo apt-get install git-core`
- Linux (Fedora, Red Hat, CentOS)：`sudo yum install git-core`

#### 绑定 Git 与 GitHub 

- 在空白处鼠标右击打开 ` Git Bash` 设置 user_name 和 user_email 配置信息：

  > `git config --global user.name`	GitHub 用户名
  > `git config --global user.email	GitHub` 注册邮箱

- 生成 ssh 密钥文件：

  > `ssh-keygen -t rsa -C`	GitHub 注册邮箱

  等待窗口响应后直接输入三个回车使用缺省配置即可。

- 在 GitHub 中配置 ssh 密钥：

   > /C/Users/`yourname`/.ssh/id_rsa	复制该文件中的全部内容   
   >
   > 打开[GitHub_Settings_keys](https://lgithub.com/settings/keys) 页面，点击 `new SSH Key` 新建密钥。
   >
   > 新建完成后可在 Git Bash 界面键入`ssh git@github.com`检测是否配置成功。

### 配置  Node.js 

​	安装 Node.js 的最佳方式是使用 [nvm](https://github.com/creationix/nvm)。

> cURL:
>
> `$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh`
>
> Wget:
>
> `$ wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh`
>
> 安装完成后，重启终端并执行下列命令即可安装 Node.js。
>
> `$ nvm install stable`
>
> 或者您也可以下载 [安装程序](http://nodejs.org/) 来安装。

### 配置 Hexo

#### 安装 Hexo

- 在本地新建文件夹作为 Hexo 的本地目录

- 在文件夹内按下`Shift`后单击`鼠标右键`打开 Powershell

- 使用 npm 安装 Hexo ：

  `$ npm install -g hexo-cli`（安装过程较长，请耐心等待）

#### 常用指令

`npm install hexo -g`		安装 Hexo

`npm update hexo -g`		升级 Hexo

`hexo init`		初始化站点

`hexo new yourtitle`		新建 post （可简写为`hexo n yourtitle`）

`hexo clean`		清除缓存

`hexo generate`		生成静态文件（可简写为`hexo g`）

`hexo deploy`		部署网站（可简写为`hexo d`）

### 推送网站

- 在建好的 blog 根目录中找到`_config.yml`文件，在文件末尾修改 deploy 代码：

  ```
  deploy: 
  type: git
  repo: GitHub仓库的路径 .git（末尾加.git后缀）
  branch: master
  ```

	保存文件

- 安装 Git 部署插件：

  `npm install hexo-deployer-git --save`

- 部署 Blog 至 GitHub：

  在 Powershell 中依次键入以下指令：

  ```
  hexo clean
  hexo g
  hexo d
  ```

- 访问网站

  在浏览器地址栏键入`仓库名.github.io`，即可访问。


### 申请、绑定域名

#### 域名是什么

>**域名**（英语：**Domain Name**），简称**域名**、**网域**，是由一串用点分隔的名字组成的 Internet 上某一台[计算机](https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA)或[计算机组](https://zh.wikipedia.org/w/index.php?title=%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BB%84&action=edit&redlink=1)的名称，用于在数据传输时标识计算机的电子方位（有时也指地理位置）。
>
>[网域名称系统](https://zh.wikipedia.org/wiki/%E7%BD%91%E5%9F%9F%E5%90%8D%E7%A7%B0%E7%B3%BB%E7%BB%9F)（[DNS](https://zh.wikipedia.org/wiki/DNS)，Domain Name System，有时也简称为域名）是因特网的一项核心服务，它作为可以将域名和[IP地址](https://zh.wikipedia.org/wiki/IP%E5%9C%B0%E5%9D%80)相互[映射](https://zh.wikipedia.org/wiki/%E6%98%A0%E5%B0%84)的一个分布式数据库，能够使人更方便的访问互联网，而不用去记住能够被机器直接读取的[IP地址](https://zh.wikipedia.org/wiki/IP%E5%9C%B0%E5%9D%80)数串。

例如 `www.baidu.com`是地址`220.181.57.216` 的域名

#### 如何申请域名

通常情况下域名需要在域名注册服务商处购买，下面推荐几家优秀的域名注册服务商：

[Godaddy](https://sg.godaddy.com/zh)

- 常规后缀域名价格相对便宜
- 客服服务到位
- 网站支持中文
- 支持支付宝付款

[Name](http://www.name.com)

- 续费价格和首年注册价格基本一致
- 操作面板简洁

[Namecheap](https://www.namecheap.com/)

- 各方面服务都很到位，性价比最高

以下是国内的服务商（不推荐使用）：

[万网](https://wanwang.aliyun.com/)

[腾讯云](https://cloud.tencent.com/)

#### 绑定域名

- 登陆 GitHUb ，进入放置 Blog 的仓库，点击`settings`，找到`Custom domain`，输入已购买的域名。

- 进入本地 Blog 文件夹，在`/source`目录下新建记事本文档，修改文件名为`CNAME` 。

- 键入已购买的域名，保存文件类型为`所有文件`。（注：键入域名时无需带有 www ）

- 解析域名

  下面提供两种方案（国内解析通常更快）：

  1. 在域名所属服务商处直接解析
  2. 在 DNSPos 或 阿里云 解析域名

  两种方案均需在解析中添加`CNAME`、`A`两种解析类型，分别解析`仓库名.github.io`和该网址对应的`IP地址`[^3]。

- 部署`CNAME`至 GIthub ，即可通过自定义域名访问 Blog。

  ```
  hexo clean
  hexo g
  hexo d
  ```


### 写作

### [个性化设置](https://ruoliang.top/post/hexo_diary_2)





### 其他









[^1]: 更多关于Git的详细内容请参见 [廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000) 
[^2]: GitHubo Pages 服务的仓库名一般为**Username**.github.io 
[^3]: IP地址 可在直接在 cmd 中 ping 对应网址得到
[^4]: 参考文章：[打造个性超赞博客Hexo+NexT+GithubPages的超深度优化](https://reuixiy.github.io/technology/computer/computer-aided-art/2017/06/09/hexo-next-optimization.html)  