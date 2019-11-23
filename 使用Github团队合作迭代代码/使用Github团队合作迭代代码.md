@[TOC](目录)
# 前言
&emsp;&emsp;总结一下使用github进行团队合作迭代代码的方法
# 一、管理员新建远程github项目仓库

1、在github上新建一个项目：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123185112541.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)


2、然后依次执行以下代码进行本地项目初始化、绑定远程git与同步到远程git：
（1）第一次初始化时运行：

> 在本地项目目录下鼠标右键点击Git Bash Here初始化git(在当前目录下生成隐藏文件夹.git)
> `git init`
> 将当前项目所有文件添加到本地git仓库
>`git add .`
>更新代码到本地仓库
>`git commit -m "first commit"`
>添加远程git的url地址
>`git remote add origin https://git地址.git`
>将本地代码同步到远程git上
>`git push -u origin master`


（2）之后更新代码时运行
> 将当前项目所有文件添加到本地git仓库
>`git add .`
>更新代码到本地仓库
>`git commit -m "first commit"`
>  将项目推送给远端第一次时不用执行下面的代码
>`git pull --rebase origin master`
>将本地代码同步到远程git上
>`git push -u origin master`


3、队长在项目`setting`——>`Collaborators`搜索队员昵称添加邀。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019112319311640.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)

# 二、队员使用github进行团队合作
&emsp;&emsp;邀请者接受邀请即可参与代码编写。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123192909853.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
## 2.1 Fork项目到个人的仓库
&emsp;&emsp;（1）点击右上角的Fork，就可以Fork团队项目到个人远端仓库了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123193659889.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
&emsp;&emsp;（2）然后回到自己打的主页点击`Repositories` 即可看到同步完的项目。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019112319411372.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
## 2.2 Clone（克隆）项目到本地
&emsp;&emsp;克隆方式有两种：推荐使用SSH协议，用HTTP协议有时会出问题。注意，这里clone的是你自己仓库里的项目
（1）点击`Clone or download`——>`Use SSH` 或直接使用http协议复制。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123195042465.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（2）点击右面的按钮复制链接
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123195343292.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（3）在本地电脑中进入到你想放置项目的目录中鼠标右键打开`Git Bash Here`，输入指令和刚才复制的地址，回车即可克隆到本地。
```java
git clone https://github.com/git链接.git
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123200109829.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
此时在当前目录中会出现该项目完整代码。

## 2.3 和团队项目保持同步
（1）首先查看有没有设置upstream，使用下面命令来查看。如下图表示没有设置。 

```java
git remote -v
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123201042636.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（2）如果没有设置upstream，则执行下面命令：

```java
git remote add upstream 团队项目地址
```
（3）接着再次使用 `git remote -v` 查看，如下图显示出了upstream，那么就设置好了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123201535713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（4）开始同步。首先执行下面代码来获取团队项目最新版本，如下图：
```java
git fetch upstream 
```
（5）此时并没有把最新版本合并到你本地上，因此还需要一步。执行下面命令后,将源项目（团队大项目）的代码同步到自己本地中。

```java
 git pull upstream master
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123204435655.png)
（6）此时队员自己的远程仓库中还没有更新成为最新的代码。更改完程序后将自己的代码同步到自己账户的流程：依次执行以下命令：

> 将当前项目所有文件添加到本地git仓库
>`git add .`
>更新代码到本地仓库
>`git commit -m "first commit"`
>  将项目推送给远端第一次时不用执行下面的代码
>`git pull --rebase origin master`
>将本地代码同步到远程git上
>`git push -u origin master`

## 2.4、请求合并到团队项目上
（1）首先到你的GitHub上，进入你Fork的仓库里。点击红框处的`Pull request`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123205341861.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（2）点击红框处的 Create pull request就可以发送合并请求了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123205614957.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（3）输入标题和代码迭代内容提交即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123210209645.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
## 2.5、团队项目负责人审核及同意合并请求
（1）首先进入GitHub的团队项目仓库中。此时右边的`Pull requests`显示当前项目有几个Pull request。点击进入查看。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019112321042831.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)
（2）如果没有问题，可以点击Merge pull request。这样就合并好了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123210551596.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0d1b1FpWmhhbmc=,size_16,color_FFFFFF,t_70)