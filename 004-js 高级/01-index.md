[TOC]







# 一. ECMAScript 6 入门

建议看 阮一峰 的书:

http://es6.ruanyifeng.com/#docs/intro



https://www.babeljs.cn   专门测试 ES6 与 ES5 之间的差异



在线画图:

https://www.processon.com



并不是所有的浏览器都支持es6语法, 我们在开发的时候使用es6 语法, 当项目上线后为了支持所有的浏览器需要把es6的代码转换为es5





## 1. ES6 变量的声明



### 1. ES6 中变量 & 常量



- 在ES6 中使用 **let**  声明变量

  ```
  // 相当于ES5中的var , 但是又有不同
  let num = 20;
  ```

- 在ES6 中, 同一个作用域内, 不能声明相同的变量, 如下, 是错误的

  ```
  <script> 
      // ES 6 不允许这样, 直接报错
      let a = 10;
      let a = 20;
      console.log(a);
  </script>
  ```

  - 但是在ES5 中是允许的

    ```
    <script>
        // ES 5 中允许这样 重复定义
        var num = 20;
        var num = 30;
        console.log(num); 
    </script>
    ```

- 在ES6 中函数的形参和函数内的变量名不能重名

  ```
  <script>
    function  fn(x) {
        console.log(x);  
        // 不允许这样, 直接报错  `Identifier 'x' has already been declared` 
        let x = 20;
        console.log(x);  
    }
    fn(10)
  </script>
  
  ```

  - 但是在ES5中是允许的

    ```
    <script>
      function  fn(x) {
          console.log(x); // 打印10
          var x = 20;
          console.log(x); // 打印20
      }
      fn(10)
    </script>
    ```

- ES6 中let 声明的变量只在自己的作用域内有效

  - for循环中使用let 和 var 的定义变量的差异差异

    - ES6 中, 只能在{}内使用

      ```
      <script> 
      		// 变量i只能在 {} 内使用
          for(let i=0; i<10; i++){ 
          }
          // 直接报错:Uncaught ReferenceError: i is not defined
          console.log(i);
      </script>
      ```

    - ES5 中, 是全局变量

      ```
      <script>  
          for(var i=0; i<10; i++){ 
          }
          console.log(i); // 结果为10
      </script>
      ```

      



### 2. ES6 声明常量

- 在ES6 中使用**const** 声明常量, 常量在定义是必须赋值且不能被修改

  ```
  // 一但赋值后就不能改了 
  <script>  
      const AGE = 18;
  </script>
  ```

  > 在 ES5 中没有常量这一说法





## 2. ES6 中字符串 (很好用)

- 有点像模板字符串的概念

  > ${} 中间放表达式即可  

```
<script> 
    let body = document.querySelector('body');
    let info = {name:'zhangsan', age:18, height:1.88};
    let ul = `<ul>
                <li>${info.name}</li>
                <li>${info.age}</li>
                <li>${info.height}</li>
              </ul>`
    body.innerHTML = ul;
</script>
```



## 3. ES6 中函数的特点

### 1.ES6 中函数可以设置默认值

```
<script> 
    function fn(num = 10) {
        console.log(num);
    }
    fn(); // 打印结果是10
    fu(5); // 打印结果是5
</script>
```

> 需要注意的是, ES6 中如果函数有多个参数, 设置默认值只能从右往左设置
>
> function fn(num = 10, age,name) // 错误写法
>
> function fn( age,name,num = 10) // 正确写法

- ES5 中函数不能设置默认值

  ```
  <script> 
  		// ES5 中函数设置默认值需要这样做
      function fn() {
          var n = num || 10
          console.log(n);
      }
      fn(); // 打印结果是10
      fu(5); // 打印结果是5
  </script>
  ```



### 2. ES6 中支持箭头函数

```
let fn = ()=> {
	console.log('箭头函数')
}
fn()
```











# javaScript 高级

快捷键

