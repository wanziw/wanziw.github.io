---
title: Butterfly主题界面
date: 2024-07-19 18:44:50
cover: https://pic.imgdb.cn/item/669a4645d9c307b7e9f4ce5f.png
categories: Hexo教程
tags: 页面配置
description: butterfly设置记录
Copyright: true
copyright_author: wanzi
copyright_author_href: https://github.com/wanziw
copyright_url: https://wanziw.github.io/2024/07/19/%5BHexo%5DButterfly主题页面/
copyright_info: 此文章版權歸wanzi所有，如有轉載，請註明來自原作者
---



> https://www.bilibili.com/video/BV1Ko4y1S7mv/?p=11 
> hexo clean
> hexo g
> hexo d

# 主题界面

[Butterfly主题页面](https://butterfly.js.org/posts/dc584b87/)

- 标签页

> hexo new page tags

- 分类页

> hexo new page categories

- 友情链接
  - 创建并修改yml文件内容，添加想要关联到的链接
  - **source/_data    link.yml**

> hexo new page link

- 404页面
  - 根目录->node_modules->hexo-theme-butterfly-YML >_config.yml
  - 先找到这个文件，复制内容，在根目录下创建 _config.butterfly.yml，粘贴进去内容。
  - 在其中找到404那块，把false改成true

# 主题配置1

- 导航菜单
  - menu
    - ![](https://pic.imgdb.cn/item/669a30d6d9c307b7e9e0850f.png)
  - 路径是自动匹配source文件夹里的路径的
  - 配置成功就会出现导航栏
- 代码块
  - 4.1. 代碼高亮主題
    4.2. 代碼複製
    4.3. 代碼框展開/關閉
    4.4. 代碼換行
    4.5. 代碼高度限制

```
highlight_theme: mac light #  darker / pale night / light / ocean / mac / mac light / false
highlight_copy: true # copy button
highlight_lang: true # show the code language
highlight_shrink: false # true: shrink the code blocks / false: expand the code blocks | none: expand code blocks and hide the button
highlight_height_limit: false # unit: px
code_word_wrap: false
```

- 社交图标
  - Butterfly支持 [font-awesome v6](https://fontawesome.com/icons?from=io) 圖標.

  - 在这个网站上我们可以搜索到想要的图标，然后获得图标名字，放在代码的这个位置上就行了，后面加上链接![](https://pic.imgdb.cn/item/669a3508d9c307b7e9e38ee7.png)

- 主页文章自动节选

- 顶部图

  - 首页 分类页上面最大的那个图 可以分别单独设置
  - disable_top_img先改成false
  - 图片的加载除了**在线链接**之外，还可以是**本地添加**
  - ![](https://pic.imgdb.cn/item/669a3b4bd9c307b7e9ea9f3d.png)
  - 更多图片类型等待设置
    - ![](https://pic.imgdb.cn/item/669a41fcd9c307b7e9f09b2d.png)
  - tag页和cate页的图片是需要单独去md文件里配置的
    - ![](https://pic.imgdb.cn/item/669a42cbd9c307b7e9f133dd.png)

- 置顶文章
  - ![](https://pic.imgdb.cn/item/669a46ddd9c307b7e9f54d5b.png)

- 文章封面

  - butterfly里统一设置

    - cover:
      - 后面进行一系列配置

    - default_cover
      - 可以设置多张默认封面，如果文章没有单独设置封面则会进行随机选择

  - > 文章封面的獲取順序 Front-matter 的 cover > 配置文件的 default_cover > false

  - 每个文章在开头单独设置cover


- 版权
  - 统一设置
    - 主题配置文章里打开Copyright
  - 文章单独设置
    - 每个文章开头可以单独设置，比如这篇是转载的，就可以把copyright关起来

- 目录
  - toc
  - ![](https://pic.imgdb.cn/item/669b3e59d9c307b7e9f9e2a7.png)
  - 同样也是可以单独设置文章
    - 在你的文章md文件的頭部，加入toc_number和toc，並配置true或者false即可。
- 相关文章推荐
  - related_post
  - 根据tag推荐
- 头像
  - avatar

- 阅读模式 夜间模式

- 图片文字描述
- footer 页脚定义文件

之后更多的请参考官方文档，懒得记了

# 待定的

- 部署到服务器上
- 待解决问题
  - 无法显示latex公式