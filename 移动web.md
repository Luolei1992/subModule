### 移动web
#### 像素是一个相对长度单位，像素并并没有固定长度
#### PPI像素密度，计算方法勾股定理
- 屏幕尺寸固定时，当PPI 越大，像素的实际大小就会越小，当PPI越小，像素实际大小就越大。
#### 设备独立像素
- 为了保证图像内容在不同的PPI设备上看上去大小差不多，这就是独立像素。
- IOS设备上叫PT(Point)，Android设备上叫DIP(Device independent Pixel)或DP
### 获取屏幕的物理像素尺寸
> window.screen.width
> window.screen.height
- CSS像素指的是通过CSS进行网页布局时用到的单位，其默认值(PC端)是和物理像素保持一致的（1个单位的CSS像素等于1个单位的物理像素），但是我们可通缩放来改变其大小

### viewport视口
1. 获取视口大小(取决于浏览器窗口大小，以css像素作为长度)
> document.documentElement.clientWidth;

> document.documentElement.clientHeight;

*移动设备上viewport不再受限于浏览器的窗口，而是允许开发人员自由设置viewport的大小，通常浏览 器会设置一个默认大小的viewport，为了能够正常显示那些专为PC设计的网页，一般这个值的大小会大于屏幕的尺寸。*

2. 视口类别

 - layout viewport（布局视口）指的是我们可以进行网页布局区域的大小，同样是以CSS像素做为计量单位，可以通过下面方式获取

+ 获取layout viewport

> document.documentElement.clientWidth;

> document.documentElement.clientHeight;

通过前面介绍我们知道，如果要保证为PC设计的网页在移动设备上布局不发生错乱，移动设备会默认设置一个较大的viewport（如IOS为980px），这个viewport实际指的是layout  viewport。

- ideal viewport（理想视口）设备屏幕区域，（以设备独立像素PT、DP做为单位）以CSS像素做为计量单位，其大小是不可能被改变，通过下面方式可以获取。

// 获取ideal viewport有两种情形

// 新设备

> window.screen.width;

> window.screen.height;

// 老设备
> window.screen.width / window.devicePixelRatio;

> window.screen.height / window.devicePixelRatio;

> **layout  viewport   <=  idea  viewport**(避免出现滚动条)

## 浏览器适配

> \<meta name="viewport" content="width=device-width,initial-scale=1">

> initital-scale设置页面的初始缩放值，为一个数字，可以带小数。

> maximum-scale允许用户的最大缩放值，为一个数字，可以带小数

> minimum-scale允许用户的最小缩放值，为一个数字，可以带小数。

> user-scalable是否允许用户进行缩放，值为"no"或"yes"。

> **注：device-width 和 device-height就是ideal viewport的宽高**

###　长度单位

- em 相对长度单位，其参照当前元素字号大小，如果当前元素未设置字号则会继承其祖先元素字号大小

- rem 相对长度单位，其参照根元素(html)字号大小例如 html {font-size: 16px;} 则 1rem = 16px

## 媒体查询

#### 关键字

关键字将媒体类型或多个媒体特性连接到一起做为媒体查询的条件。

1. and 可以将多个媒体特性连接到一起，相当于“且”的意思。
2. not 排除某个媒体类型，相当于“非”的意思，可以省略。
3. only指定某个特定的媒体类型，可以省略。

#### 引入方式

1. link方法

> \<link href="./5-1.css" media="only screen and (max-width: 320px)">

2. @media方法

```
@media only screen and (max-width:320px){
    body {
        background-color:red;
    }
}
```

#### 常用特性

1. width / height完全等于layout viewport
2. max-width / max-height 小于等于layout viewport
3. min-width / min-height 大于等于layout viewport
4. device-width / device-height 完全等于ideal viewport
5. orientation: portrait | landscape肖像/全景模式

## CSS预处理器