- `itar` 

  ```
  for (var i = 0; i < array.length; i++) {
  	var obj = array[i];
  }
  ```

  





## 一、 javaScript 的组成



### 1、 DOM

>  Document Object Model 文档对象模型, 为了我们方便的操作HTML中的标签元素, 提供了一系列的方法.
>
> 其实没有DOM 也可以操作HTML元素, 只是很麻烦而已

```
document.body ; // 获取body元素
```



### 2、 BOM

> Browser Object Model 浏览器对象模型, 它里面提供了一些方法, 可以让你对浏览器进行一些操作/ 交互, 其中最重要的就是 `window` 对象

```
window.open(); // 打开一个创库
window.open('https://baidu.com'); // 打开百度页面
```



### 3、 ECMAScript

> ECMAScript 是一个语法标准, 它规定了javaScript的核心语法.



## 二、javaScript 中的数据类型



### 1、基本(简单)数据类型 (5种)

- **string** 字符串
- **number** 数值 (整数 | 小数)
- **boolean** 布尔 (true | false)
- **undefined** 未定义
- **null** 空



### 2、复杂(复合)数据类型

- **object** 对象
- **Array** 数组对象
- **Date** 日期对象
- **function** 函数
- **String** 字符串对象 (基本包装型)
- **Number** 数值对象 (基本包装型)
- **Boolean** 布尔对象 (基本包装型)





### 3、 判断数据类型

#### 1、判断数据类型的方法

 我们通过关键字 **typeof** 判断一个变量 或者一个数据的数据类型, 其语法格式如下:

```
typeof 变量\数据
```

> typeof 判断返回的值的类型是 `string` 基本数据类型



#### 2、基本数据类型的判断 (有坑)

```
<script>

    var str = '123';
    console.log(str, typeof str); // string

    var num = 123;
    console.log(num, typeof  num); //number

    var bl = true;
    console.log(bl, typeof  bl); // boolean

    // 注意: 
    // null 并不是一个对象, 但是通过 typeof 打印出来的时候是 object, 这是因为
    // js 这门语言当初在设计的时候的一个错误, 这个错误 官方在很早就已经承认了
    var nl = null;
    console.log(nl, typeof  nl); // null | (object)
    // 判断 nl 是否是Object 类型的对象
    console.log(nl instanceof Object); // false

    var a ;
    console.log(a, typeof a); // undefined

    // var c = 20;  其实等价于下面两句
    //    var c ;  // 声明
    //    c = 20;  // 赋值 (定义)

</script>
```

![Snip20191206_2](Snip20191206_2.png) 

#### 3、复杂数据类型的判断

```
<script>
    var obj = {
        name: 'zhangsan',
        age:18
    };
    console.log(obj, typeof  obj);   // object

    var arr = [1,2];
    console.log(arr, typeof  arr);  // object
    // 通过 typeof 操作复杂数据类型时, 数据类型都是 object, 函数除外

    function  fn() {}
    console.log(typeof  fn); // function 
</script>
```

![Snip20191206_1](Snip20191206_1.png) 





## 三、 等于和全等 详解 (有坑)



### 1、等于和全等说明

- 赋值号: `=` 

- 等于号: `==`

  > 判断左右两边是否相等
  >
  > 只判断值

- 全等于号:`===`

  > 判断左右两边是否相等
  >
  > 不仅判断值, 还判断类型



### 2、等于和全等 示例 



```
<script>
    var str1 = '123';
    var str2 = '123';
    var num1 = 123;

    console.log(str1 == str2);      // true
    console.log(str1 === str2);     // true
    console.log(str1 == num1);      //true
    console.log(str1 === num1);     //false


    console.log(null == undefined);     //true
    console.log(null === undefined);    //false


    var arr1 = [1,2,3];
    var arr2 = [1,2,3]; 
    console.log(arr1 == arr2);  //false
    console.log(arr1 === arr2); //false

</script>
```





### 3、 null 和 undefined 说明



