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











# javaScript 高级(js入门介绍)

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

#### 1、判断数据类型的方法(2种情况)

-  关键字 **typeof**  获取一个变量 或者一个数据的数据类型(返回值是string), 其语法格式如下:

  ```
  // 格式: 
  typeof 变量\数据
  // 示例:
  console.log(typeof "abc"); // 获取 "abc" 的数据类型
  ```

  > typeof 判断返回的值的类型是 `string` 基本数据类型

- 关键字 **instanceof** 判断一个数据是否是某个类型(返回值是 布尔)

  ```
  // 格式: 
  nl instanceof type;
  
  // 示例:
  console.log(@"abc" instanceof string); // true
  ```

  



#### 2、基本数据类型的判断 (有坑)

> null 是基本数据类型, 但是通过 typeof 判断出的结果却是 object 类型, 这是官方承认的错误

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

#### 3、复杂数据类型的判断(有坑)

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



### 1、等于(==)和全等(===)说明

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





## 八、关键字- in、delete



### 1、 in 关键字 介绍

- `in` 关键字主要用在以下几个地方:
  - `for … in … ` 遍历对象的属性
  - `key in obj`判断对象的某个属性是否存在
  - `index in array` 判断数组某个索引是否有值



### 2、 in 关键字 具体使用(有坑)

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
> - 返回值是boolean





#### 3、index in array , 判断数组中指定索引是否有值



> - 通过 `index in array` 判断数组中指定索引位置是否有值, index 只能是正数
>- 只要索引 `index` 对应的位置有值, 不论是`undefined`  还是`null` 还是其它都为 true, 只有该位置的元素被删除了或根本没元素才为 false
> - 返回值是boolean

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



#### 1、delete 关键字删除对象某个属性

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
> - 使用 delete 删除 不存在的属性, 返回值也是true







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



#### 1、方式一(声明函数)

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

#### 2、方式二(函数表达式)

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

#### 3、方式三(使用Function 构造函数, 创建函数) 

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

    





### 2、对象的创建

```
<script>
	var obj = {
		name: 'zhangsan'
	}
	
	var obj1 = new Object(); // 等价于 var obj1 = {};
	
</script>
```





## 十四、面向对象和面向过程编程



1. 不论是面向对象还是面向过程, 其实都是解决问题的一种思想(思路)



>  区别: 关注点不一样
>
> - 面向过程, 更加关注的是解决问题的一个一个的步骤(细节)
> - 面向对象, 更加关注解决问题所需要的对象



## 十五、面向对象编程的相关概念

 



1. 什么是对象?

   什么都是对象, 万物皆对象

   一般的对象指的是具体的事物

2. 静态的描述信息

   姓名/ 性别/ 身高/ 头发颜色

3. 动态的行为特征

   睡觉/ 吃饭/ 打游戏

4. 现实生活中的对象 和  js中的对象

   静态的描述信息  <---> 属性 (定义在对象中的变量)

   动态的行为特征 <—> 方法 (定义在对象中的函数)





## 十六、前面知识复习



1、JS 组成: DOM、BOM、ESMAJavaScript

2、数据类型:

​	基本数据类型: string number boolean null undefined

​	复杂数据类型: object Array Function Number String Boolean Date ...

3、获取数据类型: typeof

​	typeof null —> object

​	typeof 函数 —> function

​	返回值是 boolean

4、 判断数据类型 instanceof

​	"abc" instanceof string  —> true

5、

​	等于==, 判断值

​	全等===, 判断值 和 类型

6、 逻辑运算

​	逻辑非 (!),  !表达式  —> 取反, 结果为boolean

​	逻辑或(||), 短路或

​		表达式1 || 表达式2, 表达式1为true,返回表达式1, 否则返回表达式2

​	逻辑与(&&), 短路与

​		表达式1 && 表达式2, 表达式1为false, 返回表达式1, 否则返回表达式2

7、 

​	值类型: 基本数据类型

​	引用类型: 复杂数据类型

​	区别: 存储的信息不一样, 值类型存储的是值, 引用类型存储的是地址

​	

​	值类型的赋值, 简单的数据复制, 相互独立不影响

​	引用类型赋值: 引用地址复制, 会共用一份数据, 相互关联影响



