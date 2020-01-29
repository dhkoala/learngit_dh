# 适用于热热的git教学文档
>git是用于版本管理的先进工具。  

>我们会学习：  
>+ git的安装和配置  
>+ github的注册  
>+ github与git之间的关系  

>进阶内容：   
>+ 本地创建仓库并管理进度
>+ 将本地仓库与git连接
>+ 将本地仓库内容上传到git

>如果黛珩还想学：
>+ 如何克隆GitHub的其他仓库到本地

## 一、 git的安装和配置
1. 打开Git 2.25.0 Setup
2. 点击Next后在`Use Vim as Git's default editor` 一栏中改为 `Use Visual Studio Code as Git's default editor`
3. 一路next到安装完毕
4. 在win菜单里，找到Git CMD并打开  
5. 在对话框内输入：  
    ```git config --global user.name "这里替换为黛珩自己想要起的名字（引号删除）"```  
    ```git config --global user.email "email@example.com替换为黛珩的邮箱（引号删除）"```  
此时就配置好啦！   
然而我们只是安装好了这个软件！接下来怎么做呢？

## 二、 GitHub的注册  
和`pornhub`其实是一样的，自己试试看！网址为：https://github.com/

## 三、 git与GitHub的联系
>二者之间的关系就像你自己的小电影和pornhub的关系。  

本地可以用Git CMD工具建立一个仓库。表面上这个文件夹和一般的文件夹没区别，实际上git创建了一个唯一的.config文件，这个文件记录里该文件夹（即仓库）内的全部变化。比如新建了某个文档，文档的第几个字被更改了（支持各类代码和Markdown格式的版本追踪）。

同时，在GitHub上也可以创建一个仓库。之后把自己本地的仓库上传到GitHub上，就可以让全世界的人（或者你指定的人）看到这个仓库内的信息。其他人可以copy你的仓库并且进行编辑。他们进行了新的编辑后可以对你发起`pull request`，你可以选择接受他们对你文档的修改或者不接受。

此外，你也可以先在GitHub上创建好你的仓库，再克隆（`clone`）到本地，这样你在本地工作完之后就可以传到云GitHub上了。

>每次的工作流程：  
>+ 打开本地仓库的文件
>+ 干活儿
>+ 把本地的文件保存更改
>+ 上传到GitHub

## 四、 本地创建仓库并管理进度  
下面我会写一些代码，把每一行的代码按次序输入进Git CMD中，如果有问题随时联系我。  
1. 输入： ```cd Desktop```  
2. 输入：```mkdir learngit_ZY```  
3. 输入：```cd learngit_ZY```  
4. 输入：```git init```  
前三步分别为进入桌面，创建名为learngit_ZY的文件夹，进入该文件夹。最后一步是将此文件夹变成一个git仓库。怎么样，是不是很简单呢？  
接下来是很很重要的一步，就是修改git的版本信息。我们现在的仓库是空的，可以理解为一颗树的种子。每一次增加新的文件，都是让这棵树长高，但目前树还没有分叉，以后我们的树可能会分出很多叉来。每次打开文件夹时看到的文件是属于“工作区”的，修改文件后需要把工作区更新一下，此时会需要用到`add`指令。  
等我们工作完成了，希望把这次的成果放到我们当前的分支中（如果只有一个主干，默认命名为master分支）。如何放进去呢？这就需要用到`commit`指令了。  
那我们书接上文吧。  
5. 输入：```git status``` 备注：这一命令能让我们看到分支的状态，如果你完全按照上述四步去做，此时应该显示为：  
“On branch master  
No commits yet  
nothing to commit (create/copy files and use "git add" to track)”  
这就说明这里什么都没有呐！让我们把本文档放进去吧~~~
6. 拖入文档进入文件夹后(此时再输入第五步的指令看看？) 输入：```git add learngit_DH.md```之后再输入第五步的指令看看？ 这一步把我们修改过的文件放入了暂存区，可以理解为保存操作。如果不add，那么关闭文件后将不会被保存。 
7. 最后一步！输入：```git commit```。此时清空了暂存区的文件，并将其放入了工作区。也就是说，我们的树干又往上长了一点。大功告成！
>总结：每一次`add`就是在把文件放入暂存区。每一次`commit`就是把暂存区的文件打包为一个新的版本，叠放在工作区老版本的上面，然后清空暂存区。你可以在任意时刻退回到老版本（但此操作较为复杂，先不讲）。有任何困难 `git status`会是你的好朋友(●'◡'●)ﾉ*\ (๑•₃•๑)*。
待续分支管理

## 五、将本地仓库与git连接
1. 在 Git CMD中输入`ssh-keygen -t rsa -C "youremail@example.com（同上修改）"`，然后一路回车。实际效果如下：“  
C:\Users\lzyws\Desktop\learngit_DH>ssh-keygen -t rsa -C ling_5945@126.com  
Generating public/private rsa key pair.  
Enter file in which to save the key (C:\Users\lzyws/.ssh/id_rsa):  
Created directory 'C:\Users\lzyws/.ssh'.  
Enter passphrase (empty for no passphrase):  
Enter same passphrase again:  
Your identification has been saved in C:\Users\lzyws/.ssh/id_rsa.  
Your public key has been saved in C:\Users\lzyws/.ssh/id_rsa.pub.  
The key fingerprint is:  
SHA256:1sK3McjLl8P20ANH/DD6gkrZ+DQ/h0nymS4axR14FRw ling_5945@126.com  
The key's randomart image is:  
+---[RSA 2048]----+  
|           .Eo   |  
|         . o.    |  
|        . o =    |  
|       + = + +   |  
|        S O . .  |  
|       B.*.X     |  
|      = B+X=+    |  
|     . =.=B=..   |  
|      o..ooo.    |  
+----[SHA256]-----+  
2. 找到id_rsa.pub文件（Your public key has been saved in C:\Users\lzyws/.ssh/id_rsa.pub.），然后拖到vscode里打开，把里面的文字全部复制。
3. 打开自己的GitHub，右上角点自己的头像，下面有setting，点进去。左侧有一栏，点击SSH and GPG keys。右上角 New SSH key，点进去title随便起，key完整粘贴之前id_rsa.pub文件的内容。
4. 点击左上角黑色小猫，再点左侧Repositories边上的New，进入新建仓库页面。**保持Repository name和本地的文件夹名称一样。**其他什么都不需要做，点击 Create repository.
5. 在本地的 Git CMD窗口里输入：` git remote add origin git@github.com:黛珩的用户名/黛珩的文件夹名.git`（如果不清楚可以关注上一步点击后的网址，.com之后就是我们需要加入到上述命令中的），这样我们就关联好了。

## 六、 将本地仓库内容上传到git
1. 在Git CMD中输入：`git push --set-upstream origin master`，回车后输入yes再回车。
2. 欣赏滚动的屏幕。
3. 刷新之前GitHub仓库的网页，看到自己美妙的文件躺在那里。  
ok现在我要把这份文件上传了，之前已经传过一次了。剩余的知识包括如何下载本文件和创建新分支。这些稍后我会提交上去。这次先把该仓库网址和本文件通过微信发过去吧。
