## 印象博客2.0.0使用说明书


### 1.环境搭建

1. 数据库（MySQL）
	- 数据库版本要求：5.6.17
	- 设置数据库的字符码为UTF-8编码，否则会出现乱码错误；
	- 在数据库中执行压缩包中的数据库文件（noteBlog2.0.sql），建立数据库

	在数据库控制台执行下面的语句如果结果相同，则数据库配置完成




2. Tomcat
	- Tomcat版本要求：8.0.33
	- 确保Tomcat可以正常使用，删除Webapps文件夹下的自带的ROOT文件夹。
	- 把war包拷贝到Webapps文件夹下，启动Tomcat，等待一小段时间可以发现Webapps文件夹下出现ROOT文件夹。则Tomcat配置完成。


### 2. Token 获取
因自己的API权限印象笔记官方暂时没有开通,故只能利用其它应用的Token问题解决地址:
[获取Token][1]


### 3.配置文件的配置详解
配置文件位置ROOT\WEB-INF\classes目录下的config.properties文件，使用文本编辑器打开，其内容如下：
```
#NoteBlog_Version=2.0
###YINGXIANG BEGIN###
token=
NoteBookName=
###YINGXIANG END###

###DATABASE BEGIN###
projectName=ROOT
db_name=jdbc:mysql:///noteblog2.0
db_user=root
db_passwd=12345678
db_driver=com.mysql.jdbc.Driver
###DATABASE END###

###tctip CONFIG BEGIN###
headText=何不请我喝杯咖啡(^_^)
siderText=公告和打赏
#为保持开源协议请不要修改下面链接
buttomLink=https://github.com/greedying/tctip  
notice=没有公告
###tctip CONFIG END###

###COMMENT BEGIN###
appid=
conf=
###COMMENT END###

###GoogleAnalytics BEGIN###

UA=

###GoogleAnalytics END###

###ALI Graphy BEGIN###
aliLink=http://at.alicdn.com/t/font_403793_fbpt7m692fdy4x6r.css
###ALI Graphy END###

###INDEX CONFIG BEGIN###
jumbotronHead=HWT Blog
###INDEX CONFIG END###

###BACKGROUND COLOR CONFIG BEGIN###
siteColor=#17d684
secondColor=#b7ffbe
###BACKGROUND COLOR CONFIG END###
```

1. YINGXIANG：印象笔记用户认证
**token**：印象笔记令牌，整个系统的身份标识
**NoteBookName**：用于分享的笔记本名，如果不填，默认为印象笔记的默认笔记本
2. DATABASE：数据库连接配置
**db_name** ：用于系统进行JDBC连接的数据库名字
**db_user**：用于系统进行JDBC连接的数据库用户名
**db_passwd**：用于系统进行JDBC连接的数据库密码
3. tctip CONFIG：打赏插件
**headText**：顶部信息
**siderTex**：边部信息
**notice**：公告

4. COMMENT：畅言评论
**appid**：畅言APPID
**conf**：畅言设置
一般开通畅言之后会产生一段代码用于开发，选取红框中的值复制到配置文件即可如图：

![畅言代码][2]

5. GoogleAnalytics  ：谷歌分析
**UA**：用于识别网站的代码

6.  tctip CONFIG：打赏插件
一般不用修改其中的属性，但是要把自己的二维码图片放到合适的位置，即`ROOT\static\tctip\img\qr`目录下，注意要将更改过后的图片文件名必须和该目录下的文件名相同。如果图片显示不清，可以利用修图软件对图片进行尺寸剪切。


7. INDEX CONFIG ：首页
**jumbotronHead**：博客头巨幕文字

8. BACKGROUND COLOR CONFIG ：背景主题色修改
**siteColor**：系统主色调
**secondColor**：系统辅色调
在此给出几种系统色调搭配仅供参考，详情参照附录。


***注意：为保证该版本系统的正常运行，未在上述描述中出现的属性，请不要擅自修改。***
### 4. 服务的启动

- 启动Tomcat,过一段时间可看到解压的ROOT文件夹
- 访问`127.0.0.1:端口号`  ,例如127.0.0.1:8080
- 访问`127.0.0.1:端口号/admin` 可启动同步服务，例如：`127.0.0.1:8080/admin`

注意：如果是外网控制，把`127.0.0.1:端口号`换成网站对于的域名即可，例如：`http://hwtblog.cn/admin`




### 5.附录

主题设置：
- 印象绿：

![印象绿][3]
``` 
siteColor=#17d684
secondColor=#b7ffbe
```
- 中国红：

![中国红][4]

``` 
siteColor=#d61717
secondColor=#e4e2e2

```
- 天空蓝

![天空蓝][5]

```
siteColor=#5ec5ea
secondColor=#fbfbfb
```

- 极客黑

![极客黑][6]

``` 
siteColor=#353535
secondColor=#fbfbfb
```
- 优雅紫

![优雅紫][7]

``` 
siteColor=#c9a9de
secondColor=#fbfbfb
```


  [1]:https://github.com/suziwen/blogxiaoshujiang/blob/master/2017-9-17%20%E5%85%B3%E4%BA%8E%20Evernote%28%E5%8D%B0%E8%B1%A1%E7%AC%94%E8%AE%B0%29%20%E5%81%9C%E6%AD%A2%E4%BD%BF%E7%94%A8%20Developer%20Token,%E5%B0%8F%E4%B9%A6%E5%8C%A0%E5%AE%A2%E6%88%B7%E7%AB%AF%E4%B8%8D%E8%83%BD%E7%BB%91%E5%AE%9A%E7%9A%84%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88.md
  [2]: ./images/1513847588397.jpg
  [3]: ./images/1513850271999.jpg
  [4]: ./images/1513850227729.jpg
  [5]: ./images/1513850445391.jpg
  [6]: ./images/1513850652896.jpg
  [7]: ./images/1513850787235.jpg