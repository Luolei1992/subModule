### 软件的基本架构
1. cs架构：client server 
  - 客户端，服务端（客户端需要自己编写）软件性能高，但需要安装包，升级不方便
2. bs架构：browser server
  - 浏览器服务端 （这些软件都是基于浏览器的）软件性能低，但升级方便，所有页面都是从服务器端获取
*不管哪种架构都需要一个客户端一个服务端*
### 服务器
+ 服务器是计算机的肯定必须要安装一个操作系统，

  - 按照操作系统来分:

        1. Linux服务器、Windows服务器等

    按服务类型可分为:

        2. 文件服务器，数据库服务器，邮件服务器,Web 服务器 （对外提供web 服务）；

  - web 服务器：
  
         1：接收客户端的请求
         2：对客户端的请求的进行处理
         3: 还需要给客户端一个响应，响应一个html 页面。

  - 按应用软件可分为: 

         Apache服务器、Nginx 服务器、IIS服务器、Tomcat服务器、Node服务器等。
        （假设我的这台超级计算机安装了一个操作系统，能对外提供服务，不行
         必须安装对应的 服务器应用软件才能对外提供服务
         我安装了web 服务器对应的软件，我就可以对外提供web 服务）

      常见的web 服务器软件：

         1：Apache服务器 它是一个软件，提供web 服务的软件
         2：Nginx 服务器,IIS服务器、Tomcat服务器、Node服务器等。

- dns  （domain Name  System） 域名解析系统
- www.baidu.com  我访问的是一个域名，它要帮我去找ip 等于119.75.217.109 的计算

#### 我们的资源分为两种类型的资源：

    静态资源: 可以直接通过浏览器打开的
           html,js,css,2.jpg 我们把这些资源叫做静态资源
    动态资源：
           .php , jsp(java)  ,asp
                php 适合于做一些小型的web 网站，论坛，博客。
                jsp 适合应用于做一些大型的系统：银行，企业办公系统，证劵系统
                php 比 jsp 要快一些.  php 杀鸡的刀，jsp 是用来宰牛.
### 文件配置

> wamp 已经安装好，我们把这个软件里面的一些配置文件了解一下。一般一个软件都会有配置文件.

> 集成软件：apache   ，mysql （数据库软件），php

**以下盘符为安装目录**

    C:\wamp\bin 这个bin 目录下我们可以看到三个文件夹
    以后我要配置apache 我需要进入到这个目录下面：
    C:\wamp\bin\apache\Apache2.2.21
    //配置文件都在这里:
    C:\wamp\bin\apache\Apache2.2.21\conf
    我这是一个软件，我需要启动这个软件.
    我要访问这个软件，我需要通过ip+端口
    192.168.38.79:80
    访问的是我本机，访问本机的ip，我们还有两种写法
    localhost
    127.0.0.1 能看到这个界面，说明wamp 安装启动成功.

    如果没有权限:You don't have permission to access / on this server.
    需要进入到配置文件（httpd.conf） 235 行添加： Allow from all（其他人也能访问）

### 配置默认文件地址

根据ip 找到计算机,通过80端口默认进入到apahce，然后默认是去c://www 找对应的文件，对应的项目，

     对应的文件下面的index 开头的文件。
     这个目录我们可以修改：c://www
     我怎么去修改这个目录:
            我们需要配置两个地方: C:\wamp\bin\apache\Apache2.2.21\conf\httpd.conf
            178 行：DocumentRoot "e:/www/"
            205 行：<Directory "e:/www/">

### 配置域名

第一步：

    http://www.taobao.com 首先它会进入到哪里进行查找，进入到的本地的硬盘上面去找一个文件，这个是默认的。
        C://windows/system32/drivers/etc/hosts.hosts
    这个文件不能在当前文件夹修改，因为会涉及到权限问题。所以我们需要拷贝到外面。
        127.0.0.1   www.taobao.com
        就能够被转换到127.0.0.1:80 这样就进入到我的apache 下面，我还需要在apahce 下面进行一些配置.

第二步：

        apahce / httpd.conf
        467 行#号去掉: Include conf/extra/httpd-vhosts.conf 它会去这个目录下面找 conf/extra/httpd-vhosts.conf

第三步：

    <VirtualHost *:80>
        ServerAdmin webmaster@dummy-host.example.com
        我们访问http://www.taobao.com 现在我们已经知道已经进入到f:/workspace
        DocumentRoot "f:/workspace/taobao"
        ServerName taobao.com
        ServerAlias www.taobao.com
        ErrorLog "logs/dummy-host.example.com-error.log"
        CustomLog "logs/dummy-host.example.com-access.log" common
    </VirtualHost>
-----------------------------------------------------------------------------------------

