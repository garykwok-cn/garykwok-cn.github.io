---
layout:     post
title:      将jar包作为windows service运行
subtitle:   java
date:       2020-08-25
author:     Gary Kwok
header-img: img/java.png
catalog: true
tags:
    - java
    - jar
    - windows service
---
## 前言
> 有时候我们开发的java程序不得不要在windows系统上运行（比如：顺丰提供的打印sdk，为了能调用打印机直接打印，不得不将其运行在windows系统上）  
>
> 仅仅只是在运行起来是容易的，只需要安装jdk，配置好环境变量后即可使用 java -jar xxx.jar 将其运行起来。
>
> 但是为了在系统重启后不用手动去启动它，我们需要将其作为windows服务，服务器开机后即可自动运行。
   

## 1. 将程序打包成jar
``在maven中打包``


## 2. 从github上下载winsw
> 可以根据系统版本情况下载对应的exe
>

地址： <https://github.com/kohsuke/winsw/releases>


## 3.配置xml
> 上面已经提到，这里的xml文件名必须与WinSW.exe一致

```xml
<service>
     <id>服务名称</id>
     <name>服务的显示名称</name>
     <description>服务说明</description>
     <!-- java环境变量 -->
     <env name="JAVA_HOME" value="%JAVA_HOME%"/>
     <!---->
     <executable>java</executable>
     <arguments>-jar "E:\springboot\test.jar"</arguments>
     <!-- 启动方式：Boot，System，Automatic或Manual -->
     <startmode>Automatic</startmode>
     <!-- 日志配置 -->
     <logpath>%BASE%\log</logpath>
     <logmode>rotate</logmode>
 </service>
```
## 4.安装服务

``打开命令行窗口，定位到jar同级目录``   

``执行 WinSW.exe install命令``






