> element.children;    // 获取子代元素
> parent.appendChild(sub);     //添加子元素到最后面
> element.removeChild();       //移除指定元素
> document.createElement("tagName")     //创建元素
> element.cloneNode(boolean)    //克隆节点(深度赋值：赋值标签和内容)
> 字符串方法(判断是否能匹配字符串中的字符，-1不在，1存在)  str.indexOf('');
> arr.sort(function(){});   //参数必须是个函数，规定排序规则
> typeof a            //判断数据类型（typeof [] ==> object）
> a instanceof b         //判断a是否为b(构造函数)的实例


> Math.max(1,2,3,4,5)
> Math.min(1, 2, 3, -4, 5)
> Math.ceil(3.1)
> Math.floor(3.1)
> Math.round(3.1)    //round   数值+0.5 然后取floor
> Math.abs(-1)       //绝对值
> Math.pow(2, 10)    //2的10次方
> Math.sqrt(9)       //根号9


> var date = new Date();   //当前的日期
> console.log(date);     //默认调用一个方法：toString()
> console.log(date.toString());  //同上效果相同
```
var date = new Date();//
    var year = date.getFullYear();//年
    var month = date.getMonth() + 1;//月
    if(month < 10) {
        month = "0" + month;
    }
    var day = date.getDate();//日
    if(day < 10) {
        day = "0" + day;
    }
    var hour = date.getHours();//时
    if(hour < 10) {
        hour = "0" + hour;
    }
    var minute = date.getMinutes();//分
    if(minute < 10) {
        minute = "0" + minute;
    }
    var second = date.getSeconds();//秒
    if(second < 10) {
        second = "0" + second;
    }
    var str = year + "-" + month + "-" + day + " " + hour + ":" + minute + ":" + second;
    console.log(str);
```


### 数组方法
//从后面推入，从数组后面添加元素,返回数组的长度
> arr.push("");
//从前面加,从数组的前面添加元素，返回数组的长度
> arr.unshift('');
//从后面删除元素，返回的是删除的那个元素
> arr.pop('');
//从前面删除元素，返回的是删除的那个元素
> arr.shift('');
//reverse:会改变原来的数组,数组翻转
> arr.reverse();
//合并：合并数组
> arr1.concat(arr2);
//包含begin，不包含end(截取数组,得到新数组，原数组不变)
> arr1.slice(1, 3);
//第一个参数：start  开始删除的位置
//第二个参数：deleteCount:删除的个数
//第三个参数：要添加进数组的内容(得到删除的数组，原数组改变)
> arr1.splice(1, 2 , "宋经济","老宋");
> arr.split("/");         //以/来切割得到数组
//第一个参数：需要查找的元素
//第二个参数：开始找的索引，不传这个参数默认是0，找到第一个就停止查找
> arr.indexOf(1,1);
//lastIndexOf()：从后面开始找
> arr.lastIndexOf(1);

> charAt(index);    //字符串的index值
> stringObject.substr(start,length)    //包括开始的和结束的，传一个参数就截取到最后，可传负数
> arr.substring(start,length);//包括开始的不包括结束的，传一个参数就截取到最后，不支持负数参数

> Array.concat( ) 连接数组
> Array.join( ) 将数组元素连接起来以构建一个字符串 
> Array.length 数组的大小
> Array.pop( ) 删除并返回数组的最后一个元素  
> Array.push( ) 给数组添加元素 
> Array.reverse( ) 颠倒数组中元素的顺序 
> Array.shift( ) 将元素移出数组 
> Array.slice( ) 返回数组的一部分 
> Array.sort( ) 对数组元素进行排序 
> Array.splice( ) 插入、删除或替换数组的元素 
> Array.toLocaleString( ) 把数组转换成局部字符串 
> Array.toString( ) 将数组转换成一个字符串 
> Array.unshift( ) 在数组头部插入一个元素
> Object.hasOwnProperty( ) 检查属性是否被继承 
> Object.isPrototypeOf( ) 一个对象是否是另一个对象的原型 
> Object.propertyIsEnumerable( ) 是否可以通过for/in循环看到属性 
> Object.toLocaleString( ) 返回对象的本地字符串表示 
> Object.toString( ) 定义一个对象的字符串表示 
> Object.valueOf( ) 指定对象的原始值