## php简单学习
```
<?php
    echo'<h1>哈哈</h1>';    //php是在服务器端运行的语言
?>

<?php
    /*定义变量*/
    $username = 'zs';
    $username1 = 'ls';
    echo($username.$username1);
    echo $username.$username1;      //两种方法都能输出，点是链接字符串的
?>

<?php
    function person($username = 'zs'){
        echo 'ls'.$username;
    };
    person('ww');       //输出lsww，这时默认的参数值不起作用
    person();            //输出lszs
?>

<?php
    $array = array('zs','ls','ww');   //定义数组
    print_r($array);            //输出数组   Array ( [0] => zs [1] => ls [2] => ww )
    var_dump($array);           //输出数组   array
                                // 0 => string 'zs' (length=2)
                                //  1 => string 'ls' (length=2)
                                //  2 => string 'ww' (length=2)
?>
```
### php常见函数

```
<?php
    //php常见函数
    //print_r()   输出数组
    //var_dump()  输出数组
    //in_array()  是否在数组中
    //count()     计算数组长度
    //array_key_exists ()   检测数组中是否存在key，这个是用在关联数组当中的.
    //array_key_exists('admin', $users)
    //file_get_contents读取文件，读取服务器硬盘上面的某个文件，并且将这个文件的内容专程字符串.
    //move_uploaded_file($files, './demo.jpg');  //我们肯定是用在文件上传上面.
            $data=file_get_contents("1.txt");
            echo $data;
            $array=array("zs","ls","ww");
            $flag=in_array("ww",$array);
            echo $flag;        //存在的话返回1，不存在不返回值
    //定义一个关联数组
              $array1=array("username"=>"zs","age"=>11);
              $flag1=array_key_exists("username",$array1);
              echo $flag1;         //存在的话返回1，不存在不返回值
?>
```
### get和post提交简单理解

```
<?php
    //echo '<h1>哈哈</h1>';
    $data = $_GET;            //$——GET是php内部定义好的，接收客户端传输的数据
    //echo $data              //输出Array
    var_dump($data);
    foreach($data as $key=>$val){     //foreach遍历关联数组
        echo $val.'--------'.'<br>';
    }
?>
```
*post用于表单提交，表单的action写提交的地址，点击提交表单会把数据发送到服务器，这是表单提交的固有属性，method设置提交方式*
```
<?php
    //echo '<h1>哈哈</h1>';
    $data = $_POST;            //$_POST是php内部定义好的
    //echo $data              //输出Array
    var_dump($data);
    foreach($data as $key=>$val){
        echo $val.'--------'.'<br>';
    }
?>
```
*简单的逻辑*
```
<?php

    $data = $_POST;            //$_POST是php内部定义好的
    //echo $data              //输出Array
    var_dump($data);
    foreach($data as $key=>$val){
        echo $val.'--------'.'<br>';
    }
    $username = $data['username'];    
    $password = $data['password'];
    if($username=='luolei' && $password=='123456'){
        echo '欢迎罗磊';
    }else{
        echo '输入有误';
    }
?>
```
### 动态输出格式书写（在.php文件中）

```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        div {
            height:30px;
            width:500px;
            background-color:pink;
            margin-top:10px;
        }
    </style>
</head>
<body>
    <?php for($i = 0;$i < 10;$i++){ ?>

        <div>
            <?php echo $i; ?>
        </div>

    <?php } ?>
</body>
</html>
```

### 客户端与服务器进行交互，传递文件

- 文件上传：（客户端向服务器端传递数据）

- 文件上传对客户端的要求:

  1. 必须是表单提交
  2. 我必须有一个input 选项  它的类型是file
  3. 我必须是post 方式提交。
  4. 必须设置在表单上面设置一个属性  form   enctype="multipart/form-data";

- 文件上传在服务端怎么去获取数据:
  - 服务器去获取客户端的数据，
  - 假设客户端是以get 方式提交的数据 我就是用$_GET
  - 假设客户端是以post 方式提交的数据，我就是用$_POST
  - 假设客户端的数据是文件上传上传，我就是用  $_FILES
------------------------------------------------------------------------
### http协议
- 协议：由w3c制定，规定了客户端与服务器进行通讯的数据格式。（约束客户端浏览器与服务器进行通讯）
- 怎么获取到客户端和浏览器之间交换的的数据，抓包工具（charles）
- 客户端给服务器发送请求
    + 请求首行
    + 请求头
    + 请求空行
    + 请求体
- 服务器给客户端相应数据
    + 响应首行
    + 响应头
    + 响应空行
    + 响应体
- http 协议的数据分为两部分：
   1. 客户端发送给服务器的数据，称为请求的数据格式；
   2. 发送到服务器端的请求的数据格式分为四部分：（客户端发送服务器的数据）
       1. 请求首行
           GET /day08/mycode/02array.html HTTP/1.1
       2. 请求头 (请求头的名称，请求头的值)
       3. 请求空行 (请求空行没有什么作用)
       4. 请求体  （get 方式提交没有请求体） 
