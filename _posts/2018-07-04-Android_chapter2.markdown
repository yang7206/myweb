---
layout: post
title:  "第二章.整装起航--Android的HelloWorld"
date:   2018-07-04 22:33:17 -0400
categories: Android
---
    
Android的HelloWorld主要包含以下几部分：

    一.创建第一个项目
    二.运行项目
    三.Android项目的项目结构说明

## 一.创建第一个项目

### 1.创建应用

启动Android Studio，在欢迎页面点击`Start a new Android Studio project`开始创建项目。

![项目创建](/img/chapter2/new_proj.png "项目创建")


![项目创建](/img/chapter2/new_proj1.png "项目创建")

输入框中需要输入以下信息：

    Application name        表示项目的名称
    Company domain          公司域名，Android Studio将用来生成唯一标识符
    Project location        项目存放位置，不存在则会进行自动创建
    Package name            项目的包名，即唯一标识符
    Include C++ support     是否引入C++支持
    Include Kotlin support  是否引入Kotlin支持

***图中的Application name，Android Studio会创建以该项目为名称的文件夹， 同时以Application name作为初始的应用名称（后期可以在项目中更改)***

***图中的Company domain ，Android官方建议以公司域名作为项目的唯一标识符，Android Studio会将该字符反转然后加上项目名称生成Package name。***

***图中的Package name ，项目的包名，作为项目的唯一标识符，类似APP的身份证号，Package name不可重复，同一个设备只能安装一个相同Package name的APP，如需要更改，可在项目中进行更改***

***图中的Include C++ support ，表示是否引入C++支持，如果需要进行NDK开发，才需要勾选，勾选后Android Studio会生成CMAKE编译相关的文件和代码，默认不勾选，本文不需要C++，不勾选，如有需要可以后期配置***

***图中的Include Kotlin support ，表示是否引入Kotlin支持，Kotlin目前已经作为Android开发的官方语言，与JAVA可100%兼容，但现在我们暂时使用JAVA开发，暂时不需要Kotlin支持，如有需要可以后期配置***
    

点击`Next`，需要选择最低版本的SDK，这里使用默认配置勾选`Phone and Tablet`，选择`API 15`即可，（API 15为4.0.3目前已经可以覆盖基本100%的设备，所以没必要向更低版本进行支持了），再次点击`Next`

![预制模板](/img/chapter2/new_proj2.png "预制模板")

上图中为官方的预制模板，可以使用官方预制模板，也可以自行创建文件，这里依然使用默认配置`Empty Activity`模板生成初始的带一个`Activity`的项目，点击`Next`

![生成文件](/img/chapter2/new_proj3.png "生成文件")

    Activity Name               Activity名称
    Generate Layout File        是否生成布局文件
    Layout Name                 布局文件名称
    Backwards Compatibility (AppCompat)    是否向低版本兼容


***Activity：Android中使用Activity来表示一个页面，一个Activity可以看做是一个页面，一个项目（Application）可以有多个页面（Activity），不同Activity之间可以互相跳转，或进行数据传递。***

***Layout File：Android中使用XML文件来展示一个页面布局，一用XML布局文件、Activity书写代码的形式来隔离UI与代码，每个Activity可以加载一个XML文件来渲染页面布局。***


回到上图，点击`Next`，Android Studio会下载需要的组件，点击`Finish`进入主界面。

在此处创建项目并下载组件过程中，如果没有配置`Gradle`和镜像源可能会因为`Gradle`或组件无法下载而导致卡住，可以参考[·第一章.万事开头难--Android开发环境搭建·]('http://www.yangxy.cn/android/2018/07/03/Android_chapter1.html')配置`Gradle`和设置镜像源，重新启动即可。

### 2.主界面构建

进入主界面后，等待Android Studio索引及构建完成，等待右下角进度条完成。


![主界面](/img/chapter2/proj_main.png "主界面")

