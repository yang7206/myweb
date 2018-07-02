---
layout: post
title:  "第一章.万事开头难--Android开发环境搭建"
date:   2018-07-03 11:33:17 -0400
categories: Android
---
    
Android开发环境主要需要以下四部分：

    一.JavaSDK开发环境
    二.Gradle工程构建环境
    三.AndroidSDK开发工具包
    四.Android Studio IDE集成开发环境

## 一.JAVA环境安装

### 1.安装JDK

Android主要以Java为主要开发语言，所以JavaSDK安装必不可少。
使用[JavaSDK下载链接](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)进行下载
    
点击Accept License Agreement同意声明，然后点击Windows x86（32位）或者Windows x64（64位）后面的下载链接执行下载，以x64位为例

![javasdk](/img/java_download.png "JavaSDK下载")
    
下载完成后双击打开点击下一步执行默认安装即可，安装过程中会弹窗提示安装jre（JAVA运行环境）,依然是执行默认安装即可

![jdk_install](/img/jdk_install.png "JDK安装")

![jre_install](/img/jre_install.png "JRE安装")

等待安装完成

### 2.配置JAVA环境变量

右键单击`我的电脑`，选择`属性`，点击左上角`高级系统设置`打开系统属性，选择`高级`，然后点击`环境变量`

![jdk_env](/img/jdk_env.png "JDK环境变量")

在打开的环境变量中，点击`新建`，在弹出框中变量名输入`JAVA_HOME`，变量值输入刚才我们安装的JAVA路径`C:\Program Files\Java\jdk1.8.0_171`，然后点击确认

![jdk_env1](/img/jdk_env1.png "JDK新建环境变量")

然后在系统变量中搜索`Path`变量,双击`Path`变量会弹出编辑系统变量，将`%JAVA_HOME%\bin;`加入到环境变量的最前面，注意不是替换，可以CTRL+A全选然后拷贝到文本中进行编辑，然后重新粘贴回去，然后点击保存

![jdk_path](/img/jdk_path.png "JDK环境变量配置")

![jdk_path1](/img/jdk_path1.png "JDK环境变量配置1")

### 3.测试JAVA是否正确安装

接下来需要测试JDK是否安装完成，使用`WIN + R`组合键打开运行栏，然后输入`cmd`运行命令行，输入`java -version`和`where java`如果能正确输出版本号及路径，说明JAVA安装已经完成

![jdk_test](/img/jdk_test.png "JDK环境测试")

    C:\Users\Administrator>java -version
    java version "1.8.0_171"
    Java(TM) SE Runtime Environment (build 1.8.0_171-b11)
    Java HotSpot(TM) 64-Bit Server VM (build 25.171-b11, mixed mode)
    
    C:\Users\Administrator>where java
    C:\Program Files\Java\jdk1.8.0_171\bin\java.exe
    
**JAVA配置完成**

## 二.Gradle环境安装

### 1.安装Gradle
Android Studio自带Gradle环境，但是可能出现被墙导致下载缓慢，仓库无法访问导致构建项目卡住的问题，这里推荐一下做法来解决问题：
    
    自行安装Gradle环境 + 国内镜像源

在下列地址中选择Gradle版本，本文中使用4.4.1版本
    
    http://services.gradle.org/distributions 选择版本

>点击这里[下载4.4.1-all版本](http://services.gradle.org/distributions/gradle-4.4.1-all.zip)

Gradle解压即可使用，下载完成后直接解压到需要安装的位置即可

![gradle_install](/img/gradle_install.png "Gradle安装")


### 2.配置Gradle环境变量

依然是按照以上JAVA配置环境变量的步骤，新增`GRADLE_HOME`和`GRADLE_USER_HOME`变量，同时将`GRADLE_HOME`配置到Path中,将`%GRADLE_HOME%\bin;`加入到Path变量中
    
    GRADLE_HOME是Gradle的安装位置
    GRADLE_USER_HOME是Gradle的工作及缓存仓库文件目录，不配置时默认为用户目录下.gradle文件夹，Gradle会下载或大量缓存文件，建议将文件夹放在非系统盘
    本文中GRADLE_USER_HOME指定为D:\.gradle文件夹
    

![gradle_env](/img/gradle_env.png "Gradle环境配置")

### 3.测试Gradle是否正确安装

依然是使用命令行输入`gradle` 和 `where gradle` 查看是否Gradle是否正确安装


    C:\Users\Administrator>gradle
    Starting a Gradle Daemon (subsequent builds will be faster)
    
    > Task :help
    
    Welcome to Gradle 4.4.1.
    
    To run a build, run gradle <task> ...
    
    To see a list of available tasks, run gradle tasks
    
    To see a list of command-line options, run gradle --help
    
    To see more detail about a task, run gradle help --task <task>
    
    
    BUILD SUCCESSFUL in 9s
    1 actionable task: 1 executed
    C:\Users\Administrator>where gradle
    D:\gradle-4.4.1\bin\gradle
    D:\gradle-4.4.1\bin\gradle.bat


如果能正确输出，说明gradle已经正确安装

### 4.配置Gradle全局镜像

在GRADLE_USER_HOME目录（D:\\.gradle文件夹，如果不存在可以自行创建）下新建`init.gradle`文件，将以下代码拷贝到init.gradle文件中

***init.gradle***
```
allprojects {
        repositories {
            maven { url 'http://maven.aliyun.com/nexus/content/groups/public/' }
            maven { url 'http://maven.aliyun.com/nexus/content/repositories/jcenter' }
            maven { url "https://maven.google.com" }
            jcenter()
        }
    }
```
>allprojects 代表所有项目
>>repositories 表示仓库路径
>>>maven 则代表一个仓库，其内部的url代码该仓库的路径
>>>
>>>jcenter()是一个默认内建官方仓库



    gradle在搜索需要的模块时，会自上而下进行搜索查找，直到找到第一个位置，如果不存在则会报找不到错误
    
    jcenter在国内可能存在被墙，所有这里使用阿里云的仓库，也可以添加其他仓库进来，只需要按`maven {url '地址'}`的格式添加即可

### 5.查看仓库路径
    
    在任意位置新建`build.gradle`文件，Gradle的大部分语法与Java兼容，放入以下代码：
    
***build.gradle***  

```
 repositories {
        mavenCentral()
 }
    
 task showRepos {
     doLast {
         println "All repos:"
         println repositories.collect { it.name +" -> "+ it.url +"\n" }
     }
 }

```
    

进入build.gradle文件所在的位置，使用命令`gradle --init-script init.gradle -q showRepos` ,以下使用`D:\android_test`文件夹进行演示:


    C:\Users\Administrator>d:
    
    D:\>cd android_test
    
    D:\android_test>gradle --init-script init.gradle -q showRepos
    All repos:
    [maven -> http://maven.aliyun.com/nexus/content/groups/public/
    , maven2 -> http://maven.aliyun.com/nexus/content/repositories/jcenter
    , maven3 -> https://maven.google.com
    , BintrayJCenter -> https://jcenter.bintray.com/
    , MavenRepo -> https://repo.maven.apache.org/maven2/
    ]
    D:\android_test>


showRepos task已经正确输出maven仓库及对应的仓库路径，说明路径配置成功，后续的Android Studio的路径将会自动加入该路径进行搜索

**Gradle配置完成**


## 三.Android SDK环境安装

    未完待续~！
    
## 四.Android Studio安装

    未完待续~！