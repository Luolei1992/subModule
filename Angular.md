- 解决闪烁问题：ng-cloak（原理是：添加style样式,display:none）
- less插件  less  lessc  less2css
- package controll   setting-user  autoCompile:false  minifile:false


# 流行框架第一天：Angular简介和入门
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
`内置指令`

- ng- 已ng-开头的标签里面的属性的扩展形式称之为指令
- ng-app 指定应用根元素，至少有一个元素指定了此属性(angular从这里开始管理代码)
- ng-model 绑定input输入框的值
- ng-click 添加点击事件
- ng-init 初始化一个对象的值
- ng-controller 指定控制器
- ng-show控制元素是否显示，true显示、false不显示
- ng-hide控制元素是否隐藏，true隐藏、false不隐藏
- ng-if控制元素是否“存在”，true存在、false不存在
- ng-src增强图片路径
- ng-href增强地址
- ng-class控制类名
- ng-include引入模板
- ng-disabled表单禁用
- ng-readonly表单只读
- ng-checked单/复选框表单选中
- ng-selected下拉框表单选中

`过滤器`

1. currency将数值格式化为货币格式
2. date日期格式化，年（y）、月（M）、日（d）、星期（EEEE/EEE）、时（H/h）、分（m）、秒（s）、毫秒（.sss），也可以组合到一起使用。
3. filter在给定数组中选择满足条件的一个子集，并返回一个新数组，其条件可以是一个字符串、对象、函数
4. json将Javascrip对象转成JSON字符串。
5. limitTo取出字符串或数组的前（正数）几位或后（负数）几位
6. lowercase将文本转换成小写格式
7. uppercase将文本转换成大写格式
8. number数字格式化，可控制小位位数
9. orderBy对数组进行排序，第2个参数可控制方向

`内置服务`

- $location是对原生Javascript中location对象属性和方法的封装。
- $timeout&$interval对原生Javascript中的setTimeout和setInterval进行了封装。
- $filter格式化数据。
- $log打印调试信息
- $http用于向服务端发起异步请求。
- 同时还支持多种快捷方式$http.get()、$http.post()、$http.jsonp

### Angular 表达式
{{}}表示一个表达式，像模板引擎
 <p>hello:{{user.name}}</p>
 <p>{{"hello:"+user.name}}</p>
 <p>{{1+1}}</p>
 <p>{{[1,2,3,4]}}</p>
 //注意不能写json或对象
<!--<p>{{{"a":"123"}}}</p>-->
### Angular 的核心特性

- AngularJS是以数据做为驱动的MVC框架，所有模型（Model）里的数据经由控制器（Controller）展示到视图（View）中。
- 所谓数据绑定指的就是将模型（Model）中的数据与相应的视图（View）进行关联，分为单向绑定和双向绑定两种方式。

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