------------------------------------------------------------------------
### ajax交互

   **get 方式提交**

        GET /day08/mycode/02array.html HTTP/1.1
        Host	127.0.0.1
        Cache-Control	max-age=0
        Upgrade-Insecure-Requests	1
        User-Agent	Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.106 Safari/537.36
        告诉服务器客户端浏览器接收的数据格式。
        Accept	text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
        //接受的编码，
        Accept-Encoding	gzip, deflate, sdch
        //接收的语言.
        Accept-Language	zh-CN,zh;q=0.8
        If-None-Match	"1900000000036e-af-53c595c55c0ef"
        If-Modified-Since	Tue, 13 Sep 2016 01:16:22 GMT

   **post方式提交**

   2:post 请求提交方式的数据格式.

          /day07/mycode/12poPOSTst.php HTTP/1.1
         Host: 127.0.0.1
         Content-Length: 35
         Cache-Control: max-age=0
         Origin: http://127.0.0.1
         Upgrade-Insecure-Requests: 1
         User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.106 Safari/537.36
         **如果是post 提交，一定会有这个请求头**
         Content-Type: application/x-www-form-urlencoded
         Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
         //请求来自于那个页面.
         Referer: http://127.0.0.1/day07/mycode/12post.html
              1:作用，做广告流量统计
              2：防盗链
         Accept-Encoding: gzip, deflate
         Accept-Language: zh-CN,zh;q=0.8
         //请求体，这个请求体是发送到服务器的参数数据
         username=zhangsan&password=zhangsan
-------------------------------------------------------------
### get方式提交和post方式提交的区别

   1. get 提交请求的参数都在地址栏当中。不安全
   2. get 提交没有请求体
   3. get 提交因为请求都在地址栏当中，所以发送给服务器的数据的大小会有限制 1kb 左右
   -------
   1. post 提交请求参数都在请求体当中，数据大小没有限制
   2. 安全
   3. 它必须有一个特殊的请求头
      Content-Type:"application/x-www-form-urlencoded";
---------------------------------------------------------      
### 我们是怎么来完成异步交互：

    我们通过js 给我们提供的一个对象叫做 xmlHttpRequest 对象来完成异步交互的。
    就是通过xmlHttpRequest 发送请求，通过这个对象 xmlHttpRequest 接受数据。

    **首先通过js 提供的对象来发送ajax 请求，这个对象叫做XMLHttpRequest
    /*
    *   1:创建这个对象
    *   2：我要跟服务端的那个资源建立连接
    *   3：发送数据给服务器
    *   4：接收服务器端返回的数据..
    * */

        *1: 创建这个对象
        var xhr=new XMLHttpRequest();
        *2. 建立连接
        //以什么样的方式发送
        //我要请求的服务器的那个资源，我就需要传递一个路径.
        xhr.open("GET","02ajax.php");
        *3. 发送一些数据给服务器
        xhr.send(null);
        *4. 接收数据.. 肯定也是通过xhr  这个对象..
        //这个函数什么时候调用.假设服务器给客户端响应了数据，就会调用这个函数.
        //这个方法会被调用很多次，在交互的过程当中都调用，数据在返回的过程当中都调用.
        xhr.onreadystatechange=function(){
            //我在这里开始接收数据.
            //readyState xmlHttpRequest 对象下面的一个属性
            //我们通过这个属性可以获取到三个值，2,3,4
            //这个2,3,4 其中这个4 代表 服务器端响应的数据已经完成.
            //alert(xhr.readyState);
            //返回的是服务端的状态吗，200 代表，代表响应是没有出错，没有问题.
            //alert(xhr.status);
            if(xhr.readyState==4 && xhr.status==200){
                    //我在这里开始接收数据.怎么去接受服务器端返回的数据
                    //肯定也是通过xhr，使用这个属性来接受服务器返回的数据.
                    var data=xhr.responseText;
                    document.querySelector("div").innerHTML=data;
            }
        }
------------------------------------------------------------
### 数据传递有两种固定的数据格式
1. XML：可扩展的标记语言；
   - xml是自定义的，里面的标签不固定，可以按xml语法去写：
   ```
    //1：xml 的文档声明 声明这个是一个xml格式的文档,xml的目的是用来做输出传递的，并不是数据展示。
        header("Content-Type:text/xml;charset=utf-8");
         <?xml version="1.0"  encoding="UTF-8" ?>
             <books>
                  <bookName></bookName>
             </books>
    //2:有且仅有一个根元素
    //3:可以嵌套，（可以自定义）
   ```
2. json数据格式