1. 什么时候变量的值为 `null`

   变量的值永远不可能为`null` , 只有手动给变量赋值为`null` 后变量的值才为`null`.

   ```
   var a = 20;
   这句话, 其实要这样理解:
   首先, var a = 20 ; 等价于下面2句:
   var a;
   a = 20;
   
   其中, var a; 相当于是在内存中申请一个变量(可以理解为一个装东西的盒子)
   a = 20; 相当于是让变量a 指向20 (或者理解为把20装进变量 a 的盒子)
   ```





## 四、关系运算符 (返回值是布尔)



### 1、 关系运算符有哪些

- 大于: `>`

- 小于: `<`

- 大于等于: `>=`

- 小于等于: `<=`

- 不等于:

  - `!=`
  - `!==`

  > 关系运算符一般用在条件判断, 其返回值都是boolean 值

  ```
  var a = 10;
  var b = 20;
  if (a > b){
  	console.log('a > b');
  }
  ```





## 五、逻辑运算符



### 1、逻辑运算符有哪些 (详解- 有坑)

- 逻辑非: `!` , 取反

- 逻辑或: `||`   *短路运算符* 

- 逻辑与: `&&`   *短路运算符* 

   

### 2、逻辑非: `!` , 取反 (返回值布尔)



> 语法: `! 表达式` 
>
> 返回结果是 boolean

```
<script>
    console.log(!0); // true
    console.log(!2); // false
    console.log(!null); // true
    console.log(!undefined); // true
    var arr = [1,2];
    console.log(!arr);  // false
</script>
```



### 3、逻辑或: `||`   (返回值表达式)

> 语法:  ` 表达式1 || 表达式2`
>
> **注意:** 返回结果不一定是布尔类型, 结果是其中一个表达式的结果 
>
> 如果表达式1为真, 返回表达式1
>
> 如果表达式1为假, 返回表达式2 
>
> 
>
> (坑) 要说明的是, js 中的逻辑或(||) 与C语言中的逻辑或是不一样的概念, C语言逻辑或后只能是 真或假

```
<script>

    console.log(true || false); // true
    console.log(false || true); // true
    console.log(0 || 0);    // 0
    console.log(0 || 1);    // 1
    console.log(1 || 0);    // 1
    console.log(1 || 1);    // 1
    console.log(2 || 3);    // 2
    console.log(null || [1, 2]);    //  [1, 2]
    console.log([1, 2] || null);    //[1, 2]
    console.log(undefined || {name: 'zhagnsan'});   // {name: "zhagnsan"}
    console.log({name: 'zhangsan'} || undefined );  // {name: "zhangsan"}
</script>
```



### 4、逻辑与: `&&`  (返回值表达式)

> 语法: 表达式1 && 表达式2
>
> 结果: 不一定是布尔类型
>
> 表达式1为假, 返回表达式1
>
> 表达式1为真, 返回表达式2

```
<script>

    console.log(true && false); // false
    console.log(false && true); // false
    console.log(0 && 0);    // 0
    console.log(0 && 1);    // 0
    console.log(1 && 0);    // 0
    console.log(1 && 1);    // 1
    console.log(2 && 3);    // 3
    console.log(null && [1, 2]);    //  null
    console.log([1, 2] && null);    //null
    console.log(undefined && {name: 'zhagnsan'});   // undefined
    console.log({name: 'zhangsan'} && undefined );  // undefined
</script>
```



## 六、 值类型和引用数据类型

### 1、 值类型

`string` `number` `boolean` `undefined` `null`



### 2、 引用类型

`object` `Array` `Function` `Date` ...



### 3、 值类型和应用类型的区别

- 值类型存储的是具体的数据
- 引用类型存储的是引用 (内存地址) 

![Snip20191206_3](Snip20191206_3.png) 



### 4、 值类型和引用类型的赋值



#### 1、 值类型赋值

