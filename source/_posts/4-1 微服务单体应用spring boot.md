---
title: 4-1 微服务单体应用spring boot
category: 微服务
tag: 微服务架构
date: 2017-04-05
---
> Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run". We take an opinionated view of the Spring platform and third-party libraries so you can get started with minimum fuss. Most Spring Boot applications need very little Spring configuration.
Spring Boot让你更容易地创建“仅仅运行”就可以的独立，产品级的基于Spring的应用。

<!--more-->
特点：
- 创建独立的Spring应用
- 直接内嵌Tomcat，Jetty或者Undertow
- 提供固执的'starter' POMs来简化你的Maven配置
- 尽可能自动配置Spring
- 提供为生产准备的特性例如度量，健康检查和外化配置
- 绝对没有代码生成和不需要XML配置
### 快速入门 ###
先看一下官方“Quick Start”的例子。
** 环境需求：**
检查java和maven已经安装，并且版本有效
```
$ java -version
java version "1.8.0_102"
Java(TM) SE Runtime Environment (build 1.8.0_102-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.102-b14, mixed mode)
```
```
$ mvn -v
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T16:41:47+00:00)
Maven home: /usr/local/Cellar/maven/3.3.9/libexec
Java version: 1.8.0_102, vendor: Oracle Corporation
```
** 开发步骤：**
将以下配置文件复制到maven工程的pom.xml配置文件里（gradle文件用来创建gradle工程的build.gradle），
`.pom`
```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.5.2.RELEASE</version>
</parent>
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```
`.gradle`
```gradle
dependencies {
    compile("org.springframework.boot:spring-boot-starter-web:1.5.2.RELEASE")
}
```
新建hello/SampleController.java
```java
package hello;

import org.springframework.boot.*;
import org.springframework.boot.autoconfigure.*;
import org.springframework.stereotype.*;
import org.springframework.web.bind.annotation.*;

RestController
EnableAutoConfiguration
public class SampleController {

    @RequestMapping("/")
    @ResponseBody
    String home() {
        return "Hello World!";
    }

    public static void main(String[] args) throws Exception {
        SpringApplication.run(SampleController.class, args);
    }
}
```
在项目根目录下运行命令mvn spring-boot:run就可以启动应用。
```
$ mvn spring-boot:run

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v1.5.2.RELEASE)
....... . . .
....... . . . (log output here)
....... . . .
........ Started Example in 2.222 seconds (JVM running for 6.514)
```
打开浏览器访问`localhost:8080`应该可以看到以下输出：
```
Hello World!
```
键入`ctrl-c`可以优雅的退出应用。
为了创建一个可执行的jar，需要添加`spring-boot-maven-plugin`到` pom.xml`。插入一下几行到`dependencies`。
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```
保存pom.xm，然后从命令行运行`mvn package`：
```
$ mvn package

[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building myproject 0.0.1-SNAPSHOT
[INFO] ------------------------------------------------------------------------
[INFO] .... ..
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ myproject ---
[INFO] Building jar: /Users/developer/example/spring-boot-example/target/myproject-0.0.1-SNAPSHOT.jar
[INFO]
[INFO] --- spring-boot-maven-plugin:2.0.0.BUILD-SNAPSHOT:repackage (default) @ myproject ---
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
```
在`target`目录下会生成`myproject-0.0.1-SNAPSHOT.jar`，文件大约有10M。如果想一探究竟，可以执行`jar tvf`:
```
$ jar tvf target/myproject-0.0.1-SNAPSHOT.jar
```
应该也能看到在`target`目录下的`myproject-0.0.1-SNAPSHOT.jar.original`。那是Maven之前创建的jar文件。
实现一个服务就是这么简单，接下来让我们看一看到底Spring Boot框架是怎么执行的，原理是什么。
### 深入理解 ###
首先，pom文件里通过使用`spring-boot-starter-web`模块依赖来快速启动运行。
`@RequestMapping`注解提供路由信息，告诉Spring任何的“／”路径下的HTTP请求都会映射到`home`方法。
`@RestController`注解告诉Spring渲染结果字符串回到调用者。
`@EnableAutoConfiguration`注解告诉Spring Boot根据添加的jar依赖，“猜测”你打算如何配置Spring。由于`spring-boot-starter-web`添加了Tomcat 和Spring MVC，自动配置会假设你要开发一个web应用并建立相应的Spring。
`main`方法是java规范的标准入口，它会代理到Spring Boot的`SpringApplication`类的`run`方法。`SpringApplication`会引导应用程序，启动Spring，依次启动自动配置的tomcat服务器。也可以传递`args`来暴露任何的命令行参数。
总之，我们可以认为整个的Spring Boot应用的运行主要包括两个阶段：
1. 以`main`方法为入口，进行自动配置初始化。
2. 一旦初始化完成，controller会拦截HTTP请求，并通过mapping配置，把请求转发到相应方法。
