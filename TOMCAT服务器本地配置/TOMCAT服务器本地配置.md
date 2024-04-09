# TOMCAT服务器的本地配置

## 以TOMCAT9.0.84为例

### 一、资源获取

​		首先登录网站链接 **https://tomcat.apache.org/** 可直达Tomcat服务器的下载界面，如图1，选择合适的版本，点击download进入对应页面，再点击64-bit Windows.zip便可下载到对应版本的压缩包。

![](.\Tomcat_p1.PNG)

<center>图1：Tomcat下载网页</center>

![](.\Tomcat_p2.PNG)

<center>图2：Tomcat9下载网页</center>

​		需要注意，目前Tomcat9已经更新到9.0.87版本，由于Tomcat9最低支持java8，所以如果自己的电脑所搭载的java版本是java8，就只能下载Tomcat9或者Tomcat8版本。因本人已下载过Tomcat9.0.84版本和Tomcat8.5.97版本，此处不再次下载。

### 二、环境变量配置

​		把已完成下载的压缩包进行解压缩，就可以进入下一步：环境变量配置。对于Win10系统而言，打开设置->系统->关于->高级系统设置->环境变量，在系统变量中，添加环境变量如下：

```java
变量名：CATALINA_HOME
变量值：E:\apache-tomcat-9.0.84-windows-x64\apache-tomcat-9.0.84/*个人示例，此处设为自己的Tomcat文件所存放的地址*/
```

​		然后在系统变量中的`path`变量进行编辑，添加上该条变量

```java
%CATALINA_HOME%\bin
```

​		至此，环境变量配置完成。

### 三、中文编码文件配置

​		完成变量配置后，由于Win10的cmd默认的中文编码是GBK，而Tomcat默认的中文编码是UTF-8，所以需要进行中文编码格式的修改，否则命令行界面会出现中文乱码。打开文件如下，其中路径为自己的Tomcat文件所存放的地址，找到文件夹`conf`当中的`logging.properties`，用记事本打开，找到图3所在的位置。

```
`E:\apache-tomcat-9.0.84-windows-x64\apache-tomcat-9.0.84\conf\logging.properties`
```

​		![](.\ziti_p1.PNG)

<center>图3：命令行界面中文编码格式设置文件</center>

​		将`java.util.logging.ConsoleHandler.encoding = UTF-8` 当中的`UTF-8`修改成`GBK`，如图4所示。

![](.\ziti_p2.PNG)

<center>图4：命令行界面中文编码格式设置文件</center>

### 四、启动本地服务器

​		以上步骤完成后，便可打开cmd（win+r 输入cmd）进行测试。输入指令名为

```
startup.bat
```

​		便可启动本地Tomcat服务器，效果如图5，注意保持该界面开启或最小化，不要关闭，否则服务器将关闭，网页将无法显示。

![](.\cmd_p1.PNG)

<center>图5：Tomcat服务器的启动</center>

​		打开浏览器，由于Tomcat的默认端口是8080，在浏览器输入网址`127.0.0.1:8080`，会出现如图6的界面。

![](.\p6.PNG)

<center>图6：Tomcat服务器的启动</center>

​		至此，Tomcat服务器的本地配置就完成了。