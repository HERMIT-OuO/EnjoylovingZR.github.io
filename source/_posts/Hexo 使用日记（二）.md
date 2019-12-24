---
title: Hexo 使用日记（二）
date: 2018-02-11 21:15:05
description: 打造属于自己的 Hexo 
urlname: Hexo_Diary_2
tags:
 - Hexo
 - 教程
---

# 了解基本的 Hexo 文件结构

## 初始主目录结构

> |-- _config.yml
> |-- scaffolds
> |-- source
>    |-- _posts
> |-- themes
> |-- .gitignore
> |-- package.json

## 主目录文件简介

- **_config.yml**

  _config.yml 是全局配置文件，采用 YAML 语法格式，可[自行学习](https://my.oschina.net/u/1861837/blog/526142?p={{totalPage}})。

  以下是该文件中默认内容的简单注释：

  ```yaml
  # Hexo Configuration
  ## Docs: https://hexo.io/docs/configuration.html
  ## Source: https://github.com/hexojs/hexo/

  # Site
  title: Hexo #网站标题
  subtitle:   #网站副标题
  description:  #网站描述
  author: John Doe  #作者
  language:    #语言
  timezone:    #网站时区。Hexo 默认使用您电脑的时区。时区列表。比如说：America/New_York, Japan, 和 UTC 。

  # URL
  ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
  url: http://yoursite.com   #你的站点Url
  root: /                       #站点的根目录
  permalink: :year/:month/:day/:title/   #文章的 永久链接 格式   
  permalink_defaults:    #永久链接中各部分的默认值

  # Directory   
  source_dir: source   #资源文件夹，这个文件夹用来存放内容
  public_dir: public     #公共文件夹，这个文件夹用于存放生成的站点文件。
  tag_dir: tags         # 标签文件夹     
  archive_dir: archives    #归档文件夹
  category_dir: categories      #分类文件夹
  code_dir: downloads/code     #Include code 文件夹
  i18n_dir: :lang                #国际化（i18n）文件夹
  skip_render:                #跳过指定文件的渲染，您可使用 glob 表达式来匹配路径。    

  # Writing
  new_post_name: :title.md # 新文章的文件名称
  default_layout: post     #预设布局
  titlecase: false # 把标题转换为 title case
  external_link: true # 在新标签中打开链接
  filename_case: 0     #把文件名称转换为 (1) 小写或 (2) 大写
  render_drafts: false  #是否显示草稿
  post_asset_folder: false  #是否启动 Asset 文件夹
  relative_link: false      #把链接改为与根目录的相对位址    
  future: true                #显示未来的文章
  highlight:                    #内容中代码块的设置    
    enable: true
    line_number: true
    auto_detect: false
    tab_replace:

  # Category & Tag
  default_category: uncategorized
  category_map:          #分类别名
  tag_map:            #标签别名

  # Date / Time format
  ## Hexo uses Moment.js to parse and display date
  ## You can customize the date format as defined in
  ## http://momentjs.com/docs/#/displaying/format/
  date_format: YYYY-MM-DD         #日期格式
  time_format: HH:mm:ss        #时间格式    

  # Pagination
  ## Set per_page to 0 to disable pagination
  per_page: 10    #分页数量
  pagination_dir: page  

  # Extensions
  ## Plugins: https://hexo.io/plugins/
  ## Themes: https://hexo.io/themes/
  theme: landscape   #主题名称

  # Deployment
  ## Docs: https://hexo.io/docs/deployment.html
  #  部署部分的设置
  deploy:     
    type:  #类型，常用的git
  ```

- **package.json**

  包含 Hexo 框架的参数和所依赖插件

- **scaffolds**

  包含新建 post 时需要的文件

- **source**

  初始状态下包含`_posts`文件夹，用于存储新建的 post 。

  另外，开启`tag`、`categories`等功能后会在`source`中生成相应的文件夹。

- **themes**

  包含 Hexo 主题文件

# Theme

## 选择心仪的主题

- Hexo 主题官方汇总： [Themes | Hexo](https://hexo.io/themes/) 
- 知乎：[有哪些好看的 Hexo 主题](https://www.zhihu.com/search?type=content&q=hexo%E4%B8%BB%E9%A2%98) 

## 应用主题

主要分以下两种方法：

1. 通常情况下，可将新的主题文件下载存放于`suorce`目录下，同时将`_config.yml`文件中`theme`的值修改为为主题名称。
2. 某些深度定制的主题没有提供主题文件，而是一个完整的 Hexo 文件夹。可选择将该站点作为新的 Blog 部署至 GItHub 。

## 配置主题

请参照主题的描述文件进行配置。

## 自定义样式

许多情况下，仅仅依靠修改主题无法达到预期的效果，此时便需要对某一部分内容进行针对性修改。