- 默认会把赋值符号`=` 右边的存储的信息**(具体数据)**复制一份给左边 

  ```
  <script>
    var a = 10;
    var b = a;
    b = 20;
    console.log(a); // 10
    console.log(b); // 20
  </script>
  ```

  > 特点:
  >
  > 只是简单的数据复制, 相互之间独立

#### 2、 引用类型赋值 

- 把赋值符号`=` 右边的存储的信息**(指向具体数据的地址)**复制一份给左边

  ```
  <script>
      var  obj = {
          name: 'zhangsan'
      }
      var obj1 = obj;
      console.log(obj.name);  // zhangsan
  
      obj1.name = 'ls';
      console.log(obj.name);  // ls
      console.log(obj1.name); // ls
  </script>
  ```

  > 特点:
  >
  > 共享同一份数据, 修改其中一个对象属性的值, 会影响另外一个

  ![Snip20191206_7](Snip20191206_8.png)  

- 思考:

  ```
  <script>
      var  obj = {
          name: 'zhangsan'
      }
      var obj1 = obj;
      console.log(obj.name);  // zhangsan 
      obj1.name = 'ls';
      
      obj1 = {des: 'des'}
      console.log(obj.name);  // ls
      console.log(obj1.name); // undefined
      console.log(obj.des); 	// undefined
      console.log(obj1.des); 	// des
  </script>
  ```

- 回顾, 理解

  ```
  <script>
    var arr1 = [1,2,3]; // 0x123
    var arr2 = [1,2,3]; // 0x223
    console.log(arr1 == arr2);  //false   (0x123 != x223 ) 值不相等
    console.log(arr1 === arr2); //false   (0x123 != x223 ) 值不相等, 肯定类型也不同
  </script>
  ```





### 5、 值类型和引用类型在函数中的使用

- 实参: 实际参数
- 形参: 占位用的, 函数调用之前形参没有值
- 函数的调用: 默认会把实参赋值给形参



#### 1、值类型作为函数参数

- 值类型作为函数的参数时(值传递), 实参和形参之间是独立的

  ```
  <script>
      var a = 10;
      function fun(num) { 
          console.log(num);   // 10
          num = 20;
          console.log(num);   // 20
          console.log(a);     // 10
      }
      fun(a);
  </script>
  ```

  

#### 2、 引用类型作为函数的参数

- 引用类型作为函数的参数时(地址传递),  形参和实参之间会共用一分数据之间相互影响

  ```
  <script>
      var obj = {name:'zs'}
      function fn(obj1) {
          console.log(obj1.name); //zs
  
          obj1.name = 'ls';
          console.log(obj1.name); //ls
          console.log(obj.name);  //ls
      }
      fn(obj)
  </script>
  ```






## 七、 对象的动态特性



### 1、js对象的动态特性

可以对已经创建好的对象 `增加` `修改` `删除` 属性或方法



### 2、访问对象的属性

js中的对象, 既可以使用点语法`.`访问属性, 也可以使用方括号`[]` 访问属性,操作基本都是差不多的, 不过还是有一些差异, 比如说: 

- `[] 语法` ,只能通过属性名(字符串) 访问对象的属性

- `. 语法` , 不能通过属性名(字符串) 访问对象的属性

  > `for in obj` 中使用 [] 语法访问对象属性

  

#### 1、点语法

```
<script>
    // 1. 创建一个对象 (key - value)
    var obj = {
        name: '张三',
        age:18
    }

    // 2. 动态增加属性 | 方法
    obj.des = '我是张三,年龄18'; 
    obj.logDes = function () {
        console.log(this.des);
    }

    console.log(obj.des);
    obj.logDes();

    // 3. 修改属性
    // 通过点语法操作对象的时候, 已经存在的属性就修改, 如果不存在就添加
    obj.des = 'des'
    console.log(obj.des);


    // 4. 删除属性
    delete  obj.des;
    console.log(obj.des); // undefined

</script>
```