- 常见的CSS预处理器有：LESS、SASS、Stylus等
- 引用<link rel="stylesheet/less" type="text/css" href="styles.less" />

## 触屏事件

1. 事件类型

> touchstart: 手指触摸屏幕时触发

> touchmove: 手指在屏幕上移动时触发

> touchend: 手指离开屏幕时触发

2. TouchEvent  对象

> touches: 位于屏幕上的所有手指的列表

> targetTouches: 位于该元素上的所有手指的列表

> changedTouches：touchstart时包含刚与触摸屏接触的触点，touchend时包含离开触摸屏的触点

3. Touch 对象

> clientX/Y       手指相对于layout viewport的水平/垂直像素距离

> pageX/Y     手指相对于layout viewport的水平/垂直像素距离（含滚动） 

> screenX/Y       手指相对于layout viewport的水平/垂直像素距离（含滚动）
    （未设置viewport时，screenX/Y在Webview中不正确）

> target          手指最初与屏幕接触时的元素

移动开发通常会设置 \<meta name="viewport" content="width=device-width, initial-scale=1">，这时这三对坐标值是完全一样的。  

4. click 延时
5. tap检测接触和离开屏幕的距离来实现，见代码示例7-5.html,drag跟踪手指移动位置，进而设置元素定位坐标，见代码示例7-6.html,swipe 判断手指滑动的方向
6. zepto.js
- zeptojs为我们封装了常的触屏事件，需要touch模块支持
7. 移动端类库
- iScroll
- swipe.js
- fastclick.js（在移动设备上为了提升click的响应速度，我们选择了使用Zepto事件封装的tap来进行模拟，但是这会带来一个副作用，这个副作用就是“点透”，我们通过一个例子来解释“点透”）
8. 网页布局
    1. 固定宽度布局：为网页设置一个固定的宽度，通常以px做为长度单位，常见于PC端网页。
    2. 流式布局：度为网页设置一个相对的宽，通常以百分比做为长度单位。
    3. 栅格化布局：将网页宽度人为的划分成均等的长度，然后排版布局时则以这些均等的长度做为度量单位，通常利用百分比做为长度单位来划分成均等的长度。
    4. 响应式布局：通过检测设备信息，决定网页布局方式，即用户如果采用不同的设备访问同一个网页，有可能会看到不一样的内容，一般情况下是检测设备屏幕的宽度来实现。

9. css框架
- bootstrap
- Amaze UI
- Framework7

*移动浏览器*

- 实现省略号的写法

```
    display: -webkit-box;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    word-break: break-all;
```

+ 移动web：原生开发打包，嵌入h5页面
+ webApp：全部都是H5开发的应用
+ 混合APP：使用第三方开发平台从apicloud，appcan，hbuilder等开发，cordova技术打包
+ 原生APP：就是eclipse开发或者studio等工具开发

- 解决默认行高问题
    1. 法一
        + 设置line-height为1
        + 再用padding来挤
    2. 法二
        + 设置line-height为120%
    3. 法三
        + 设置line-height为1.2
- 行高继承问题
    1. 父盒子设置line-height为百分比时，子盒子继承的是父盒子字号的百分比
    2. 父盒子设置line-height为数字，子盒子继承的是数字乘以自己字号的数字倍

**页面惯性滑动属性设置**

`-webkit-overflow-scrolling:touch;`

### less解析

- 全局安装`npm install -g less`
- 命令：`lessc test.less test.css`

#### 语法(查看文档具体语法)

```
@color:red;
.border(@r){        //默认参数写法.border(@r:10px){}
    -webkit-border-radius:@r;
    -o-border-radius:@r;
    -moz-border-radius:@r;
    border-radius:@r;
}
.box {
    color:@color;
    .border(10px);  //如果上面定义的有参数就需要传参数，或者写默认参数
}
```

- 引入less.js解析
    + \<link rel="stylesheet/less" href="index.less">
    + \<script src='less.js'></script>
