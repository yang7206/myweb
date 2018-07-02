---
layout: post
title:  "1.万事开头难--Android开发环境搭建"
date:   2016-05-23 11:33:17 -0400
categories: yang7206 update
---
    
Android开发环境主要需要以下四部分：

{% highlight ruby %}
  1.JavaSDK开发环境
  2.Gradle工程构建环境
  3.AndroidSDK开发工具包
  4.Android Studio IDE集成开发环境
{% endhighlight %}

## 一.JAVA环境安装

Android主要以Java为主要开发语言，所以JavaSDK安装必不可少。
使用[JavaSDK下载链接](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)进行下载
    
点击Accept License Agreement同意声明，然后点击Windows x86（32位）或者Windows x64（64位）后面的下载链接执行下载，以x64位为例
![javasdk](/img/java_download.png "JavaSDK下载")
    
下载完成后双击打开点击下一步执行默认安装即可，安装过程中会弹窗提示安装jre（JAVA运行环境）,依然是执行默认安装即可
![jre_install](/img/jre_install.png "JRE安装")

 等待安装完成
    
    
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
