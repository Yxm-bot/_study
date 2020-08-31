#    php7

> **变量**
>
> > **$GLOBALS用法**

![微信截图_20200117155736](https://user-images.githubusercontent.com/53646119/72594425-4961ea80-3942-11ea-924d-112de3e53cea.png)

![微信截图_20200117155810](https://user-images.githubusercontent.com/53646119/72594452-5383e900-3942-11ea-89a7-4886576e4a71.png)

##### 2.static定义变量

~~~ php
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

~~~ php
var_dump();            //既 打印出数值，又打印出数据类型
echo  octdec();       //八进制转为十六进制
echo  hexdec();       //十六进制转为八进制

header(string:'Content-type:text/html;charset=utf-8')   //处理乱码

$string="huoudunren.com";
echo "后盾人{$string}hello"        //双引号里面可以加变量，单引号不能
~~~

##### 4.字符串操作

~~~php
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

~~~ php
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

##### 数组

~~~ php
$users=['向军大叔','小明'];
array_push($user,'李四');        //向数组后面压入一个数据'李四'
array_pop($user);        //向数组后面取出一个数据
array_unshift($user,'小明');        //向数组前面压入一个数据'小明'
array_shift($user);        //向数组前面取出一个数据
count($user)          //获取数组的长度
    
$allowImageType=['jpeg'=>50000,'jpg'=>20000,'png'=>30000,];
array_key_exists('jpg',$allowImageType);    //判断'jpg'是否早数组的键位里存在
in_array('50000',$allowImageType);       //判断'50000'是否在数组的值存在
array_keys($allowImageTypae);         //获取数组的键值

$users=[
    ['name'=>'向军大叔','age'=>'23'],
    ['name'=>'小明','age'=>'22'],
    ['name'=>'小张','age'=>'219'],
]; 
$filterUser=array_filter($users,function($user){       
        return $user['age']>20;                   //获取年龄大于20 的数据
});
 print_r($filterUser);

$mapUser=array_map(function($user){             
    unset($user['age']);              //删除数组中'age'的数值
    $user['class']='houdunren.com';       //向数组里添加 'class'=>'houdunren.comn'
    // return $user['name'];            只返回数组中 'name' 的值
    return $user; 
},$users);
 print_r($users);

array_values($users);                      //获取数组的值


$arr=['host'=>'localhost','port'=>3360,'user'=>'root'];
print_r(array_merge($arr,['a'=>'b']));      //合并数组，如果原数组里面有 'a'这个键值,则会修改原有的数据，否则在后面添加

array_change_key_case($arr,1);          //将数组里面的键名转为大写；
array_change_key_case($arr,0);          //将数组里面的键名转为小写；
serialize($arr);                        //将数组序列化为字符串
unserialize($arr);                      //将字符串反序列化为数组
~~~

##### 通过递归将多维数组转大小写

**方法一：手动写方法**

![微信截图_20200119115117](https://user-images.githubusercontent.com/53646119/72674464-d1b2cd80-3ab1-11ea-80f8-e79921ff87cb.png)

**方法二：使用函数(将函数的值改为大写或者小写)**

![微信截图_20200119115816](https://user-images.githubusercontent.com/53646119/72674524-c8763080-3ab2-11ea-84cb-fae214538045.png)

##### 时区

~~~ php
1.date_default_timezone_set('PRC');      //设置时区
2.date_defalut_timezone_get();            //获取时区
~~~

##### 时间戳

~~~ php
echo time();         //获取当前的时间戳
echo microtime()        //获取当前的毫秒时间戳
1.例子：计算for()方法和while()方法的运行时间
   <?php
function runtime($start=null,$end=null){
    static $num=[];
    if(is_null($start)){
        return $num;
    }elseif(is_null($end)){
        return $num[$start]=microtime(true);
    }
    else{
        $end=$num[$end] ?? microtime(true);
        echo '1<hr/>';
        return round($end-$num[$start],2);
    }

}
runtime('for');
for($i=0;$i<20000000;$i++){
    $i++;
}
runtime('forend');
echo runtime('for','forend');
echo '<hr/>';
runtime('while');
$n=0;
while($n<20000000){
    $n++;
}
runtime('whileend');
echo runtime('while','whileend');
?>

~~~

##### 日期

~~~ php
1.echo  date('Y-m-d H-i-s',time()-3600*24);     //获取一天之前的时间
2.print_r(getdate());                           //获取的是一个数组
3.strtotime('2020-01-18');                   //将标准的时间转换为时间戳
4.strtotime('now');              //获取当前时间戳
5.echo  date('Y-m-d H-i-s',strtotime('+1 year'));   //打印一年之后的时间
~~~

##### 文件操作

~~~php
1.dis_total_space('目录名');           //获取目录大小（字节）
2.disk_free_space('目录名')            //获取目录可用大小

$filename="a.txt";
$open_f=open($filename);               //打开'a.txt'文件
echo filesize($filename);               //文件大小
echo fread($filename,filesize($filename))   //读取文件全部内容
is_writable('a.txt');         //查看是否有写的权限
is_readable('a.txt');         //查看是否有写的权限
file_exists('a.txt');      //查看是否存在这个文件
is_dir('../80');         //判断上一层是否存在‘80’这个目录
file_put_contents('a.txt','houdunre.com');   //创建并编写内容（注意：会覆盖原有的内容）
file_put_contents('a.txt','houdunre.com'，FILE_APPEND);   //创建并编写内容（注意：不会覆盖原有的内容）
file_get_contents('a.txt')          //读取文件内容
echo __FILE__;                      //文件完整路径
echo basename(__FILE__);           //文件名称
echo dirname(__FILE__);           //文件路径
~~~



