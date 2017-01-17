# Android笔记


### 1、Android Studio gradle 升级遇到的问题

 ![](https://ww2.sinaimg.cn/large/006y8lVagw1fbsh5tkko8j315o05gtaj.jpg)
 
 碰到这种情况，修改工程目录 /gradle/gradle-wrapper.properties文件里的
 distributionUrl=https\://services.gradle.org/distributions/gradle-2.14.1-all.zip   问题即可解决
 
 
### 2、Android 偶尔用却又容易忘记的快捷键：
 
 
 	1、重命名   alt+shift+R
 
	2、大小写切换   crt+shift+U
	
	
### 3、android 打包签名（应用市场提交app需要加固,加固的apk需要下载下来重新签名）

如何签名
jarsigner -verbose -keystore [keystorePath] -signedjar [apkOut] [apkIn] [alias]
jarsigner命令格式：-verbose输出详细信息 -keystore密钥库位置 -signedjar要生成的文件 要签名的文件 密钥库文件
keystorePath参数代表keyStore的绝对路径，如D:\keystore
apkOut参数代表签名后的apk路径，如D:\signed.apk
apkin参数代表在腾讯应用中心下载的未签名apk，默认名称为tap_unsign.apk
alias参数代表签名用的整数名称（创建keyStore时所填写），如 key


example:
jarsigner -verbose -keystore /Users/tanghui/AndroidStudioProjects/cloudcampus_android_gitlab/cloudcampus/keyStore/cloudcampus.jks -signedjar /Users/tanghui/huihui/signed.apk /Users/tanghui/Downloads/TestSign.apk  key


### 4、Android studio gradle 问题

Error:Could not read entry ':cloudcampus:processDevelopDebugManifest' from cache taskArtifacts.bin (/Users/tanghui/AndroidStudioProjects/cloudcampus_android66/.gradle/2.10/taskArtifacts/taskArtifacts.bin).
> enum constant INSTANT_RUN_REPLACEMENT does not exist in class com.android.manifmerger.ManifestMerger2$Invoker$Feature


问题描述：
Android Studio升级到2.0后，当build.gradle修改以后，会存在缓存。这时候编译就会报类似下面的错误：
 (/.gradle/2.10/taskArtifacts/taskArtifacts.bin).> enum constant INSTANT_RUN_REPLACEMENT does not exist in class com.android.manifmerger.ManifestMerger2$Invoker$Feature
 
解决方法：
删除.gradle/2.10/目录下的所有文件，然后重启Android Studio。


### 5.设置Git命令别名【git config --global alias】

可以为常见的命令起个简单的别名，就不用每次都敲完整命令，比如可以设置：
status为st，checkout为co ; commit为ci ; branch为br等

> git config --global alias.st status