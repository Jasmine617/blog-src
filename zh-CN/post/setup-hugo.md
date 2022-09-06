+++
author = "Jasmine"
title = "使用Hugo创建个人博客框架"
date = "2021-11-24"

description = "Guide to setup blog by hugo"
tags = [
    "GitHub Pages",
    "Hugo",
]

categories = [
    "CS",
]

+++

昨天跑通了如何[使用GitHub Pages建了自己的第一个hello world页面](https://jasmine617.github.io/post/setup-helloworld/)，今天尝试使用Hugo来建一个完整的静态网站框架。

创建静态网站，用Jekyll、Hexo、Hugo等工具都可以，看了网上大家的分析，最终决定用Hugo来做。

这里先介绍如何安装Hugo、使用Hugo创建站点，并引入一个主题。按照本文操作完，站点的页面还是themes带的样例页面。我将在下一篇文章中总结如何加入自己的博文，以及修改网站的其他个人信息。

<!--more-->
我的创建过程基本顺利，基本过程记录如下，遇到的小问题在最后单独说明：

1. 打开[Hugo下载页面](https://github.com/gohugoio/hugo/releases)，获取与本机环境相匹配的安装包。

   例如，我下载的是：“hugo_0.89.4_Windows-64bit.zip”。

   

2. 安装Hugo。

   1. 在本机建一个Hugo文件夹，为方便后续管理，在其下再建一个bin目录。

      例如，我建的目录是“D:\Hugo\bin”。

   2. 将安装包拷贝到bin目录下并解压。

      解压成功后，可以在bin目录下看到“hugo.exe”。

   3. 配置系统环境变量，为变量Path添加“hugo.exe”所在目录。

      对于我来说，添加的是“D:\Hugo\bin”。

   4. 执行如下命令，如果能显示版本号，则说明安装成功。

      ```shell
      $ hugo version
      hugo v0.89.4-AB01BA6E windows/amd64 BuildDate=2021-11-17T08:24:09Z VendorInfo=gohugoio
      ```

      

3. 建立站点。

   1. 在Windows cmd窗口下进入Hugo文件夹。

      注意这里是“D:\Hugo”，不是“D:\Hugo\bin”。

   2. 假设要创建的站点目录为“myblog”，则执行如下命令：

      ```shell
      $ hugo new site myblog
      Congratulations! Your new Hugo site is created in D:\Hugo\myblog.
      
      Just a few more steps and you're ready to go:
      
      1. Download a theme into the same-named folder.
         Choose a theme from https://themes.gohugo.io/ or
         create your own with the "hugo new theme <THEMENAME>" command.
      2. Perhaps you want to add some content. You can add single files
         with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
      3. Start the built-in live server via "hugo server".
      
      Visit https://gohugo.io/ for quickstart guide and full documentation.
      ```

      执行完成后，可以看到“D:\Hugo”下自动创建了一个“myblog”目录，且目录下包含如下内容：

      | 文件夹/文件 | 说明                                                         |
      | ----------- | ------------------------------------------------------------ |
      | archetypes  | 存放default.md，头文件格式，每次新建文章默认显示的头部信息在此修改。 |
      | content     | 存放博客文章，markdown格式文件。                             |
      | data        | 存放自定义或者导入的模板。                                   |
      | layouts     | 存放网站的数据模板。                                         |
      | static      | 存放图片、css、js等静态资源                                  |
      | themes      | 存放主题文件，每个主题都是一个独立的文件夹。                 |
      | config.toml | 网站配置文件。                                               |

      

   3. 下载themes。

      访问[Hugo主题页面](https://themes.gohugo.io/)，找一个自己喜欢的主题下载到上一步创建的“themes”文件夹下，并解压。

      我这次下载的是[NexT主题](https://themes.gohugo.io/themes/hugo-theme-next/)，它支持多设备显示自适应，同时支持评论、转发等博客需要的功能。

      下载完成后，需要按照themes的说明做一些配置。对于我下载的主题，我按照要求把hugo-theme-next目录下的两个子目录config和content到站点根目录（即“D:\Hugo\myblog”）下。

   4. 在本地启动站点。

      在站点根目录执行如下cmd命令：

      ```shell
      $ hugo server
      Start building sites …
      hugo v0.89.4-AB01BA6E windows/amd64 BuildDate=2021-11-17T08:24:09Z VendorInfo=gohugoio
      
                         | ZH-CN | EN
      -------------------+-------+-----
        Pages            |    28 | 34
        Paginator pages  |     0 |  0
        Non-page files   |     8 |  0
        Static files     |    25 | 25
        Processed images |     0 |  0
        Aliases          |     9 | 12
        Sitemaps         |     2 |  1
        Cleaned          |     0 |  0
      
      Built in 42196 ms
      Watching for changes in D:\Hugo\myblog\{archetypes,content,data,layouts,static,themes}
      Watching for config changes in D:\Hugo\myblog\config.toml, D:\Hugo\myblog\config\_default, D:\Hugo\myblog\config\development
      Environment: "development"
      Serving pages from memory
      Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
      Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
      Press Ctrl+C to stop
      ```

      hugo服务启动完成时，将出现与上面相类似的响应。

   5. 在浏览器中访问“http://localhost:1313/”，检查本地站点效果。

   6. 在cmd窗口中按Ctrl+C，停止Hugo服务。

      

4. 发布需要提交到到GitHub的站点文件。

   1. 将站点的BaseURL配置为GitHub Pages主页地址。

      待修改的文件包括“D:\Hugo\myblog\config.toml”、“D:\Hugo\myblog\config\development\config.toml”和“D:\Hugo\myblog\config\_default\config.toml”，将BaseURL的值修改为“https://jasmine617.github.io/”。

   2. 发布站点。

      在站点根目录执行如下cmd命令：
   
      ```shell
      $ hugo
      hugo v0.89.4-AB01BA6E windows/amd64 BuildDate=2021-11-17T08:24:09Z VendorInfo=gohugoio
      
                         | ZH-CN | EN
      -------------------+-------+-----
        Pages            |    28 | 34
        Paginator pages  |     0 |  0
        Non-page files   |     8 |  0
        Static files     |    25 | 25
        Processed images |     0 |  0
        Aliases          |     9 | 12
        Sitemaps         |     2 |  1
        Cleaned          |     0 |  0
      
      Total in 42190 ms
      ```
   
      发布成功，可以在“D:\Hugo\myblog\”下看到public文件夹。将这个文件夹发布到GitHub即可。

      

5. 将站点发布到GitHub。
   1. 进入上一步创建的"D:\Hugo\myblog\public"文件夹，鼠标右键选择“Git Bash Here”，进入Git Bash窗口，执行后续命令。

   2. 初始化git库：

      ```shell
      $ git init
      Reinitialized existing Git repository in D:/Hugo/myblog/public/.git/
      ```
      
   3. 将文件提交到本机git库中。commit备注可以根据实际需要修改。
   
      ```shell
      $ git add --all
      $ git commit -m "first commit of Hugo site"
      ```
      
   4. 检查本机git库是否已经提交成功。下例中的系统响应代表本地git库当前的分支名是master，并且本地已经没有需要commit的文件了。

      ```shell
      $ git status
      On branch master
      Your branch is ahead of 'origin/master' by 1 commit.
        (use "git push" to publish your local commits)
      
      nothing to commit, working tree clean
      ```
      
   5. 使用如下命令，与远程GitHub公仓建立连接，并将站点提交到远程：

      请根据自己的事情，修改GitHub仓库地址和本地分支名。
      
      ```shell
      $ git remote add origin https://github.com/Jasmine617/jasmine617.github.io.git
      $ git push -u origin master
      Enumerating objects: 206, done.
      Counting objects: 100% (206/206), done.
      Delta compression using up to 8 threads
      Compressing objects: 100% (64/64), done.
      Writing objects: 100% (205/205), 194.83 KiB | 32.47 MiB/s, done.
      Total 205 (delta 90), reused 190 (delta 83), pack-reused 0
      remote: Resolving deltas: 100% (90/90), done.
      To https://github.com/Jasmine617/jasmine617.github.io.git
         5e8f0dc..8850953  master -> master
      Branch 'master' set up to track remote branch 'master' from 'origin'.
      ```
      
      如果git操作不熟练，这里可能会出现关联远程仓库失败或者推送失败的情况。请根据错误提示，搜索解决方法。
      
      
   
8. 检查GitHub Page。

   1. 在GitHub仓库中查看本地public目录下的文件是否都已上传。

      我在实际操作时，前一天上传的index.html在远程GitHub上创建的是main分支，今天上传的文件创建的是master分支。并且main分支是默认分支。
      
      而main分支实际没有用了，所以，可以先将默认分支修改为master，再删除main分支。
   

   2. 检查Pages设置是否正确。
   
      前一天GitHub Pages的Source设置是main分支的根目录，需要检查修改为当前的master分支。
   

   3. 打开GitHub Pages页面，显示内容与本地访问“http://localhost:1313/”一致，则说明整个配置成功。

      

   
   
   
