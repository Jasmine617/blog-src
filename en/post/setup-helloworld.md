+++
author = "Jasmine"
title = "Setup the first GitHub Page"
date = "2021-11-23"
description = "Guide to setup hello world in GitHub Pages"
tags = [
    "GitHub Pages",
]

categories = [
    "Blog",
    "Web",
]

+++

Let‘s talk about how to setup a github page.
<!--more-->
This is my method ：

1. Register in[GitHub](https://github.com/).

   

2. Create a repository。

   ![单击创建仓库按钮](//jasmine617.github.io/post/images/20211123001.png)

   

   The name of the repository should be same as your user name.

   ![创建仓库](//jasmine617.github.io/post/images/20211123002.png)

   

3. Install git in your PC.

   then config your name and email：

   ```shell
   $ git config --global user.name "Jasmine"
   
   $ git config --global user.email "123456@qq.com"
   ```
   
   
   
4. Create a SSH Key，and config it to GitHub.

   1. Run ssh-keygen in  your PC.

      Please use your own email：

      ```shell
   $ ssh-keygen -t rsa -C "123456@qq.com"
      ```

   
   2. Config the key to GitHub.
   
   ![创建SSH密钥](//jasmine617.github.io/post/images/20211123003.png)
      
   
      ![配置密钥](//jasmine617.github.io/post/images/20211123004.png)
   
   

5. Clone the repository from GitHub.

   1. Get the URL of your repository:
   
      ![获取仓库URL](//jasmine617.github.io/post/images/20211123005.png)

      

   2. Create a folder in your PC, then open the  Git Bash and excute.
   
      Please use  your own URL:
   
      ```shell
      $ git clone git@github.com:Jasmine617/jasmine617.github.io.git
      Cloning into 'jasmine617.github.io'...
      warning: You appear to have cloned an empty repository.
      ```
      or：
      
      ```shell
      $ git clone https://github.com/Jasmine617/jasmine617.github.io.git
      ```




6. Create index.html and commit to git in your PC.

   1. After clone, you will fine a new folder. Enter, then Create index.html，

      This is a example:

      ```html
      <!DOCTYPE html>
      <html lang="en">
      <head>
          <meta charset="UTF-8">
          <title>my first blog</title>
      </head>
      <body>
      <p>hello world</p>
      </body>
      </html>
      ```
   
   3. Commit the file in Git Bash.

      ```shell
      $ cd jasmine617.github.io
      $ git add --all
      $ git commit -m "test commit index.html"
      ```
   
   
   
7. Pull the file to your GitHub repository.

   1. check your git status.

      ```shell
      $ git status
      On branch main
      Your branch is up to date with 'origin/main'.
      
      nothing to commit, working tree clean
      ```
   

   2. pull it to your GitHub repository.

      ```shell
      $ git push origin main
      Enumerating objects: 3, done.
      Counting objects: 100% (3/3), done.
      Delta compression using up to 8 threads
      Compressing objects: 100% (2/2), done.
      Writing objects: 100% (3/3), 338 bytes | 338.00 KiB/s, done.
      Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
      To https://github.com/Jasmine617/jasmine617.github.io.git
       * [new branch]      main -> main
      ```

   

8. Check your GitHub Page。

   1. Check whether the index.html is in repository.

      ![检查上传结果](//jasmine617.github.io/post/images/20211123006.png	"检查上传结果")
   

   2. Check the GitHub Page Configuration.

      ![页面设置](//jasmine617.github.io/post/images/20211123007.png	"页面设置")
   
   
   3. Open your GitHub Pages.

      ![创建结果](//jasmine617.github.io/post/images/20211123008.png	"创建结果")

   

   
