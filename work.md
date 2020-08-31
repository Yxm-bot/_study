

## [Markdown语法大全][https://www.cnblogs.com/zhao-yang/p/11755656.html]

-----------------



### 【git学习】

---

##### 1.连接远程Git库

~~~ java
git remote add origin https://github.com/...
~~~

##### 2.推送到远程Git库   --(先同步远程库)  

// *git pull origin master --allow-unrelated-histories*

~~~ java
git push -u origin master
~~~

##### 3.生成秘钥

~~~ java
ssh-keygen -t rsa -C '邮箱'
   // 公钥文件在 C:\user\administrator
~~~

------

##### 4.连接远程github库   （git remote -v ）查看本地是否添加远程库的别名

~~~ java
1.git remote add origin https://giothub.com/...
//本地添加origin(名字)-远程库名字(https://github.com/...)
<上面操作之后，以后就可以用(origin)代替远程github库名字>
    例如：git push origin(远程github库别名) master(远程库的分支)
~~~

##### 5.Git版本跳跃

~~~ java
   reset命令的三个参数:
         --hard      
                      在本地库移动HEAD指针
                      重置暂存区
                      重置工作区

         --mixed      
                      在本地库移动HEAD指针
                      重置暂存区

         --soft       仅仅在本地库移动HEAD指针

   git reset --hard  [索引值]
~~~



##### 6.查看版本历史记录

~~~ javja
   git log                        查看版本历史
   git log --pretty=oneline
   git log --oneline
   git log --name-only          //查看文件的变化
   git log --name-status       //查看文件变化的类型
   git commit --amend          //修改最新一次提交的日志文件内容
~~~

##### 7.设置忽略文件 .gitignore

 1.在库里面创建一个.gitignore的文件，在编辑添加*.txt,后保存退出，在新建一个a.txt文件后用git  status测试不会提示a.txt文件

-----

#####  语法

~~~ javav
*.txt   //全部以txt结尾的文件
!a.txt   //除了a.txt其余都不影藏
/vendor   //忽略文件夹   注意：只有在文件夹里面有文件是Git才回去监测
~~~

##### 8.仓库问价删除

~~~ java
git rm a.txt      //本地库和工作区同时删除文件a.txt
git rm --cached readme.txt  //【第一次提交时】只删除(本地库或则暂存区)里面的文件，工作区不删除  
git  reset HEAD a.txt  //【之后的多次提交】只删除(本地库或则暂存区)里面的文件，工作区不删除.【会撤销从上一次提交（commit）之后的一些操作】
 git checkout -- a.txt  //回到上一步修改 
~~~

##### 9.仓库文件改名

~~~~ javav
1.  git mv a.txt b.txt        //本地改名
2.  git add .            //提交到暂存区
3.  git commit -m 'first rename'  //提交到本地库
~~~~

##### 10.分支

~~~ java
1.git branch               //查看分支
2.git checkout ask         //创建ask分支
3.git checkout -b ask      //创建并切换到新的分支
~~~



##### 11.rebase

~~~ java
git rebase master    //在子分支上面操作，目的将子分支的根节点想后面一一位
~~~









### 【apache】

----------

##### 1.apache安装

~~~ java
linux: yum install -y httpd         //联网状态下安装httpd
       rpm -qa | grep  httpd        //查看是否安装了httpd
~~~

##### 2.apache 配置文件

~~~~ java
1.配置文件一般都保存在 /etc/httpd/  目录下
2.apache是一个模块化设计的服务
3./etc/httpd/run/http.pid       //里面存放的是apache的主进程号
  /etc/http/conf.d              //每个模块都可以在conf.d下生成一个独立的模块配置文件
4.ps aux | grep httpd           //查看apache进程
5.which a.txt                   //查看a.txt文件位置
6.httpd -M                      //查看模块
7.httpd -l                       //查看哪些模块是被静态编译的
8.netstat   -tnl                  //查看端口是否开启
9. httpd  -t                         //查看配置文件是否有语法错误
    
~~~~

##### 3.apache认证

![](https://user-images.githubusercontent.com/53646119/71499631-55efa780-289c-11ea-8a3e-112c076db9fc.png)

##### 4.区与域名虚拟主机配置

![微信截图_20191227120326](https://user-images.githubusercontent.com/53646119/71500624-c1d40f00-28a0-11ea-9710-abc8838e5967.png)

>  1.apache虚拟主机配置流程[**虚拟主机**][https://blog.csdn.net/bmengmeng/article/details/90479114] 



##### 5.apache配置文件的讲解

> 全局配置： 

~~~~ java
1.ServerRoot  "etc/httpd"             //主配置文件路径
2.Listen  80 或(192.168.1.1:80)                //服务器监听端口
3.Include  conf.d/*.conf         //将conf.d/*.conf 里的模块配置文件从新加载到主配置文件里面

~~~~

> 主配置文件

~~~~java
1.ServiceAdmin   apache@linux.net                       //管理员的邮箱名
2.ServiceName    www.apache.com                      //指定服务器域名
    (在 /etc/hosts 配置下本机dns，就能用域名访问网站了)
3.DocumentRoot    "/var/www/htm"                     //默认网站路径
4.<Directory />
                                     //里面的 '/'是指目录也可以是其他，用设置该目录的一些访问权限
  </Directory>
5.DirectoryIndex   index.html index.html.var       //默认加载的首页的名称
6.AddDefaultCharset      UTF-8         //服务器默认使用的编码
~~~~



### 【apache】加载【php】

#####  1.php配置文件

~~~ java
1.php里面有两个配置文件
    php.ini-development              //开发环境(使用电脑的性能不多)
    php.ini-production               //生产环境
~~~

##### 2.让apache识别php

![微信截图_20191231170336](https://user-images.githubusercontent.com/53646119/71616085-69c64100-2bef-11ea-9129-e705898c5f0b.png)

~~~ java
第一行：本机php所下载的位置
第二行：为apache添加可识别的文件类型
第三行：php配置文件路径
~~~





















 