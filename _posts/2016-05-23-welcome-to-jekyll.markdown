---
layout: post
title:  "1.万事开头难--Android开发环境搭建"
date:   2016-05-23 11:33:17 -0400
categories: yang7206 update
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

## 一.Gradle环境安装

### 1.安装Gradle
Android Studio自带Gradle环境，但是可能出现被墙导致下载缓慢，仓库无法访问导致构建项目卡住的问题，这里推荐一下做法来解决问题：
    
    自行安装Gradle环境 + 国内镜像源

在下列地址中选择Gradle版本，本文中使用4.4.1版本
    
    http://services.gradle.org/distributions 选择版本

点击这里[下载4.4.1-all版本](http://services.gradle.org/distributions/gradle-4.4.1-all.zip)

Gradle解压即可使用，下载完成后直接解压到需要安装的位置即可

![gradle_install](/img/gradle_install.png "Gradle安装")

### 2.配置Gradle环境变量

依然是安装以上JAVA配置环境变量的步骤，新增`GRADLE_HOME`和`GRADLE_USER_HOME`变量，同时将`GRADLE_HOME`配置到Path中,将`%GRADLE_HOME%\bin;`加入到Path变量中
    
    GRADLE_HOME是Gradle的安装位置
    GRADLE_USER_HOME是Gradle的工作及缓存仓库文件目录，不配置时默认为用户目录下.gradle文件夹
    GRADLE_HOME

![gradle_env](/img/gradle_env.png "Gradle环境配置")

### 3.测试JAVA是否正确安装
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