此时可以看到Android Studio可能会报以下错误：

    Error:Failed to find Build Tools revision 27.0.3
    Install Build Tools 27.0.3 and sync project

![构建错误](/img/chapter2/main_err.png "构建错误")

***此错误是由于Gradle没有找到配置中对应的`Build Tools Version 27.0.3`的版本***

解决此问题有两种方法：

- 直接点击`Install Build Tools 27.0.3 and sync project`下载27.0.3版本，下载完成后会Android Studio会自动刷新并重新构建

- 点击右上角Android弹出下拉菜单，选择`Project`将项目切换为`Project`结构模式，展开文件夹结构找到并打开`HelloWorld/app/build.gradle`文件，
将`buildToolsVersion`（如果不存在直接添加即可）后面的版本号改为Android SDK中的`build-tools`文件夹下面的版本号，然后再次点击`Try Again`即可重新构建，如下图：


![解决错误](/img/chapter2/main_re.png "解决错误")

***到此，第一个项目已经创建成功了***


## 二.运行项目

### 1.使用模拟器运行项目

Android模拟器可以支持大部分APP，如果涉及到传感器等硬件相关的需要，可能需要使用真机进行调试，HelloWorld项目暂不需要硬件相关的东西，可以使用模拟器运行。

***创建模拟器主要有一下两种方式：***

- 可以在点击绿三角图标，在弹出框中点击`Create New Virtual Device`创建模拟器。

    ![创建模拟器](/img/chapter2/create_m.png "创建模拟器")
    
    ![创建模拟器](/img/chapter2/create_m1.png "创建模拟器")
    
    此处下载Android 7.0版本，点击名称后面的`Download`进行下载，在弹出框中点击`Accept`按钮，然后点击`Next`进行下载
    ![创建模拟器](/img/chapter2/create_m2.png "创建模拟器")
    
    模拟器文件较大，需要等待一段时间下载完成。
    
    ![创建模拟器](/img/chapter2/create_m3.png "创建模拟器")
    
    下载完成后，选择下载的设备点击`Next`，在`Verify Configuration`页面如需改名，在AVD Name输入名称即可，本章使用默认配置，点击`Finish`，
    
    ![创建模拟器](/img/chapter2/create_m4.png "创建模拟器")
    
    此时会在`Select Deployment Target`弹出框中的`Available Virtual Devices`选项中多出我们刚才创建的虚拟机，选中点击`OK`即可运行APP了。

- 也可以点击手机图标，打开ADV 打开Android 模拟设备管理器，点击左下角`Create Virtual Device`进行下载安装，步骤同第一种步骤相同，此处不再赘述。
    
    ![创建模拟器](/img/chapter2/create_m5.png "创建模拟器")

模拟器安装完成

### 2.运行项目
    
点击绿三角图标![运行](/img/chapter2/tran.png "运行")，选择刚才创建的虚拟器，点击`OK`，等待虚拟机启动完成，Android Studio会自动运行APP

![运行项目](/img/chapter2/app.png "运行项目")

### 3.使用真机运行项目

使用Android手机需要先开启开发者模式，大部分手机开启开发者模式流程为：打开设置--系统--关于手机--连续点击内核版本号--直到弹出提示你现在处于开发者模式--设置页出现开发者选项（不同手机可能有所不同，可以自行搜索相关手机需要打开开发者选项）。

以下以华为P10为例：

![开启开发者模式](/img/chapter2/real_phone.png "开启开发者模式")

![开启开发者模式](/img/chapter2/real_phone1.png "开启开发者模式")

![开启开发者模式](/img/chapter2/real_phone2.png "开启开发者模式")

![开启开发者模式](/img/chapter2/real_phone3.png "开启开发者模式")


进入开发者选项后，开启`USB调试`选项

![开启开发者模式](/img/chapter2/real_phone4.png "开启开发者模式")

然后将设备插入电脑，连接后选择`MTP`，如果第一次可能设备会弹出需要调试设备授权，点击确定即可

