---
title: Hexo+Github Page搭建个人博客
date: 2018-01-02 14:12:31
tags: hexo
categories: Note
---

# 前言  

前两天刚刚搭建好这个博客，想着趁热乎，脑中还记得一些搭建时需要在意的注意点啥的。于是，便有了下文。只是希望能够给以后想自己搭建博客的人一点微不足道的帮助。有什么不对的地方可以留言告诉我。

<!-- more -->
# 博客搭建   
## <font color=#0099ff>准备工作</font>
此教程中的博客是在Windows系统下搭建的，git用的是命令行而非图形化处理界面
* git（必需）
* node.js （必需）
* Github账号（必需）
* markdown编辑器（最好有一个，以后也方便写博客）
* 域名  


## <font color=#0099ff>git下载并安装</font>
作用：将本地hexo代码提交到GitHub上，（关于git，不了解的可以参考[史上最全github使用方法：github入门到精通](http://blog.csdn.net/v123411739/article/details/44071059/)也可自行搜索获或者去[官网](https://git-scm.com/)看看）
[下载](https://git-scm.com/download/win) 好相对应的git版本并安装，安装时按默认选项安装即可

## <font color=#0099ff>node.js下载并安装</font>
同样，[下载](https://nodejs.org/en/) 好，安装时同样可按默认选项安装即可

> 注：以上需要安装的步骤，若安装时出现问题请自行查询相关解决办法，此处不再详细说明

## <font color=#0099ff>Github账号</font>
申请GitHub之后即可建立个人远程库，用来做个人博客的服务器，以及生成GitHub域名，[可以参考此](https://pages.github.com/)
申请GitHub账号我就不多说了

## <font color=#0099ff>安装Hexo</font>
Hexo使用可以参考 [`Hexo document`](https://hexo.io/zh-cn/docs/index.html)
> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。（$为git命令行自带不需手动输入，只需输入$后面的，以下所有命令皆是）

**①** 鼠标右击桌面或其他任意地方，选择Git Bash Here，使用以下命令进行安装hexo
```
$ npm install hexo-cli -g
```

**②** 创建放置博客源码的文件夹：hexo文件夹
在自己想要的位置创建文件夹，建议放在英文文件夹目录下。如：E:\hexo

**③** 打开刚刚新建的hexo文件夹（此时文件夹需为空），右击选择Git Bash Here执行以下命令
```
$ hexo init
```
回车之后Hexo会自动在该文件夹下下载搭建网站所需的文件

**④** 安装依赖包
```
$ npm install
```
**⑤** 生成静态文件
```
$ hexo generate (或者输入 hexo g)
```
**⑥** 启动本地服务器
```
$ hexo server (或者输入 hexo s)
```
默认情况下，访问地址为：`http://localhost:4000/`
此时git命令行显示如下：
![](/assets/blogImg/hexo s.png)
由提示可以看出，hexo服务器已启动，并提示你按`Ctrl + C`来停止服务器


好了，运行到此，其实我们已经可以看到我们搭建的博客的雏形了，打开浏览器，在地址栏输入`http://localhost:4000/`在正常操作的情况下，此时你应该可以看到一个类似下面的图片的界面。这就是刚刚在本地建立的博客，别人无法访问。
页面如下：
![](/assets/blogImg/first.png)

这边我是将我现在的博客主题切换为默认主题时的样子，所以title和subtitle是被我修改过的，这些可在E:\hexo目录下的_config.yml配置文件中修改，进去找到相应的字段在其后面添加你的文字即可（`:`后同样需要加空格）

## <font color=#0099ff>注册Github账号</font>
已有Github账号跳过此步骤，点击[github](https://github.com/)进入注册页面

## <font color=#0099ff>创建repository</font>
repository作为一个远程的仓储室，即一个远程仓库，用来放置你上传的源码
![](/assets/blogImg/repository1.png)  

按照途中数字顺序进行操作，第③步时，blog为你想取的repository名，`.github.io`别忘了加上，后面设置需要
![](/assets/blogImg/repository2.png)

## <font color=#0099ff>部署本地文件到github</font>
远程仓库和本地仓库都创建好了，剩下的就是建立将本地代码提交到远程仓库的路径了，如此才能连接本地仓库和远程github提供的仓库。打开`E:\hexo`（刚刚新建的生成本地博客代码的文件夹）下的`_config.yml`文件，因为是mackdown文件，为了编辑方便，可以下载一个[Notepad++](https://notepad-plus-plus.org/download/v7.5.4.html),
一般是在_config.yml最下方，添加如下配置
```
deploy:
  type: git
  repository: http://github.com/username/blog.github.io.git
  branch: master
```
> 每个`: `后必须带一个空格
> repository后的`username`为GitHub用户名，第二个为之前创建的Repository的名字，记得修改为自己的。上面提到创建repository时填写Repository name要加个`.github.io`我一开始没加，自然这边也就没加，导致部署到GitHub page上后打开我的远程博客时报404，折腾了一会儿，在这边添加了这个之后问题解决，这还是因为对github不够了解，惭愧。

配置好之后执行以下代码
```
$ hexo generate (或者输入 hexo g)
$ hexo deploy (或者输入 hexo d)
```
上面两行也可简写为
```
$ hexo g -d
```


到目前，博客已经算是搭建完成了，而且也已经发布到GitHub上，别人也可以访问得到了。在浏览器上访问`http:\\username.github.io`就能看到自己的博客了。
> tips：1.这边的username并非我的GitHub帐户名，我只是举个例子，你们将username改为你自己的GitHub帐户名即可  
2.每次部署到GitHub上之后，可能要过一会儿才能显示最新的页面。即：输入完`hexo deploy`之后。建议一开始调试页面的时候在本地服务器上操作，可节省时间。  

<br>
>提示：每次部署前最好先clean  
步骤如下  

```
$ hexo clean
$ hexo generate
$ hexo deploy
```

## <font color=#0099ff>两个配置文件及主题更改</font>
在本地博客目录下有两个配置文件，分别是
* E:\hexo\_config.yml
* E:\hexo\themes\landscape\_config.yml  

第二个为博客主题的配置文件，若想换成自己喜欢的主题可以去网上找一些主题（这里推荐几个不错的[主题](https://www.zhihu.com/question/24422335)），把主题源码下载下来，然后将整个文件夹粘贴到`E:\hexo\themes`下，然后编辑第一个配置文件，找到`theme:`字段，将后面的landscape改为刚刚添加的主题文件夹名
第一个配置文件中第一部分，Site部分，需要修改为你个人的信息，其他没提到的暂时可以使用默认的，若想修改的更加个性化可以自己再研究，可以参考[Hexo文档](https://hexo.io/zh-cn/docs/index.html)，博主觉得这些已经够用了，找个喜欢的主题就差不多了，所以也没有深究。
```
# Site	//这下面的几项配置都很简单，基本都能明白什么意思及用途
title: Chillax blog	 //博客名
subtitle: Goals determine what you are going to be	//副标题
description: Goals determine what you are going to be //用于搜索，没有直观表现
author: DouDo	//作者
language: zh-CN	//语言
timezone: 	//时区，此处不填写，hexo会以你目前电脑的时区为默认值
```
第二个配置文件是根据主题而来，找到你喜欢的主题时，仔细看一下相关文档进行相应的修改即可。

## <font color=#0099ff>最后</font>
原本打算也整理出评论添加和域名绑定的相关文档，评论区引用有好多，目前比较推荐使用的是：Disqus和gitment,评论添加也很简单，我这边只稍微说一点，先推荐一个[教程](https://www.jianshu.com/p/c4f65ebe23ad)
> 他里面具体到添加多说代码块儿，你们添加时注意看下你们所找的主题，有的主题里可能已经配置好了，只需要你修改下配置文件里参数值。

至于域名，其实是可有可无的，自己有个域名可能会显得更加高大上些，这当中其实没多少要配置的，主要就是购买域名和域名解析，网上的域名绑定都大同小异，很容易搞定。

# 结语
其实，一开始想写个很详细的教程，后来又想，网上已经有很多教程了，总结来总结去也就这些。虽然本人也是第一次建博客，不过搭建时也没遇到啥大的坑，比较顺利。所以，觉得没啥好讲的。写它也是因为自己在博客初篇中提到以后会写个搭建教程，自己挖的坑哭着也要填完T.T
就当练一练mackdown文本编辑吧。  
有错误欢迎指出！
