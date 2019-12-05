

# javaScript



# 一、 script 标签书写的位置



## 1、script标签的书写规范



1. script标签可以放在html文档的任何位置, 但是一般不要乱写.

2. 建议书写的位置(2个)

   - `head` 的开始标签和结束标签之间
   - `body` 结束标签之前

   ```
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
   
       <style>
           
       </style>
       <script>
           // script 标签建议书写的位置一
       </script>
   </head>
   <body>
   
   <script>
       // script   标签建议书写的位置二 (更推荐)
   </script>
   </body>
   </html>
   ```





## 2、浏览器解析HTML文档顺序

1. 浏览器会从`HTML文档`的**第一行开始逐行解析** `HTML标签`
2. 当解析到`head标签`时, `head标签` 内可能会包含一些外部文件的引入标签,比如: `link`  , 当解析到时就开始下载这些外部引入文件
3. 当解析到 `style` 标签时会跳过, 暂时不解析`style` 标签内容
4. 当在`head` 标签内遇到`script` 标签时, 浏览器会暂停解析(不是暂停下载, 没下载完的文件继续下载), 将控制权交给`javaScript引擎` , 由`javaScript引擎执行完毕javaScript脚本`  执行完毕后会将控制权再交回浏览器, 浏览器继续解析后面的标签
5. `head` 标签解析完毕后就开始解析`body` 标签, 如果在`body` 标签中遇到`script`  标签后, 浏览器又会暂停解析, 将控制权交给`javaScript引擎`  , `javaScript 引擎` 将脚本执行完成后再将控制权交回给浏览器, 由浏览器继续解析
6. 当浏览器解析完毕`body` 标签后并且所有的CSS样式加载完毕, CSS 就会重新渲染整个页面的HTML元素.



>  有了浏览器解析HTML文档顺序的了解后, 我们就会发现, 如果`script` 标签写在`head` 内, 当`javaScript引擎`  执行javaScript 脚本时, HTML还没开始解析, 就会出现找不到HTML节点的问题, 因此我们推荐script 标签写在最后一个body 前面.



>  有人又会说, 为什么我们不把`script` 标签写在整个 `HTML` 文档的最后呢? 这样也不会出现`javaScript引擎` 找不到HTML节点的问题, 

>  虽然写在最后可以解决问题, 但是这就和我们整个html文档的内容分开了, 破坏了结构性语义. 因此推荐下载最后一个body的前面.





# 二 、 javaScript 中的变量



## 1、 变量的命名规则

- 变量只能由字母(a~z A~Z) 数字(0~9) 下划线(_) 美元符($) 组成,

- 变量不能以数字开头

- 变量区分大小写 (var a 和 Var A 不是同一个变量 )

  > javaScript 中推荐使用驼峰命名 lastName  firstName





## 2、 变量数据类型

### 1 、javaScript 中的数据类型有7种:

- 字符串
- 数字
- 布尔
- 数组
- 对象
- Null
- Undefined



### 2、 javaScript 拥有动态数据类型

- 这意味着同一个avaScript 变量可用作不同的类型

  ```
  
  ```





## 3、变量提升

### 1、 局部变量

- 在函数内部通过`var` 声明的变量称为局部变量, 局部变量只能在函数内部使用

  ```
  <script>
      // 全局变量
      var a = 10;
      
      function fn() {
          // 局部变量
          var  b = 20; 
          // 全局变量
          c = 220
          
          console.log(a);
          console.log(b);
      }
      fn();
  
      console.log(c);
  </script>
  ```

  



### 2、变量提升 (ES6之前可以)

使用变量在定义变量之前, 就称为变量提升, 如下示例:

```
面试题

var num = 10;
function fn() {
	console.log(num); // 变量num 会被提升
	var num = 20;
}
fn(); // 打印结果为 undefined


上面的代码等价于下面的写法
var num = 10;
function fn() {
	var num;
	console.log(num);
	num = 20;
}
fn();

```





## 4. javaScript 中的变量使用前必须先定义



```
console.log(num); //执行结果为 undefined , 因为变量提升
var num = 20;
```

