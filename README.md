VeekXT 的个人主页

url: <http://gh.veekxt.com>

记录一些乱七八糟的东西

目录结构：

```
/
├── category        #分类页面
├── category_date   #按日期分类页面
├── css_js          #css样式和js
├── _includes       #整站的各个部分
├── _layouts        #各种页面的模板
├── media           #图片等文件
│   ├── png
│   └── svg
├── mine            #我的杂项页面，个人垃圾
│   └── xxx
├── other           #其他
│   ├── about       #关于
│   ├── friend_link #友链
│   ├── pic         #图片
│   ├── rss         #rss订阅页面
│   └── tell_me     #留言
└── _posts          #所有文章

_includes目录文件
.
├── category_date.html  #侧栏日期分类框
├── category.html       #侧栏目录分类框
├── comments.html       #多说评论插件
├── footer.html         #页脚
├── head.html           #head标签
└── nav.html            #导航栏

_layouts目录文件
.
├── default.html        #模板：包含导航条和页脚
├── list.html           #模板：继承自default，包含侧栏两种分类和主体（应是一个列表）
├── mine.html           #模板：继承自default，包含侧栏杂项列表和主体
├── page.html           #模板：继承自default，包含侧栏两种分类和主体（应是一篇文章）
└── post.html           #模板：继承自page，在page基础上增加了上一篇及下一篇链接

```

veekxt

2015-10-27
