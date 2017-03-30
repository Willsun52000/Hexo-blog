---
title: 知识管理Confluence
category: 微服务
tag: 基础流程
date: 2017-03-30
---
> Atlassian Confluence（简称Confluence）是一个专业的wiki程序。它是一个知识管理的工具，通过它可以实现团队成员之间的协作和知识共享。Confluence 不是一个开源软件，非商业用途可以免费使用。
Confluence使用简单，但它强大的编辑和站点管理特征能够帮助团队成员之间共享信息，文档协作，集体讨论。 目前，Confluence被用于广泛地用于项目团队，开发团队，市场销售团队。

<!--more-->
使用Confluence作为知识管理平台已经有两年时间，起初作为团队敏捷开发练习，用免费试用版搭建了一个供小团队内部联系使用。试用期只有一个月到期可以renew，接着试用。由于公司内部已经搭建了一套面向全公司所有敏捷项目的平台，作为练习拿试用版练手也无可厚非。值得强调的是针对10个账号的许可证，只需要10刀，是相当划算的，很适合开源小团队使用。但是如果25人的许可，就需要1400刀，学院教育机构可以半价。
总结我司对Confluence的使用，放置的文档有：需求定义BRD，会议纪要，API契约定义，冲刺回顾，环境配置，各种开发规范。
### Confluence基本操作
**创建一个空间**
在Confluence创建一个空间，相当于创建一个项目。具体的操作是，点击上方菜单【Spaces】-【Create space】来创建一个空间。
![Alt text](http://i4.buimg.com/589792/0fcc1f563e8075b4.png)

创建空间
弹出的对话框共有4个选项。如果是个人项目，一般选【Blank space】，可创建页面、博客；如果只需要创建页面，则选择【Documentation Space】；如果要限定团队某个成员访问的空间，则选择【Team Space】；至于【Knowledge base】与【Blank space】差不多。
因此，个人用，选【Blank space】；团队用，选【Team space】。这里选择【Blank space】。
![Alt text](http://i4.buimg.com/589792/07803eeec1eb3cf7.png)
选择空间类型
为创建的【Blank space】空白空间进行命名，【Space name】设置名称，【Space key】设置key，key是标识，填写字母即可。这个空间是个人用的话，不希望团队其它成员看到，记得勾选【Visible only to me】，即该空间仅自己可视。
![Alt text](http://i4.buimg.com/589792/1e80b543e0346fc1.png)
空间设置
**创建一个文档**
点击菜单栏上方的【Create】即可弹出创建对话框，提供了多种不同创建模板。一般三种模板就够用了，【Blank page】用以创建属于自己所需的文档；【Blog pot】可以创建从网络收藏的网页；【File list】创建一个文件网盘，可以上传各类文档、软件等。
这里选择【Blank page】空白页面创建。
![Alt text](http://i4.buimg.com/589792/ee8c1ff86a17e3e2.png)
创建空白页面
页面创建提供强大的编辑功能。以下简单介绍：
- 注意页面创建位置。比如，在首页创建页面，则该页面在首页之下。如果在首页创建了【社会心理学】页面，并进入了该页面位置，则创建的页面的父级就是【社会心理学】。了解这一点很重要，这决定了你创建的页面在哪一个位置。

- 【Page title】是页面标题，下方为页面正文。

- Ctrl+s快捷键会执行【Save】保存功能。按下该快捷键，会完成编辑操作。
![Alt text](http://i4.buimg.com/589792/8eec4022daa5ff25.jpg)
创建页面
**页面编辑**
Confluence提供了强大的页面编辑支持。下面简要介绍常用功能：
- 【Paragraph】这里的下拉选项可以设置文字格式。包括标题、引用。
- 加号处的下拉选项，提供了增强性的编辑功能。包括支持Markdown语法、支持Todo任务列表、支持多种宏等等。
- 【Table of Contents】插入目录插入目录宏，该功能可以根据你的标题格式自动生成目录。
![Alt text](http://i4.buimg.com/589792/0d187fa197e78011.jpg)
页面编辑
其中最后一项的【Other macros】提供了近100种宏模板，你可以插入PDF、图表各种各样的媒体内容。
![Alt text](http://i4.buimg.com/589792/b2e832728435da14.jpg)
丰富的宏
**页面操作**
完成编辑后可对页面进行相应的操作。点击页面右上方的【…】会显示页面操作的功能菜单。
- 【Page History】可对页面进行版本控制，回退到特定的版本。
- 【Export to Word】将页面导出为Word文档。
- 【Copy】、【Move】、【Delete】可对页面进行复制、移动、删除等操作。
![Alt text](http://i4.buimg.com/589792/93d88dae032a6508.png)
页面操作
**空间管理**
空空间管理包括对空间的配置、删除、权限等等一系列的管理。在页面左下方的【Space tools】即可进入空间管理操作。

- 【Delete Space】可将该空间删除。
- 【Permissions】对空间其它成员进行详细的权限控制设置。
![Alt text](http://i4.buimg.com/589792/ad7fd450b49d4cc5.png)
空间管理
**总结**
Confluence的功能非常之多，这里仅能介绍了常用的功能。无论对于个人还是创业公司，Confluence是真正意义上的Wiki知识管理工具。现在有很多的用户使用Evernote、为知、有道作“知识管理”，恐怕大多数的情况，这类工具仅仅是扮演着收集与采集的工具，比如我现在用的Reede应用，看到好的文章就同步至Evernote，但是，我基本不会使用evernote做笔记或者撰写材料，这是因为Evernote的形态并不符合Wiki的理念。
又由于知识以各种各样的形态呈现，比如文章、图片、视频、文档、软件等等，传统的笔记类工具远远还不足以应付。
Confluence与Evernote的区别就像图书馆与迅雷。Confluence（图书馆）存放的知识在需要的时候可以应用，且以良好的结构组织；而Evernote（迅雷）只是为了收集（收藏）内容的目的而存在，即便有一天你知道evernote有你需要的知识，但你多数用搜索引擎直接搜索。
是时候试试confluence。