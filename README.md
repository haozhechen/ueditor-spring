# ueditor-spring

[![License](https://img.shields.io/badge/license-Apache%202-4EB1BA.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)


This project integrates the UEditor into SpringMVC project which also replaces the old json lib with the swanky fastjson lib(this will improve the speed definitely). Please star it if u think it's useful, thanks. 

该项目整合了百度UEditor与SpringMVC，并且将UEditor JAVA源码中的json处理库替换为阿里的fastjson，提高了运行速度。该项目配置简单，只需要将其源码下载并添加到项目中即可进行整合。如有问题请在issues中留言或者留下邮箱，我将抽时间一一解答。

## Getting started / 开始使用

Firstly, you need to add fastjson dependency in yout pom.xml, in my project I use version 1.2.39, you can specify any version you like.

首先在maven中添加fastjson依赖，在该项目中我使用的是1.2.39，你可以替换成你喜欢的任意版本

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.39</version>
</dependency>
```

Then, clone the *baidu(src\main\java\com\baidu)* folder into your project. 

接下来将 *baidu(src\main\java\com\baidu)* 文件夹放置到您的项目中

Next create a controller in your project.

在您的Spring项目里新建一个Controller

```java
@Controller
@RequestMapping(value="/ueditor")
public class UEditorController {
	
	 /**
	 * UEditor 入口方法
	 * 
	 * @param request
	 * @param response
	 */
	@RequestMapping("/init")
	    public void index(HttpServletRequest request, HttpServletResponse response) {
	     
		 try {
	            request.setCharacterEncoding("utf-8");
	            response.setHeader("Content-Type", "text/html");
	            String rootPath = request.getServletContext().getRealPath("/");
	            response.getWriter().write(new ActionEnter(request, rootPath).exec());
	        } catch (Exception e) {
	            e.printStackTrace();
	        }
	    }

}
```

Ensure *config.json* is placed in your classpath since the controller created above will read the relative path.

然后确保 *config.json* 放置在项目的classpath中（因为controller会读取相对路径，本例放置在resource目录下）。

Below is the explaination of the *config.json* , replace it as yours.

下面是 *config.json* 配置，替换成您的配置即可

```json
{  
    "imageActionName": "/fileupload/images",
    "imageFieldName": "file", 
    "imageMaxSize": 2048000,
    "imageAllowFiles": [".png", ".jpg", ".jpeg", ".gif", ".bmp"],
    "imageCompressEnable": true,
    "imageCompressBorder": 1600, 
    "imageInsertAlign": "none", 
    "imageUrlPrefix": "/RootPath/", ==>项目根地址，如www.example.com/RootPath中，RootPath即为根地址
    "imagePathFormat": "/upload/images/" ==>图片上传方法地址
}  
```

Next put all the files from webapp folder into your web app root directory, now your project structure should be：

接下来，将webapp文件夹下的UEditor静态资源放置到您web项目根目录下，此时项目结构为：

```
project root
│
└───java
│   └───main
│       └───com
│           └───baidu
│               └───ueditor
│                   │   define
│                   │   hunter
│                   │   ......
└───resources
│       │   config.json
└───webapp
│       │   
│       └───ueditor
│            │   dialogs
│            │   lang
│            │   themes
│            │   ......
```