![开启开发者模式](/img/chapter2/real_phone5.png "开启开发者模式")

![开启开发者模式](/img/chapter2/real_phone6.png "开启开发者模式")

此时Android Studio的`Logcat`的设备选择列表就会列出设备，并且会有日志输出。

![开启开发者模式](/img/chapter2/real_phone7.png "开启开发者模式")

此时同样点击绿三角，在设备选择弹出框中的`Connected Devices`列表下选择真机设备，点击OK即可运行APP在真机

点击`Logcat`框的左侧栏相机按钮，可以获取屏幕快照

![运行APP](/img/chapter2/real_phone8.png "运行APP")


至此，APP已成功运行。

## 三.Android项目的项目结构说明

### 1.Android Studio面板说明

![Android Studio面板](/img/chapter2/as.png "Android Studio面板")

使用左侧面板栏的Project/Structure可以切换并显示项目文档结构和当前编辑文件的结构

![Android Studio左侧面板栏](/img/chapter2/as1.png "Android Studio左侧面板栏")

![Android Studio左侧面板栏](/img/chapter2/as2.png "Android Studio左侧面板栏")

文本编辑区域，右键点击文件文件，会弹出菜单栏，会提供一些界面拆分等有用的功能

![Android Studio文本编辑区域](/img/chapter2/as3.png "Android Studio文本编辑区域")

![Android Studio文本编辑区域](/img/chapter2/as4.png "Android Studio文本编辑区域")

底部左侧区域提供日志，终端，性能分析，构建信息等相关功能，右侧则是设备文件浏览器

![Android Studio底部区域](/img/chapter2/as5.png "Android Studio底部区域")

![Android Studio底部区域](/img/chapter2/as6.png "Android Studio底部区域")


右侧边栏则是Gradle脚本相关的任务面板

![Android Studio右侧区域](/img/chapter2/as7.png "Android Studio右侧区域")

### 2.Android 项目结构

以下标注为项目相关的核心文件：

![Android 项目结构](/img/chapter2/as8.png "Android 项目结构")

* `HelloWorld` 
* |-   `.gradle`    自动生成文件夹
* |-   `.idea`    自动生成文件夹
* |-   `app`   程序相关模块，每个程序可以有多个模块，其中一个模块为程序启动模块，此处的app为单一模块，并且作为启动模块
   * |-  `build`  Android Studio 自动生成文件夹，里面包含编译后代码及生成的相关程序apk
   * |-  `libs`   第三方库放置位置，jar、aar文件放置位置
   * |-  `src`    包含该模块的代码及测试代码、布局及图片资源、清单文件的文件夹
      *  |-   `androidTest`   Android测试代码
      *  |-   `main`     模块的代码 、布局及图片资源、清单文件
          *  |-   `java`  模块的java代码文件夹
          *  |-   `res`   图片及布局等资源文件文件夹
          *  |-   `AndroidManifest.xml`   Android配置清单文件，
      *  |-   `test`   Java测试代码文件夹
      *  |-   `build.gradle`  模块的Gradle配置文件
      *  |-   `proguard-rules.pro`  代码混淆配置
* |-  `gradle`    内嵌gradle配置文件夹
* |-  `build.gradle`  项目的gradle配置文件，里面可以配置项目的仓库镜像源，全项目的gradle变量及部署相关工具等
* |-  `gradle.properties`  gradle运行的一些配置
* |-  `gradlew`  项目的gradle启动文件
* |-  `gradlew.bat`  项目的gradle启动文件
* |-  `HelloWorld.iml`  Android Studio 通过该文件找到相关文件配置等，Android Studio自动维护，不可删除
* |-  `local.properties`  用于gradle使用的相关SDK位置配置文件
* |-  `settings.gradle`  声明项目引入的模块，在该文件中声明的文件夹将当成程序的模块处理
* `External Libraries` 当前项目已经以来的相关库文件列表