- 怎么去使用js 解析json 格式的数据.
      服务端：返回json 格式的数据{"username":"zhangsan","age":11}

      客户端：
      接收数据  xhr.responseText;
      （我们是吧符合json 格式的数据转换成javascript 的对象，然后通过对象.key 获取值）

      转换有两种方式：
            1：通过我们的js 提供的一个函数  eval
                 var data='{"username":"zhangsan","age":11}';
                 var obj=eval("("+data+")")
            2:提供JSON.parse 解析
                 var obj=JSON.parse(data);
            根据key可以获取到value，看value对应的值是什么.
                 var obj='{
                      "username":["zhangsan","lisi","zhaoliu"],
                      "users":[{"username":"congcong"},{"username":"laoduan "}],
                      "bgm":{"username":"cc"} ,
                      "run":"function(){}"}';
                 obj=eval("("+obj+")");      //变成对象
                 //找到zhaoliu
                 obj.username[2];
---------------------------------------------------------                 
### ajax API
1. 指定页面几秒钟后自动跳转，语法：
    > header('refresh:5;url=http://www.baidu.com');  //5s后自动跳转到URL地址
2. 页面休眠
    > sleep(4);   //点击请求后页面需要加载4秒时间才能打开
--------------------------------------------------------    
### jQuery封装了一套ajax操作；提供了一套API，底层封装了XMLHttpRequest这个对象。
- jQuery提供了6个方法来操作ajax，跟后台进行数据交互（从工作角度看，会一个即可）
> $.ajax();

> $.get();   $.post();

> $("div").load();

> $getScript()  $.getJSON();
```
    document.querySelector("#ajaxId").onclick = function() {
        $.ajax({
            url: "01ajax.php",
            type: "get",
            //data 是发送到后台的参数的数据，这个是第一种写法
            //data:"username=zhangsan&age=11&sex=nan",
            //第二种写法，以对象的方式把数据发送到服务端.
            data: {
                username: "wangwu",
                age: 11
            },
            //超时，我现在给服务器发送一个请求，假设服务器过一段时间还没有给我
            //响应，我就断开这个连接
            /* timeout:3000,*/
            //请求发送之前调用.
            beforeSend: function() {
                alert("请求发送之前调用");
                //这个函数如果没有返回值，我的执行顺序
                //beforeSend,success,complete
                //调用不会再去发送请求了.
                return false;
            },
            //这个回调函数，是请求响应完成，并且响应成功的 时候调用.
            success: function(data) {
                alert("请求成功的时候调用");
            },
            // 还有一些回调函数，请求失败的时候调用
            error: function() {
                alert("请求失败的时候调用");
            },
            //完成的意思，请求响应完毕之后调用.
            complete: function() {
                alert("请求响应完成");
            }
        })
    }
```
- 设置timeout:3000;  响应时间为3s超过时间就断开连接
```
$.get("01ajax.php", {
        "username": "zhangsan"
    }, function(data) {
        alert(data);
});
```

```
$.post("03post.php",{
        "username":"songtao"
    },function(data){
        alert(data);
});
```

```
    /*
        * 两种类型的方法，
        *   一种是全局方法:$.ajax()
        *   一种是局部方法：$("div").css();
        *   从后台返回的数据放在当前元素div 里面.
        *
        *   ajax 方法，我可以设置提交方式 ，get ，post
        *   $.GET() 默认就是get 方式提交
        *   $.POST() 默认就是post 方式提交
        *   load 是get 方式提交，还是post 方式提交.
        *   默认提交方式也是get
        *   如果给服务器端发送了参数，就是post 方式提交.
        *
        * */
    $("div").load("04load.php",{"username":"zhangsan"});
```

```
    //去获取远程的一段javascript 脚本
    //需要的时候才去载入这段脚本文件.
    $.getScript("js/script.js");
```

```
    $.getJSON("06json.php", function(data) {
    //我使用别的方法，这里返回的是字符串。
    //我还需要把字符串转换成javascript 对象
    //现在我使用的是getJSON，返回的就已经是对象，
    //我直接获取对象里面的值就可以
    alert(data);})
```

### 跨域问题的解决

1. 主域名相同的跨域问题

```
    <script>
        var iframe = document.querySelector("iframe")
        iframe.onload = function(){
            //在两个页面上都添加这样一行代码
            document.domain = "www.主域名";
            var win = this.contentWindow;
            var btn = win.document.querySelector("#su");
        }
    </script>
```
2.
### JSONP实现跨域
   - Jsonp并不是一种数据格式，而json是一种数据格式，jsonp是用来解决跨域获取数据的一种解决方案，

   >具体是通过动态创建script标签，然后通过标签的src属性获取js文件中的js脚本，该脚本的内容是一个函数调用，参数就是服务器返回的数据，为了处理这些返回的数据，需要事先在页面定义好回调函数，本质上使用的并不是ajax技术.
   

















