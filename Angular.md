- 解决闪烁问题：ng-cloak（原理是：添加style样式,display:none）
- less插件  less  lessc  less2css
- package controll   setting-user  autoCompile:false  minifile:false


# 流行框架第一天：Angular简介和入门

`复习`
###非对称加密

它的原理较为简单，我们假设有消息发送方A和消息接收方B，通过下面的几个步骤，我们就可以完成消息的加密传递：

消息发送方A在本地构建密钥对，公钥和私钥；

消息发送方A将产生的公钥发送给消息接收方B；

B向A发送数据时，通过公钥进行加密，A接收到数据后通过私钥进行解密，完成一次通信；

反之，A向B发送数据时，通过私钥对数据进行加密，B接收到数据后通过公钥进行解密。

## 前端流行技术的历史
- 之前时代，是桌面应用的天下，客户端服务器的天下，本没有前端这样的职位，网站设计师
- 石器时代，互联网开始发展网站设计师（静态）-不过是html、css、js、flash，页面设计师
- 青铜时代，yui、prototype、extjs、dojo等等框架的时代，美工、页面设计师 前端工程师
- 黑铁时代，jquery和jquery的一堆衍生品jqueryui、easyui、ligerui等 ui设计 前端工程师
- 白银时代，angularjs、react
- 黄金时代，现在前端技术和后端平起平坐的时代


## 前端缘何一地鸡毛？
- 一地鸡毛，书名，刘震云的中篇小说，意思是说琐事特别多，并非贬义词。
- 说前端一地鸡毛，既是机遇又是挑战
- 这几年前端技术迅速发展，特别是在nodejs的基础之上发展，
- 分工协作前后端分离，给前端带来的机会



## 什么是库（包），什么是框架？
 - jQuery ：库
  + 封装了一些常用的方法，我们主动的调用这些方法
    -- 提高了代码的利用，以及代码后期的维护

 - Angular: 前端框架
  + 框架提供了一些结构或者模式，
  + 我们是根据框架提供的结构或者模式去书写代码
  + 由框架帮助我们去执行相应的操作。
 
## 什么是 Angular

- 一款非常优秀的前端高级 JS 框架
- 最早由 Misko Hevery 等人创建
- 2009 年被 Google 公式收购，用于其多款产品
- 目前有一个全职的开发团队继续开发和维护这个库
- 有了这一类框架就可以轻松构建 SPA 应用程序
- 单页面应用程序 模拟cs结构 客户端服务器 作出的bs的结构的网站，但是带有客户端的功能性、页面局部刷新特点

- 其核心就是通过指令扩展了 HTML，通过表达式绑定数据到 HTML。
- *Angular不推崇DOM操作，也就是说在NG中几乎找不到任何的DOM操作*



### 安装 Angular


- 暴力安装: 直接从本地硬盘中复制一个angular.js文件到项目中

- 通过工具安装
  + npm 方式 `npm install angular`

  + bower 方式 'bower install angular'
- bower 
 安装 'npm install -g bower'

## CDN - 扩展内容
content delivery network 
内容分发网络

*注意，每一种安装方式，本质都是为了拿到angular.js文件*

### 指令
内置指令
ng- 已ng-开头的标签里面的属性的扩展形式称之为指令
ng-app 告诉angular从这里开管理代码了
ng-model 绑定input输入框的值
ng-click 添加点击事件
ng-init 初始化一个对象的值

### Angular 表达式
{{}}表示一个表达式，像模板引擎
 <p>hello:{{user.name}}</p>
 <p>{{"hello:"+user.name}}</p>
 <p>{{1+1}}</p>
 <p>{{[1,2,3,4]}}</p>
 //注意不能写json或对象
<!--<p>{{{"a":"123"}}}</p>-->
### Angular 的核心特性

- 指令

- MVC

- 模块化  angular.module()

- 双向数据绑定

### 模块(module)
- angular.module('myApp',[])
  > 第一个参数是模块的名字
  > 第二个参数是一个数组，数组的元素是该模块所依赖其他模块的名字
*注意,即使不依赖任何模块，也需要给第二个参数传递一个空数组*
*否则angular.module('myApp')就是去获取名为myApp的模块对象*

### 控制器(controller)
- angular.module('myApp',[]).controller('demoController',function($scope){})
> 第一个参数，是控制器的名字
> 第二个参数，是一个回调函数，在回调函数里写我们想要的js代码。

### 双向数据绑定
- 数据模型的值发生改变，就会导致页面值的改变.
  页面值的改变，就会导致数据模型值的改变，这各种相互影响的关系就是双向数据绑定。
- ng-model

### 单向数据绑定
- 使用表达式显示数据模型的值。
### MVC 思想

### 依赖注入
- AngularJs 内置一些具有特殊功能的“模块”，开发者在开发时可以直接使用这些模块
- 定义控制时，需要使用一个叫做$scope的“模块”
  + 行内注入"数组的形式传入"
```
App.controller('WeatherController', ['$scope', '$http', '$log', function($scope, $http, $log) {

    }])
```
  + 推断式的注入
```
App.controller('WeatherController',function($scope){

    })
```

#### 什么是 MVC 思想
- M:Model 模型  :数据存储，一些业务逻辑
- V:View  视图 ：就是用来展示数据
- C:Controller 控制器: 调度业务逻辑

### 数据模型的调用
//创建一个用户对象
var user = new User($scope.username,$scope.password);
                var e = user.save();
                if(result){
                    $scope.msg='注册成功';
                }else{
                    $scope.msg='用户名已存在';
                }
### 数据模型的建立
        //创建一个构造函数
        function User(username,password){
            this.username=username;
            this.password=password;
        }
        //保存
        User.prototype.save=function(){
            //提取数据，如果没有给一个空数组
            var data = localStorage.getItem('user')||'[]';
            //把提取出来的数据转成json
            var users = JSON.parse(data);
            //循环变量一下数据，看用户是不是已经存在了
            for (var i = 0; i < users.length; i++) {
                var item = users[i];
                if(item.username==this.username){
                    return false;
                }
            }
            //如果用户不存在，则放到users对象里面
            users.push({username:this.username,password:this.password});
            //把数据存储进去
            localStorage.setItem('user',JSON.stringify(users));
            return true;
        }

### $watch
- 用于监视数据模型的变化（并且只能监视数据模型的变化）
- $scope.$watch('数据模型名的字符串形式',function(变化后的值,变化前的值){})
- $scope.$watch里的回调函数会默认执行一次。


- 速度快
- 减轻了服务器自身在带宽压力。

### 学习资料
- AngularJS 1.x 官方网站
  + https://angularjs.org/
- AngularJS 2.x 官方网站
  + https://angular.io/
- Google Material Design for Angular
  + https://material.angularjs.org
- Angular UI（Angular最大的第三方社区）
  + http://angular-ui.github.io/
- AngularJS中文社区
  + http://www.angularjs.cn/
- AngularJS中文社区提供的文档（不用翻墙）
  + http://docs.angularjs.cn/api
  + http://www.apjs.net/
