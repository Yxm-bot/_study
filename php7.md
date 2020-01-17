#    php7

> **变量**
>
> > **$GLOBALS用法**

![微信截图_20200117155736](https://user-images.githubusercontent.com/53646119/72594425-4961ea80-3942-11ea-924d-112de3e53cea.png)

![微信截图_20200117155810](https://user-images.githubusercontent.com/53646119/72594452-5383e900-3942-11ea-89a7-4886576e4a71.png)

##### 2.static定义变量

~~~ java
function make(){
  static $num=1;       //(static)解释此语句只在第一次调用时才会执行赋值操作，之后都不会执行
  $num=$num+1;
    return $num;
}
echo make();
echo make();
echo make();

//结果是   2  3  4;
~~~

##### 3.数据类型

~~~ javaj
var_dump();            //既 打印出数值，又打印出数据类型
echo  octdec();       //八进制转为十六进制
echo  hexdec();       //十六进制转为八进制

header(string:'Content-type:text/html;charset=utf-8')   //处理乱码

$string="huoudunren.com";
echo "后盾人{$string}hello"        //双引号里面可以加变量，单引号不能
~~~

##### 4.字符串操作

~~~java
$string=" houdunren.com ";
$str='向军大叔';
strlen($string);             //字符串长度
mb_strlen($str);             //区分宽字节
trim($string);                     //删除左右空格   结果：15
trim($string,' moc.ner')      //结果：5 (从两边开始匹配字符，有就删除)
explode('.','houdunren.com')    //已 '.' 来拆分字符串
 
$arr=['email','234234224qq.com']
implode(':',$arr)            //已 ':' 合并字符

$str='username'
substr($str,0,4)           //0:从左边数  4:长度
mb_substr()             //区分宽字节
~~~

##### 常量

~~~ java 
常量不受使用范围限制，在任何地方都能用
1.define('name','向军'，false)       //定义常量，'name'只能定义一次   【false】是否区分daxiaoxie
2.define('data',[1,2,3]);
  echo data[2]   //结果  3
3.conset url='houdunren.con'    //定义常量
  defined('name')        //监测常量是否存在
      
4.系统定义的常量
      __CLASS__       //类名
      __METHOD___     //方法名
      get_defined_constants()        //系统中的全部常量
5.三木运算符
      a??b:c       //判断a是否存在并且值不能为空
          
6.错误
    @+....              //屏蔽错误
~~~





