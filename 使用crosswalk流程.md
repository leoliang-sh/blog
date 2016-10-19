##使用crosswalk流程
###一、`ionic browser add crosswalk`

运行此命令后，目录做了以下更改

1. 目录会添加engine文件夹；
2. 目录会修改一下文件：
	* package.json
	* ionic.project
	* config.xml
3. 添加了android platform

###二、`gulp -b`
此命令会编译app目录中的文件到www中，以便后面执行ionic命令
>ionic 命令是针对www目录的

###三、`ionic build android`
此命令会调用cordova的相关命令对进行Android打包。由于添加了crosswalk的缘故。编译出了两个apk文件：

* platforms/android/build/outputs/apk/android-x86-debug.apk
* platforms/android/build/outputs/apk/android-armv7-debug.apk

前者是针对x86架构的设备的，后者是针对arm架构的设备的。一般情况下我们手机是arm架构的。

apk中包含了crosswalk的浏览器引擎所以会比android webview打包大15M左右。