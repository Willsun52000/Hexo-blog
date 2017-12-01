---
title: 4-3 主流技术框架集合JHipster
category: 微服务
tag: 微服务架构
date: 2017-04-09
---

> JHipster is a fully Open Source, widely used application generator. Easily create high-quality Spring Boot + Angular projects!

JHipster是一个完全开源，广泛使用的医用程序生成器。易于创建高质量Spring Boot + Angular项目！

<!--more-->
### 简介 ###

jhipster简单来说是一个基于nodejs+yeoman的java代码生成器。往大了说是基于java的一套微服务解决方案。请注意是一整套的微服务解决方案。jhipster在整个程序架构上都做好了整合，包括前端mvvm框架（angularjs），前端构建工具（gulp）到后端的微服务框架（spring cloud）和hibernate/mongodb，再到单元测试/ui测试。
毫不客气的说 ：学会了这套框架，你就是程序开发/程序架构界的潮男。对,hipster的意思就是：追求新奇的人。

### demo ###

下面跟着我来一步一步的来见证奇迹。
1. 安装nodejs。
2. 安装yeoman/bower/gulp 
```
npm install -g yo bower gulp-cli
```
3. 安装jhipster 
```
npm install -g generator-jhipster
```
### 生成mciroservice app ###
**生成基础架构**
cd到你想存放代码的路径，然后运行：
```
yo jhipster
```
这时候jhipster向导就会启动了，如图：
![enter image description here](http://i4.buimg.com/589792/83b1ef4864fe80f0.png)

第一个选择很重要，项目类型要选择microservice application
![enter image description here](http://i4.buimg.com/589792/243dee86cd03a09c.png)

后面的根据实际情况，选择就可以。失败了也没关系，删掉文件夹重新来过。
生成成功后运行 ./mvnw 或者gradlew下载依赖包。
**jhipster**是可以生成实体和实体的增删改查带分页的
运行
```
yo jhipster:entity <entityName>
```
来启动实体生成向导。
然后跟着向导输入信息。

### 生成microservie ###

**生成基础架构**
继续运行：
```
yo jhipster
```
第一个选择很重要，项目类型要选择*microservice gateway

**生成实体**
运行
```
yo jhipster:entity <entityName>
```
来启动实体生成向导。
然后跟着向导输入信息。

此处需要注意：
1. 询问是否选择存在的app时 选择是
2. <entityName>需要时在app中生成过的

### 运行 jhipster registry ###
jhipster registry是一个基于spring cloud的配置中心，jhipster的微服务架构依赖此程序。
1. 从github下载源码https://github.com/jhipster/jhipster-registry
2. cd 到解压目录 然后运行 ./mvnw或者gradlew 启动应用

运行效果如下
![enter image description here](http://i4.buimg.com/589792/81a5a3e31c2a8de3.png)

这个时候就可以启动app和gateway了。
cd到刚才存放microservice app的目录 运行./
cd到刚才存放microservice gateway的目录 运行./mvnw
然后打开浏览器见证奇迹
![enter image description here](http://i4.buimg.com/589792/0d261e364d86d134.png)
![enter image description here](http://i4.buimg.com/589792/e46890436e9755a3.png)
![enter image description here](http://i4.buimg.com/589792/737ab016b37e90a4.png)
![enter image description here](http://i4.buimg.com/589792/97e11cdaf73534d0.png)