> 通过点语法操作对象的时候, 已经存在的属性就修改, 如果不存在就添加
>
> 使用 `delete 关键字` 删除对象的属性



#### 2、[] 语法 (和点语法差不多)

```
<script>
    // 1. 创建一个对象 (key - value)
    var obj = {
        name: '张三',
        age:18
    }

    // 2. 动态增加属性 | 方法
    obj['des'] = '我是张三,年龄18'; 
    obj['logDes'] = function () {
        console.log(this['des']);
    }

    console.log(obj['des']);
    obj['logDes']();

    // 3. 修改属性
    // 通过[]语法操作对象的时候, 已经存在的属性就修改, 如果不存在就添加
    obj['des'] = 'des'
    console.log(obj['des']);


    // 4. 删除属性
    delete  obj['des'];
    console.log(obj['des']); // undefined

</script>
```

> 通过 [] 语法操作对象的时候, 已经存在的属性就修改, 如果不存在就添加
>
> 使用 `delete 关键字` 删除对象的属性





## 八、关键字



### 1、 in 关键字 介绍

- `in` 关键字主要用在以下几个地方:
  - `for … in … ` 遍历对象的属性
  - `key in obj`判断对象的某个属性是否存在
  - `index in array` 判断数组某个索引是否有值



### 2、  in 关键字 具体使用

#### 1、for … in... 遍历对象中所有的key(属性名)



- 通过`for…in…` 遍历对象时, 遍历到的是属性的名字

  >  属性名只能使用 []语法访问属性值

```
<script>
    var obj = {
        name: "张三",
        age: 18,
        height: 1.88
    }

    for (var key in obj){
        console.log(key, obj.key);
    }
    console.log('------------');
    for (key in  obj){
        
        console.log(key, obj[key]);
    }
</script>
```

![Snip20191206_9](Snip20191206_9.png) 





#### 2、属性名 in 对象  判断对象{}中是否存在指定的属性 



> 通过属性名 in 对象, 判断对象中是否存在指定的属性时, **属性名一定是字符串**
>
> 格式: `keyName in obj` 

```
<script>
    var obj = {
        name: "张三",
        age: 18,
        height: 1.88
    }

    console.log('name' in obj);     // true
    console.log('age' in obj);      // true
    console.log('height' in obj);   // true 
    console.log('test' in obj);     // false
    obj.name = null;
    console.log('name' in obj);     // true
</script>
```

> 注意:
>
> - `key in obj` 在操作` (key - value) 的对象`时, 判断的是 obj 这个对象中是否存在名字为 key 的属性, `key` 必须是字符串, `obj` 必须是一个 `{name: value}` 的对象
> - `key in obj` 只判断对象中是否有这个名字的属性, 与具体的属性值是`null` 或 `undefined` 无关





#### 3、index in array , 判断数组中指定索引是否有值



> - 通过 `index in array` 判断数组中指定索引位置是否有值, index 只能是正数
>
> - 只要索引 `index` 对应的位置有值, 不论是`undefined`  还是`null` 还是其它都为 true, 只有该位置的元素被删除了或根本没元素才为 false

```
<script> 
    var arr1 = ['a','b','c','d','e','f']
    // 判断索引1位置是否有值
    console.log(1 in arr1);     // true
    console.log('a' in arr1);   // false

    var arr2 = [1,,3,4,5,6,7]
    console.log(1 in arr2);     // false
    console.log(arr2[1]);       // undefined
    console.log(2 in arr2);     // true
    console.log(arr2[2]);       // 3

    var arr3 = [1,2,3,4,5,6,7]
    console.log(1 in arr3);     // true
    arr3[2] = null;
    console.log(arr3[2]);       // null
    console.log(2 in arr3);     // true


    delete  arr3[3]
    console.log(arr3[3]);       // undefined
    console.log(3 in arr3);     // false
</script>
```





### 3、 delete 关键字



#### 1、 delete 关键字删除对象某个属性

