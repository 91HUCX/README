#弹幕+聊天室——barrage


##一.barrage接入

###barrage是做什么的？
barrage是为视频播放终端提供弹幕服务。 包括添加弹幕、获取弹幕信息。详情见[点播弹幕接API](https://gitlab.lilinlin.science/java/barrage/blob/master/doc/%E7%82%B9%E6%92%AD%E5%BC%B9%E5%B9%95API_v1.0.0_20161202.docx)

###快捷部署（运维同学请看）
a.需要的环境

```
1、tomcat7+jdk1.7.0.79
2、redis3.0以上
3、mysql数据库
```
b.需要依赖的系统

```
无
```
c.数据库初始化

```
1、新建数据库（barrage），导入git更目录sql下面的sql脚本
2、新建数据库（grope_quartz），配置到quartz_data.properties配置文件中
```
d.需要配置的配置文件说明

```
1、WEB-INF/classes/config.properties，具体配置见文件中的注释
2、WEB-INF/classes/dataSource.xml，多数据源的配置。 不依赖多租户
3、WEB-INF/classes/jdbc_data.properties，数据库的配置
4、WEB-INF/classes/quartz_data.properties，集群定时器的数据库配置
5、WEB-INF/classes/redis_data.properties，redis的配置
```
e.启动tomcat，并查看日志文件时候有错误信息

```
tail -f /usr/local/tomcat/logs/catalina.out
```
f.如何查看服务是否启动成功

```
在浏览器中访问http://127.0.0.1:8080/barrage
会有“Hello barrage”字样	
注意：IP和端口以实际情况为准
```

##二.聊天室接入

###聊天室简介
聊天室接入的底层是融云提供的服务，在融云的基础上，做的接口封装。其他系统接入请参考：[聊天室接入API](https://rap.lilinlin.science/workspace/myWorkspace.do?projectId=14#417) 。

###快速部署（运维同学请看）

a.数据库初始化

```
1.新建数据库（chatroom），建表初始化数据见sql目录中chatroom-base.sql文件
#创建聊天室数据库
create database chatroom;
```

b.需要配置的配置文件说明

```
WEB-INF/classes/jdbc_data.properties，数据库的配置
WEB-INF/classes/config.properties，具体配置见文件中的注释(修改头像地址)

```