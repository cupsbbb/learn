#Java 的代理文件
###处理支持Java代理 [download](https://github.com/Esri/resource-proxy)

* 访问跨域资源
* 请求超过2048个字符
* 访问基于令牌认证保护的资源。
* OAuth 2.0应用登录。
* 启用日志记录
* 这两种资源和客户端基于IP限速

###说明
* 下载并解压缩.zip文件或 clone the repository。你可以下载一个发布的版本（推荐）或最新的每日构建。
* 安装Java的文件夹中的内容在Web容器，如Apache Tomcat上一个Web应用程序。
* 测试该代理已安装并可用：

```
http://[yourmachine]:8080/Java/proxy.jsp?ping
```

* 测试代理能够直接使用浏览器转发请求：

```
http://[yourmachine]:8080/Java/proxy.jsp?http://services.arcgisonline.com/ArcGIS/rest/services/?f=pjson
```

* 编辑proxy.config文件中的文本编辑器来设置代理服务器的配置设置。
* 更新您的应用程序使用代理指定的服务。在这个JavaScript示例要求到route.arcgis.com将利用代理服务器。

```java
    urlUtils.addProxyRule({
        urlPrefix: "route.arcgis.com",
        proxyUrl: "http://[yourmachine]:8080/Java/proxy.jsp"
    });
```

* 安全提示：默认情况下，proxy.config允许任何引用。要锁定下来，用自己的应用程序URL替换allowedReferers属性*。

###文件夹和文件
代理包括以下文件：

* proxy.jsp：实际的代理应用程序。在大多数情况下，你不需要修改此文件。
* WEB-INF /classes/ proxy.config：此文件包含代理的配置设置。在这里，您将定义所有将使用代理服务器的资源。更新此文件后，需要重新启动或更新您的Web容器的代理应用程序。重要提示：为了使您的凭据安全，确保在浏览器中的Web服务器时，不会显示proxy.config内的文本（即：HTTP：// [yourmachine]：8080/Java/proxy.config）。

###要求
* Java 6或更高

###问题

发现了一个错误或者需要一个新功能？让我们通过提交一个问题知道了。

###特约

所有捐款都欢迎。

###许可

版权所有2014年ESRI的

在Apache许可2.0版（简称“许可证”）;你可能不使用这个文件除了在遵守许可。您可以在http://www.apache.org/licenses/LICENSE-2.0获得许可证的副本

除非适用法律要求或书面同意，根据许可证分发的软件是基于“按原样”的基础，没有担保或任何形式的条件，明示或暗示的保证。请参阅下许可特定语言的管辖权限和限制许可。