```
<script>
    var obj = {
        name : "zhangsan",
        age: 18
    }

    console.log(obj.name);	// zhangsan
    delete obj.name;
    console.log(obj.name);	// undefined

</script>
```



#### 2、delete 关键字, 可以直接删除未使用 var 声明的变量

```
<script> 
    // 未使用var 声明的变量是一个全局变量, 会自动成为 window 的属性
    a = 10;
    console.log(a); // 10
    console.log(window.a);  // 直接报错

    var b = 20; // 20
    delete  b;      // 无法使用delete 删除var 声明的变量
    console.log(b); // 20 
</script>
```

> 注意:
>
> - 使用var 声明的变量, 是无法使用delete 关键字删除的
> - 使用 var 声明的变量, 要使用 `delete window.属性名` 的方式才能删掉
> - 未使用 var 声明的变量被delete 关键字删除掉后再次被访问会直接报错
> - 访问使用 delete关键字删除掉的对象属性时, 返回值是undefined
> - 有返回值, 是布尔类型, 删除成功 true , 删除失败 false 







## 九、异常处理



### 1、 异常处理的结构

```
try {

} catch(e){

}
```



### 2、 异常的处理 (程序执行的常识)

-  在正常的情况下, 程序在执行过程中, 如果出现了错误或者异常, 后面的代码都不会被执行

  ```
  <script> 
      function  demo() {
          console.log('demo');
      }
      var a = 10;
      a();  // 这一行报错, 后面不会再执行了
      demo();
  </script>
  ```

  ![Snip20191206_11](Snip20191206_11.png) 

- 但是, 在有的时候, 我们需要保证即使程序出现了错误或者异常, 后面的代码还是可以继续执行

  这时, 我们就需要使用 `try{}catch(e){}` 来捕获对应的错误, 保证后面的代码继续执行

  ```
  <script>
  
      // 在正常的情况下, 程序在执行过程中, 如果出现了错误或者异常, 后面的代码都不会被执行
  
      function  demo() {
          console.log('demo');
      }
      var a = 10;
      try{
          // try 里面书写可能出现错误的代码
          a();  // 这一行会报错
      }
      catch (e){
          // 如果 try 里面的代码出现了错误, 就会执行这个大括号
          // 一般这里需要对错误进行一些处理
          console.log(e);
      } 
      demo();
  </script>
  ```

  ![Snip20191206_10](Snip20191206_10.png) 





### 3、 手动抛出异常

在有些时候程序的执行过程中, 我们需要手动的抛出异常

```
<script> 
    try {
        var a ;
        // 使用throw 手动抛出异常
        throw 'a 未定义';
    }
    catch (e) {
        console.log(e);
    }
</script>
```

> throw + 异常信息 (字符串 | 对象)
>
> 很多公司要求是对象:
>
> 1001 : 变量未定义
>
> 1002 : 不合法的参数
>
> 1003 : …   

```
<script> 
    try {
        var a ; 
        throw {// 使用throw 手动抛出异常
        	error: 'a 未定义',
        	code: 1001
        };
    }
    catch (e) {
        console.log(e);
    }
</script>
```



### 4、异常的完整结构 (*) 

```
<script> 
    try {
        var a ;
        // 使用throw 手动抛出异常
        //throw 'a 未定义';
    }
    catch (e) {
        console.log(e);
    }
    finally {
        // 不论前面是否抛出异常, finally 中的代码都会被执行
        console.log('无论抛不抛异常, 这句代码都会被执行了');
    }
</script>
```

> 上面的代码书写和下面的代码书写, 在效果上是一样的

```
<script> 
    try {
        var a ;
        // 使用throw 手动抛出异常
        //throw 'a 未定义';
    }
    catch (e) {
        console.log(e);
    } 
    console.log('无论抛不抛异常, 这句代码都会被执行了');
</script>
```



> 上面的两端代码, 都会执行最后一句`console.log('无论抛不抛异常, 这句代码都会被执行了');` , 那么这两端代码到底有什么区别呢? 