8、函数调用

​	默认把实参的数据复制给形参

​	值类型作为函数参数: 实参和形参是独立的

​	引用类型作为函数的参数: 实参和形参共用一份数据

9、对象的动态特定

​	可以为已经创建好的对象, 增加、 删除、 修改属性

10、 属性的访问

​	点语法

​	[]语法

​	点语法和[]语法基本用法差不多, 只是在使用场景上有差异

11、关键字 in

 	for … in,遍历所有的属性名,通过属性名只能使用[]语法访问属性

​	 判断对象{}是否有对应名字的属性, 属性名 in obj

​	 判断数组指定缩影是否有值, index in arr

​	 返回值是 boolean

12、

​	 删除对象的某个属性, delete 对象.属性 或者 delete 对象[属性名]

​	delete 可以直接删除未使用 var 声明的变量

​	不能删除使用var 声明的属性, 但是可以使用 delete window.属性

​	返回值是boolean

​	使用delete 删除根本不存在的属性, 返回值也是true

13、异常处理

​	try{// 写可能异常的代码}catch(e){// 异常发生会来这里}finally{// 无论有误异常都会执行这句}

 	异常的处理,就是为了保证程序发生异常后仍然执行, 而不是终止执行

​	finally{} 块的目的是释放一些资源











# javaScript 高级 (面向对象)





## 一、 面向对象的三大特性

所有的面向对象的语言都有这三大特性

- 封装
- 继承
- 多态



### 1、javaScript 中的封装

-  在js封装的实现, 就是使用一个对象把一些`变量`和`函数` 包裹起来, 就称为**封装**  

- 封装的作用: 提高代码的复用性, 便于代码维护, 隐藏细节

  ```
  <script> 
      var name = "一出好戏"
      var actors = ['黄渤', '王宝强', '王迅']
      var type = "喜剧"
      var showTime = "2018"
      var play = function () {
          console.log('播放一出好戏');
      }
  
      // 下面操作就是对上面的封装
  
      var film = {
          name: "一出好戏",
          actors: ['黄渤', '王宝强', '王迅'],
          type: "喜剧",
          showTime: "2018",
          play: function () {
              console.log('播放一出好戏');
          }
      }
  </script>
  ```



### 2、javaScript中的继承

- 程序中的继承: 

  - 一个类(对象)获取另外一个类(对象)的属性和方法

    >面向对象语言的一个判断重要判断依据: 有没有类的概念
    >
    >- 一般来说我们根据一个语言有没有类的概念来判断它是不是面向对象的语言, 比如: (C++, Java, OC…) 这几个语言都是有累的概念, 因此我们称他们是面向对象的语言.  但是传统的javaScript 语言它并没有类的概念, 从这个角度来说的话, 你可以说javaScript不是面向对象的语言. 因为它没有类的概念.  但是javaScript 它有真实的 `封装` `继承` 和 `多态` 的概念(面向对象的三大特性), 从面向对象三大特性来说javaScript 又是面向对象的语言, 所以说看一个问题,要看你从哪个角度去看, 不同的角度有不同的结果
    >
    >因此,我们说 javaScript 是面向对象的语言 (有三大特性)

  - 属性拷贝继承 (混入式继承)

    ```
    <script> 
        var obj1 = {
            name : "张三",
            age: 18,
            des:"姓名:张三, 年龄:18"
        }
        var obj2 = {};
        // obj2 想要获取obj1 的属性和方法
        // 属性拷贝 (混入式继承)
        for (var key in  obj1){
            obj2[key] = obj1[key];
        } 
        console.log(obj2);
    </script>
    ```

    

  



### 3、javaScript 中的多态

- 多态:

  - 对于同一个操作, 不同的对象有不同的行为

  - JS 天生就具备多态的特性(弱类型语言)

    > javaScript 是弱类型语言
    >
    > 具体javaScript 中的多态是什么, 我们在讲函数传参的时候就明白了









## 二、javaScript 中创建对象的方式(4类)



### 1、字面量方式创建对象(代码冗余,无法区分类型)

- 字面量创建对象 (json对象)

  > 特点: 创建好的对象,无法附庸, 有大量的重复代码 (代码冗余度过高) 
  >
  > 只需要创建简单的对象是, 很快捷

  ```
  <script> 
      var obj = {
          name: "zhangsan",
          age:18,
          paly:function () {
              console.log("玩耍");
          }
      }
  </script>
  ```

  

 

### 2、内置的构造函数创建对象(代码冗余,无法区分类型)

- 什么是内置构造函数?

  > 所谓的内置构造函数就是说, 这个构造函数是系统提供的, 不是你自己写的.  有代表性的内置构造函数如下:
  >
  > `Object` `Array` `Date` `Function` `String` `Number` `Boolean` 

- 使用内置构造函数创建对象 (示例)

  > 内置构造函数和字面量创建对象的特点都差不多, 代码无法复用

  ```
  <script> 
      var stu1 = new Object(); // 等价于  var stu = {}
      stu1.name = "zhangsan";
      stu1.age = 18
  </script>
  ```

   

### 3、 简单的工厂函数创建对象(无法区分类型)

- 提供一个函数把创建对象的过程封装起来

  > 解决 了 `字面量创建对象 和 内置构造函数创建对象` 代码无法复用的代码

  ```
  <script>
      // 提供一个函数把创建对象的过程封装起来
       function  createStu(name, age) {
           var obj = new Object();
           obj.name = name;
           obj.age = age;
           study = function () {
               console.log(this.name);
           }
           return obj;
       }
       
        function  createDog(name, age) {
           var obj = new Object();
           obj.name = name;
           obj.age = age;
           run = function () {
               console.log(this.name + '在跑' );
           }
           return obj;
       }
  
       var s1 = createStu('张三', 18)
       var d1 = createDog('wangcai', 1)
       console.log(s1);
       console.log(d1);
       
       
       console.log(typeof s1); //object
       console.log(typeof d1); //object
  </script>
  ```

  ![Snip20191209_1](Snip20191209_1.png) 

  > 简单工厂函数创建对象的方式, 虽然解决了代码复用性的问题, 但是依然引入了一个问题:
  >
  > 通过简单工厂函数方式创建的不同的对象都是一个类型 (object)类型, 无法更详细的判断详细类型(人 狗 不分), 在以后的开发中, 我们无法根据具体的类型来做对应的事情

​		





### 4、 自定义构造函数创建对象(有坑)(重点)

- 提供一个构造函数(自己写的) 

  > 构造函数首字母大写(规范) 
  >
  > 构造函数内不需要使用return

- 通过`this`设置对象的属性和方法

- 使用`new`构造函数创建对象 

  ```
  <script>
      function  Person(name, age) {
          // 通过this给狗仔函数设置属性 和 方法
          this.name = name;
          this.age = age;
          this.des = function () {
              console.log("姓名:" + this.name + ",年龄: " + this.age);
          } 
          // 构造函数内不需要调用 return
      }
  
      var p1 = new Person('zhangsan', 18)
      var p2 = new Person('lisi', 19)
      console.log(p1);
      console.log(p2);
  
      console.log(typeof  p1);
      console.log(typeof  p2); 
  </script>
  ```

  - 自定义构造函数和工厂函数的区别

    - 首字母大写

    - 需要使用new 关键字 调用构造函数 (工厂函数不需要)

    - 默认会自动创建一个对象, 不需要手动创建 (工厂函数需要)

    - 默认会自动返回这个对象 (工厂函数需要手动返回)

      - 如果主动使用return 返回简单的数据类型会被忽略, 还是默认返回的构造对象

        ```
        function  Person(name, age) {
          // 通过this给狗仔函数设置属性 和 方法
          this.name = name;
          this.age = age; 
          // 返回的任然是 Person
          return "abc";
        }
        ```

      - 如果主动使用return 返回复杂数据类型, 那么默认返回的构造对象会被覆盖

        ```
        function  Person(name, age) {
          // 通过this给狗仔函数设置属性 和 方法
          this.name = name;
          this.age = age; 
          // 返回的任然是 [1,2,3]
          return [1,2,3];
        }
        ```

        



#### 1 、自动一构造函数注意项1(函数传值&对象类型&构造器属性)



##### 1、函数传值 (多态特性)

- 把一个函数作为构造函数的参数

  > 这也就体现了 javaScript 的多态特性 (不同的对象, 调用同一个方法. 表现出不同的结果)
  >
  > 这就是为什么我们说, javaScript 天生就具备多态特性

  ```
  <script>
      // 函数作为构造函数的参数 
      // 体现javaScript 的多态特性
      function  Person(name, age, show) {
          this.name  = name;
          this.age = age;
          this.show = show;
      }
      
      var p1 = new Person('zhagnsan', 18, function () {
          console.log(this.name);
      })
      
      var p2 = new Person('lisi', 20, function () {
          console.log(this.age);
      })
      
      // javaScript 的多态特性
      p1.show();  // zhangsan
      p2.show();  // 20
  </script>
  ```

  

##### 2、判断对象的类型

- 通过 `对象  instanceof  构造函数` 可以判断对象是否是通过指定构造函数创建出来的

  > 注意:
  >
  > 虽然通过`对象  instanceof  构造函数`可以判断,某个对象是否是通过指定构造函数创建出来的
  >
  > 但是, 通过 `typeof 对象` 获取到的仍然是 `object` 类型

  ```
  <script>
      function Person(name, age){
          this.name = name
          this.age = age
      }
  
      function Dog(name, age){
          this.name = name
          this.age = age
      }
  
      var p1 = new Person('zhagnsan', 18)
      var d1 = new Dog('wangcai', 2)
  
      console.log(typeof p1);	//object
      console.log(typeof d1); //object
      
      console.log(p1 instanceof Person);  // true
      console.log(p1 instanceof Dog);			// false
      
      console.log(d1 instanceof Dog);			// true
      console.log(d1 instanceof Person);	// false
  
  </script>
  ```



##### 3、获取对象的类型 (构造器属性) 

- 对象有一个`constructor` 属性, 可以获取它的构造函数

  ```
  <script>
      function Person(name, age){
          this.name = name
          this.age = age
      }
  
      var p = new Person('zhangsan', 18)
      console.log(p.constructor);
  
      var obj = {}
      console.log(obj.constructor);
  
  </script>
  ```

  ![Snip20191209_2](Snip20191209_2.png) 





#### 2、构造函数注意事项2(函数调用 & this)

- 通过new 去调用构造函数时, 构造函数的 `this` 就是新创建的对象

- 直接调用构造函数`(不使用new 调用)`, 构造函数内部是不会创建对象的, 此时, 构造函数内的`this`为`window`

  ```
  <script>
      function Person(name, age){
          console.log(this);
          this.name = name
          this.age = age
      }
  
      var p = new Person('zhangsan', 18)    // this = p
      // 不建议这样直接调用构造函数, 因为此时的this代表的是window
      // 可能就不小心修改了window的属性和方法了, 可能会出现误操作
      var p = Person('lisi', 20)  // this = window
  
  </script>
  ```

  >其实哈, `new` 和构造函数是有分工的.
  >
  >- `new`: 创建对象, 返回对象
  >- `构造函数`: 对 对象进行初始化设置





####3、 自定义构造函数的问题

虽然我们通过自定义构造函数, 可以解决`字面量对象` 和`内置构造函数`  代码冗余的问题, 解决了`工厂函数` 对象不能判断类型的问题, 但是自定义构造函数仍然有问题, 什么问题呢? 

> 自定义构造函数, 多个对象内的同名函数, 各个函数是独立不同的, 造成代码冗余
>
> 每个对象都有一个函数, 这样内存多浪费啊

```
<script>
    function  Person(name) {
        this.name = name;
        // 每个对象内都有一个新的 play 方法
        this.play = function () {
            console.log(this.name + '在play');
        }
    }

    var p1 = new Person("zhagnsan")
    var p2 = new Person("lisi")

    console.log(p1.play == p2.play); // false

</script>
```

> 通过自定义构造函数创建的对象, 可能会造成, 资源重复浪费的情况















## 三、 知识回顾总结

1、 面向对象的三大特定

​	封装: 使用对象封装(包裹)一些变量和函数

​	继承: 一个类(对象)获取另外一个类(对象) 的属性和方法 (混入式继承)

​	多态: 对于同一个操作, 不同的对象有不同的行为. (函数作为构造函数的参数实现)

2、创建对象的方式

​	字面量创建, 代码重复,冗余

​	内置构造函数, 代码重复冗余

​	工厂函数, 解决了代码冗余, 对象类型不能判断

​	自定义构造函数, 解决了代码冗余, 对象类型判断, 但是新增了,方法冗余的问题









## 四、构造函数的原型对象



### 1、什么是构造函数的原型

- 构造函数在创建出来的时候, 系统默认就会创建一个对象与之相关联, 这个对象就称为构造函数的原型对象

  > 原型对象是系统创建的

- 约定:

  > - 该对象 构造函数的原型对象那个
  > - 构造函数的原型
  > - 构造函数的原型对象
  > - 对象的原型对象
  > - 对象的原型
  >
  > 以上几种说法, 说都都是一个意思

### 2、原型对象的作用

- 通过构造函数创建出来的对象, 默认就可以使用原型对象的属性和方法



### 3、访问原型对象

- 使用构造函数的 `prototype` 属性访问构造函数的原型对象

  ```
  <script>
      function  Person(name) {
          this.name = name;
          this.play = function () {
              console.log(this.name + '在play');
          }
      } 
      // 访问构造函数的 原型对象
      console.log(Person.prototype); 
  </script>
  ```



### 4、设置原型对象(2种)

- 原型对象的本质就是一个对象, 利用对象的动态特性设置原型对象
- 替换原型





## 五、使用原型对象解决自定义构造函数创建对象的问题

- 属性 设置在构造函数内部

- 方法设置在原型对象上

  ```
  <script>
      function Person (name){
          // 1. 属性设置在构造函数内部
          this.name = name;
      }
      
      // 2. 方法设置在构造函数的原型上
      Person.prototype.show = function () {
          console.log(this.name);
      }
      
      var p1 = new Person('zhangsan')
      var p2 = new Person('lisi')
      
      p1.show();  // zhangsan
      p2.show();  // lisi
  
      console.log(p1.show == p2.show); // true   
  </script>
  ```

  



## 六、实例化和实例 



- 实例化
  - 通过构造函数创建对象的过程, 称为实例化

- 实例:

  - 通过构造函数创建出来的对象就是一个实例. 一般说实例时要说明是哪一个构造函数的实例

    > 比如: 你可以说  xxx实例 是XXX构造函数的实例

> 一句话, 实例化是一个过程, 实例是一个对象



## 七、原型的使用方法



### 1、 利用对象的动态特性设置原型对象

- 构造函数的原型对象是构造函数创建后, 系统自动添加的对象

- 只有通过构造函数才能访问原型对象, 通过构造函数的实例不能访问构造函数的原型对象, 但是通过实例对象能访问到构造函数的原型对象的属性和方法

- 构造函数原型对象中的属性和方法, 只能通过构造函数修改, 不能 通过实例修改, 实例只能访问属性和方法

  ```
  <script>
      // 利用对象的动态特性, 我们可以给构造函数的原型对象 增加 删除 修改 属性和方法
  
      function Person (){
      }
  
  
  
  
      // 1. 为构造函数的原型对象 动态增加属性和方法
      Person.prototype.des = 'des'
      Person.prototype.logDes = function () {
          console.log(this.des);
      }
  
      // 2. 实例化 对象, 通过对象访问构造函数的原型对象的属性和方法
      var p1 = new Person();
      console.log(p1.des);
      p1.logDes();
  
      // 3. 修改构造函数原型对象 中的方法 和 实例
      Person.prototype.des = '修改后的 des'
      Person.prototype.logDes = function () {
          console.log('修改后的' +  this.des);
      }
      console.log('--修改后-------');
      console.log(p1.des);
      p1.logDes();
  
  
      // 4. 删除构造函数的原型对象中的属性和方法
      
      
      delete Person.prototype.des;
      delete Person.prototype.logDes;
  
      console.log('--删除后-------');
      console.log(p1.des);
      p1.logDes();
  
  
  </script>
  ```

  >
  >
  >构造函数才有原型对象
  >
  >实例对象没有原型对象
  >
  >构造函数可以直接访问原型对象
  >
  >实例对象不能访问原型对象, 但是能访问原型对象的  属性和方法



### 2、替换原型

1、 为甚么我们要有替换原型的需求呢? 

如下代码段, 当我们要个构造函数的原型添加很多的属性和方式时, 每次都要一个个的添加太麻烦而且容易出错

```
<script>
    function Person(){
        
    }
    Person.prototype.des = 'des'
    Person.prototype.test = 'test'
    Person.prototype.log = 'log'
    // 一直这样写下去, 好繁琐
</script>
```

- 原型替换示例

  > 替换原型的使用场合:
  >
  > 需要设置的属性 和 方法很多时, 通常我们会使用原型替换

  ```
  // 自定义构造函数
  function Person (){
  }
  
  // 自定义对象
  var obj = {
  	des: 'des',
  	test: 'test',
  	log: 'log'
  }
  
  // 替换原型
  Person.prototype = obj
  ```

  



### 3、替换原型的注意点

- **修改** 原型前和修改原型后, 创建的实例对象的对比

  ```
  <script>
      function Person() {
  
      }
  
      var p1 = new Person()
      // 修改原型对象
      Person.prototype.des = 'des'
      var p2 = new Person()
  
      console.log(p1.des);  // des
      console.log(p2.des);  // des
      
      console.log(p1.constructor == p2.constructor); // true
  
  </script>
  ```

  > 修改原型前后修改原型后, 不同实例对象访问的原型对象是同一个

  

- **替换** 构造函数的原型对象之前和之后, 原型对象不是同一个

  ```
  <script>
      function Person() {
  
      }
  
      var p1 = new Person()
      // 替换原型对象
      Person.prototype= {
      	des:'des'
      }
      var p2 = new Person()
  
      console.log(p1.des);  // undefine
      console.log(p2.des);  // des
      
      // 当访问对象的 constructor 属性时, 真实是访问的是原型对象的constructor属性
      console.log(p1.constructor == p2.constructor); // false
  
  </script>
  ```

  > 替换原型之前和替换原型之后, 不同的对象访问的不是同一个原型对象



- 结论: 

  > 为了不引起意向不到的错误
  >
  > - 尽量避免, 创建对象后替换原型对象
  > - 原型对象的替换, 尽可能在创建对象之前



### 4、对象的constructor 属性

- 当我们在访问一个 对象的`construtor` 属性时, 默认访问的其实是其内部原型的 `constructor` 属性

- 当一个构造函数的`prototype` 原型对象是默认的原型对象时(即, 没有替换过构造函数的原型对象), 原型对象的`construtor` 指向的就是构造函数本身

- 当一个构造函数的`prototype` 原型对象被替换过, 那么对象的`constructor` 指向的就是, 替换的原型对象的`constructor` 对象

  ```
  <script>
      function Person() {
  
      }
  
      var p1 = new Person() 
      var obj =  {des: 'des'}
      Person.prototype= obj
      var p2 = new Person()
   
      console.log(p1.constructor);
      console.log(p2.constructor);
   
      console.log(p1.constructor == Person);
      console.log(p2.constructor == obj.constructor);
  
  
  </script>
  ```

  ![Snip20191209_3](Snip20191209_5.png)  

  

  ![Snip20191209_4](Snip20191209_4.png) 

  > 一句话, 默认的原型对象有`constructor` 属性, 就是构造函数本身.
  >
  > 替换原型对象后的`construtor` 属性, 通过替换原型对象一层层的找.
  >
  > 对象没有`constructor` 属性, 通过原型对象层层的找



#### 1 、替换原型对象后, 我们要修正 `constructor` 属性



```
<script>
    function Person() {

    }

    var p1 = new Person()
    //替换原型对象后, 手动修正 `constructor` 属性
    var obj =  {
    			des: 'des',
			    constructor:Person}
    Person.prototype= obj
    var p2 = new Person()

    console.log(p1.constructor);
    console.log(p2.constructor);

    console.log(p1.constructor == p2.constructor);  // true

</script>
```





### 5、 构造器属性

- 构造器属性, 指向对象的构造函数

  ```
  <script>
      function Person() {
  
      } 
      var p1 = new Person() 
      console.log(p1.constructor);  // Person
  
  </script>
  ```

  > 访问对象的构造器属性, 其实访问的是原型对象的构造器属性





###6、使用原型的注意点

