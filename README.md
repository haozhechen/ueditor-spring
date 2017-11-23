# ueditor-spring

This project integrates the UEditor into SpringMVC project which also replaces the old json lib with the swanky fastjson lib(this will improve the speed definitely). Please star it if u think it's useful, thanks. 

该项目整合了百度UEditor与SpringMVC，并且将UEditor JAVA源码中的json处理库替换为阿里的fastjson，提高了运行速度。该项目配置简单，只需要将其源码下载并添加到项目中即可进行整合。如有问题请在issues中留言或者留下邮箱，我将抽时间一一解答。

#Get started
#开始整合

Firstly, you need to add fastjson dependency in yout pom.xml, in my project I use version 1.2.39, you can specify any version you like.

首先在maven中添加fastjson依赖，在该项目中我使用的是1.2.39，你可以替换成你喜欢的任意版本

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.39</version>
</dependency>
```

#即将更新
