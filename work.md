### git学习

---

##### 1.连接远程Git库

~~~ java
git remote add origin https://github.com/...
~~~

##### 2.推送到远程Git库

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

















