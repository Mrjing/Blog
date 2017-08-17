---
title: 使用github和hexo搭建博客并绑定自己的域名
date: 2017-03-30 16:19:04
tags: 
- hexo
categories: [hexo]
---
<p></p>
<!-- more -->
这几天看了些使用github加上hexo搭建博客的资料，便着手搭建了一个个人博客，虽然网上有许多人分享了成功搭建的经验，但自己还是遇到了不少坑，现将完整的搭建过程进行总结。

## 使用hexo搭建个人博客并部署到github  ##

 1. github上创建仓库blog,设置它的github page，此时github给你分配的域名为 https://你的github用户名.github.io/blog/
 
 2. 本地新建一个空文件夹blog，进入文件夹并使用hexo 命令初始化
    ``` bash
    $ hexo init
    ```
 3. 安装依赖,hexo init后会默认安装一些依赖，但是这里我们还需要安装hexo-deployer-git
    ``` bash
    $ npm install hexo-deployer-git --save
    ```
 4. 修改项目根目录下的_config.yml文件(即站点配置文件,:后的属性值前要加空格)
    ``` yml
    url: https://你的github用户名.github.io/blog
    root: /blog/
    deploy:
      type: git 
      repository: git@github.com:Mrjing/blog.git #换成你自己的
      branch: master #自己选择分支
    ```
 5. 使用hexo命令部署到github上
    ``` bash
    $ hexo clean #清除缓存
    $ hexo deploy 
    ```
 6. 现在访问https://你的用户名.github.io/blog/, 发现已经可以访问landscape主题的页面,现在我们就完成了使用hexo搭建个人博客并部署到gitHub上. 

## 购买域名 ##
 1. 相信很多朋友都想有一个属于自己的域名，这里我选择在godaddy上购买(貌似万网贵很多?),进入godaddy官网后先确认自己的国家/地区是否为新加(以前貌似可选中国,现在没了),这一步的目的是确保付款时有支付宝选项。
 2. 搜索框中输入自己想要的域名，你的域名可用时，下一步godaddy会为你推荐一些服务,忽略即可,然后进入购物车。
 3. 在购物车中选择期限，我选了一年，此时godaddy又为我推荐了服务，继续忽略，然后点击付款。
 4. 这时付款页面上应该能看到支付宝和银联以及借记卡的方式，一般选前两种会比较方便,注意:有的朋友可能会发现自己并没有支付宝或者银联选项，这时你可能需要换一下你的促销码(我之前就遇到了这个问题，但是换了促销码后价格的优惠也可能变化).之后点击支付即可。

## 将自己的域名与博客 绑定 ##
 1. 进入godaddy，点击右上角的个人用户名，链接菜单中选择管理域名
 2. 找到DNS管理，进入后可以添加记录，这里我们添加两条主机记录
    主机记录@,类型A，记录值192.30.252.153
    主机记录www, 类型A, 记录值192.30.252.153(或者主机记录www,类型CNAME,记录值你的github用户名.github.io)
 3. 进入本地的博客项目根目录的source文件夹下，新建文件，重命名为CNAME(无后缀),内容输入你申请的域名
 4. 再次修改项目根目录下的_config.yml文件
    ``` yml
    url: http://www.yoursite.com #换成你自己的域名
    root: /
    ```
 5. 再次使用hexo命令将其部署到gitHub上(与第一个操作中第5条一样),这时候访问你的域名就可以看到hexo搭建的博客了.
 





