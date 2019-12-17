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
    例如：git push origin(远程github库别名) master(本地的分支)
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
~~~