是这样的哈, `finally{}` 这个数据块在前端开发中一般不会使用, 因为前端开发中一般不会关心内存飙升的 ,但是在后端就不一样了, 因为服务器是 24 消失不关机的, 所以后端开发人员需要严格的管理内存的问题, 特别是内存飙升, 否则程序宕机.

`try {} catch(e){}finally{}` 中的fianlly 一般使用在当程序出现异常后使用一些内存资源的, 如果资源得不到释放, 最终系统内存被耗尽就会宕机.







## 十、 调试工具的使用

`f12` 打开浏览器调试工具

![Snip20191206_12](Snip20191206_12.png) 







## 十一、循环和分支



### 1、循环

- `for .. in`

- `for`

- `while`

- `do… while`

  ```
  <script>
      var obj = {
          name: 'zhangsna',
          age: 18
      }
      for(var key in obj){
          console.log(key);
      }
      
      for(var i=0; i< 10; i++){
          console.log(i);
      }
      
      var a = 10;
      while (a > 0){
          a --;
          console.log(a);
      }
      
      do {
          a++;
          console.log(a); 
      }while(a < 10)
  </script>
  ```

  



### 2、分支

- `if .. else`

- `switch .. case`

  ```
  <script>
    if (a > 0){
    
    }
    else{
  
    }
  
  // js 中的switch 没有 break 会 穿透
    switch (b){
      case 0:
        console.log('00');  
        break;
      case 1:
        console.log('11');
        break;
      default:
        break;
    }
  </script>
  ```

  



## 十二、 DOM 操作



### 1、DOM 的简单操作

- 要求:

  - 创建一个div标签
  - 设置标签的样式
  - 添加到页面中
  - 获取到新创建的div标签
  - 删除这个标签

  ```
  <script>
      // 1. 创建一个div标签
      var div = document.createElement('div');
  
      // 2. 设置标签的样式
      div.innerHTML = '我是一个div';
      div.style.width = '200px';
      div.style.height = '200px';
      div.style.background = 'red';
  
      // 3. 添加到页面
      document.body.appendChild(div);
  
      // 4. 获取到新创建的div标签
      var div1 = document.querySelector('div');
      
      // 5. 删除这个标签
      document.body.removeChild(div1); 
  </script>
  ```





## 十三、函数和对象的创建



### 1、函数的创建 (3种方式)



#### 1、声明函数



- 使用function 关键字声明函数

  > 格式:
  >
  > function  函数名(形参1, 形参2...) {	
  >
  > ​	// 函数体
  >
  > }

  ```
  <script>
      function  函数名(形参1, 形参2...) {
      }
      
      function  sum(a, b){
      	return a + b;
      }
  </script>
  ```

#### 2、函数表达式(方式)

- 函数表达式 创键函数

  ```
  <script>
  		// 匿名的函数表达式
      var fun1 = function () {
      }
      
      // 命令的函数表达式
      var fun2 = function demo(){ 
          console.log('demo');
      } 
      fun2(); 
      // demo(); 不能再使用demo 调用了
  </script>
  ```

#### 3、使用Function 构造函数, 创建函数

- Function 构造函数 

  ```
  <script>
  		// 使用Function构造函数, 创建一个函数实例
      var fun = new Function();
  </script>
  
  // 上面使用Function构造函数, 创建的函数实例, 等价于下面 
  <script>
     function fun(){
     }
  </script>
  上面2种方式创建的函数, 函数体里面都是空的, 没有执行内容
  ```

  - 通过Function构造函数创建的函数实例, 如果需要有执行语句, 需要使用字符串传参, 如下:

    ```
    <script>
        var fun = new Function("console.log('使用Function构造函数')");
        fun(); 
    </script>
    
    // 等价于下面
    <script> 
      function fun() {
         console.log('使用Function构造函数')
      } 
      fun();
    </script>
    ```

    





