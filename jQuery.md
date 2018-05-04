### jQuery方法
```
var $obj = $(“div”);
$obj.html(“jquery对象设置文本的方法”);
$obj.show();                   //jquery对象显示文本
$obj.click(function() {});     //jquery对象绑定事件
```

```
1. jquery对象转DOM对象
var $li = $(“li”);              //这样写就不用再遍历了
- 第一种方法（推荐使用）
$li[0]
//第二种方法
$li.get(0)            //其实jQuery对象转DOM对象的实质就是取出jQuery对象中封装的DOM对象。
2.DOM对象转jquery对象
var $obj = $(domObj);          // $(document).ready(function(){});就是典型的DOM对象转jQuery对象
```

#### jQuery过滤选择器
> - :eq（index）
> - :odd
> - :even
+ 语法
> $('li:even').css('color', 'red');  //设置样式.css

> $("#one").css({
>    "background":"gray",
>    "width":"400px",
>    "height":"200px"
> });

> $("div").css("background-color");  //获取样式

#### jQuery筛选选择器
> children(selector)    
  - $(“ul”).children(“li”)  相当于$(“ul>li”)，子类选择器
> find(selector)    
  - $(“ul”).find(“li”); 相当于$(“ul li”),后代选择器
> siblings(selector)    
  - $(“#first”).siblings(“li”);  查找兄弟节点，不包括自己本身。
> prevAll()  //前面的兄弟元素

> nextAll()  //后面的兄弟元素

> next() 当前元素的下一个兄弟元素
> parent()  
  - $(“#first”).parent();      查找父亲
> eq(index) 
  - $(“li”).eq(2);  相当于$(“li:eq(2)”),index从0开始

### class操作
> $(“div”).addClass(“one”); //给所有的div添加one的样式。

> $(“div”).removeClass();  //移除div所有的样式类

> $(“div”).removeClass(“one”);  //移除div中one的样式类名

> $(“div”).hasClass(“one”);  //判断第一个div是否有one的样式类

> $(“div”).toggleClass(“one”);  //需要切换的样式类名，如果有，移除该样式，如果没有，添加该样式。

#### 显示和隐藏
- show方法详解：
> show([speed], [callback]);

1. speed(可选)：动画的执行时间
2. 如果不传，就没有动画效果。
3. 毫秒值(比如1000),动画在1000毫秒执行完成(推荐)
4. 固定字符串，slow(200)、normal(400)、fast(600)，如果传其他字符串，则默认为normal。
5. callback(可选):执行完动画后执行的回调函数
- hide方法详解：与show方法的用法完全一致。
> show/hide：修改的是元素的width、height、opacity。

#### 滑入和滑出
- slideUp/slideDown,使用方法与show/hide基本一致。
> slideUp(speed, callback);
1. speed(可选)：动画的执行时间
2. 如果不传，默认为normal，注意区分show/hide。
3. 毫秒值(比如1000),动画在1000毫秒执行完成(推荐)
4. 固定字符串，slow(200)、normal(400)、fast(600)
5. callback(可选):执行完动画后执行的回调函数

- slideUp/slideDown：修改的是元素的height;

**滑入滑出切换**

> $(selector).slideToggle(speed,callback);

- 如果是隐藏状态，那么执行slideDown操作，如果是显示状态，那么执行slideUp操作。

#### 淡入和淡出
- fadeIn/fadeOut使用方法与show/hide、slideDown/slideUp一致。
> fadeIn(speed, callback);
1. speed(可选)：动画的执行时间
2. 如果不传，默认是normal。
3. 毫秒值(比如1000),动画在1000毫秒执行完成(推荐)
4. 固定字符串，slow(200)、normal(400)、fast(600)
5. callback(可选):执行完动画后执行的回调函数

**淡入淡出切换**
- fadeToggle(speed, callback);
> 如果当前元素处于隐藏状态，那么执行fadeIn操作，如果处于显示状态，那么执行fadeOut操作。
*淡入淡出到某个值*


- fadeTo(speed, value, callback)//可以设置具体的透明度
> 与淡入淡出的区别：淡入淡出只能控制元素的不透明度从 完全不透明到完全透明；而fadeTo可以指定元素不透明度的具体值。并且时间参数是必需的！
1. speed（必须）
2. value  0-1之间的数值(比如0.4)，表示淡到某一个值。
3. callback(可选) 回调函数

*fade系列方法：修改的是元素的opacity*

#### animate：自定义动画
> $(selector).animate({params},[speed],[callback]);
1. {params}：要执行动画的CSS属性，带数字（必选）
2. speed：执行动画时长（可选）
3. callback：动画执行完后立即执行的回调函数（可选）

+ 6easing参数
1. 控制动画在不同元素的速度，默认为“swing”
2. “swing”：在开头和结尾移动慢，在中间移动速度快
3. “linear”：匀速移动

- stop方法：停止动画效果
> stop(clearQueue, jumpToEnd);
1. 第一个参数：是否清除队列
2. 第二个参数：是否跳转到最终效果
3. 最常用的停止动画：stop();

### jquery操作DOM(节点)
1. 创建元素

> $(“<span>这是一个span元素</span>”);
 
2. 添加元素
- 方法一：将jQuery对象添加到调用者内部的最后面。

> var $span = $(“<span>这是一个span元素</span>”);

> $(“div”).append($span);

- 方法二：参数传字符串，会自动创建成jquery对象

> $(“div”).append(“<span>这是一个span元素</span>”);

3. 添加已经存在的元素

> var $p = $(“p”);

> $(“div”).append($p);

> 注意：如果添加的是已经存在的元素，那么会把之前的元素给干掉。（类似于剪切的功能）。

**类似的用法：append  prepend  after before**

4. 使用html方法创建元素
- 设置内容

> $(“div”).html(“<span>这是一段内容</span>”);
- 获取内容

> $(“div”).html()

5. 清空元素
- empty：清空指定节点的所有元素，自身保留(清理门户)

> $(“div”).empty();//

- 清空div的所有内容（推荐使用，会清除子元素上绑定的内容，源码）

> $(“div”).html(“”);//使用html方法来清空元素，不推荐使用，会造成内存泄漏，绑定的事件不会被清除。

6. 删除元素
- remove：相比于empty，自身也删除（自杀）

> $(“div”).remove()

7. 克隆元素

> $(selector).clone();

# jQuery
```
1. DOM操作
    1.1  属性操作(很重要)
        attr：css用法一样
            设置单个属性：attr(name, value)
            设置多个属性：attr(json)  {"name":"value","name1":"value1"..}
            获取属性：attr(name)  如果是多个元素，返回第一个的元素对应的值

        prop : checked selected disabled

    1.2 val操作表单值  value
        val():不传参数，就是获取
        val(value):传参数，就是设置

    1.3 html与text
        html():获取，能获取到标签+内容
        text():获取，会丢弃标签
        html(value): 设置内容，能识别html标签
        text(value):设置内容，会对html标签进行转义

    1.4 width()和height()
        width():获取宽度
        width(value):设置宽度
        height():获取高度
        height(value):设置高度

    1.5 offset()  能设置(不带单位)能获取，，相对的是document
        position(): 只能获取，相对于有定位的父元素
        position()获取，css进行设置

    1.6 scrollTop()和scrollLeft()
        scrollTop():获取
        scrollTop(value):设置


        css(name):获取
        css(name,value):设置
        attr(name):获取
        attr(name,value):设置



2. 事件机制
    2.1 发展历程   简单事件---》bind事件(子绑定到父，新创建的子元素不会被绑定事件) ---》delegate事件(父委托子，新创建的子元素也会被绑定事件)  -->on事件
    2.2 on注册事件的两种方式(重点)
        给自己机本身注册： $("div").on("click", function(){})
        注册委托事件：$("div").on("click", "p" , function(){})

    2.3 事件解绑
        off():解绑所有的事件
        off("click"):解除click事件
        off("click", "**");只解除委托事件

    2.4 事件触发
        click()
        trigger("click")
        triggerHandler("click"):不会触发浏览器的默认行为
        
    2.5 事件对象
        pageX和pageY
        event.preventDefault():
        event.stopPropagation():
        return false;//既能阻止浏览器默认行为，也能阻止事件冒泡
        event.keyCode:键盘事件
        //event.data:就是用来存储一些数据的
        $("div").on("click", {name:"zs",money:"100"}, function (event) {
            alert("哈哈哈，我有"+ event.data.money);
        });
    *******//jquery可以自动的释放掉$的控制权,有一个返回值
        //这个返回值就替代了之前jquery里面$的作用。
        `var c = $.noConflict();`
        c(function () {
            c("div").width(100).height(100).css("backgroundColor","red");
        });

    
    display:box;
    box-orient: vertical;
    line-clamp: 2;
    overflow: hidden; 

    插件：jquery.lazyload.js,jquery.color.js,jquery.ui.js....
```


