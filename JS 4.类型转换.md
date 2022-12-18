# JavaScript 入门笔记 4.类型转换

类型转换指 将一个数据类型，转换为其他数据类型

最常用的转换是，将其他类型转换为{数值(number)、字符串(string)、布林值(boolean)}



首先注意

- 调用xxx的yyy方法，在程序里写作`xxx.yyy`

​	如常用的，调用console 的log 方法写为：console.log()；

- 调用aa的函数，在程序里写作`aaa()`

***

# 转换原理图导读

1.定义完变量后，会在内存写一个空间跟位址，给变量定位

![image-20221216022313972](https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671128594.png)



2.调用a 的toString 方法，实际上是在内存新开辟一个字符串"10"

`但此时变量a还 ==未更改新定位== ，所以typeof输出仍然是number`

![image-20221216022402647](https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671128642.png)



3.给a 赋值，等于给a一个新地址，导向在a.toString()步骤就创建好的新值

![image-20221216022911395](https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671128951.png)



4.转换成功

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671127904.png">



***

# 类型转换-字符串

```js
let a = 10;
console.log(typeof a, a);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671126847.png">

此时a 的类型是数值(number)，要转换成字符串(string)有以下方法：

## 方法1.toString()

前文提到，我们实际上没有办法改变类型，因此 所谓的类型转换其实是：

`根据被转换的那个值，去创建一个同样的值的字符串`

以上述代码为续

```js
let a = 10;
a.toString();
console.log(typeof a, a);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671126847.png">

此时仍然没有发生变化，原因是，虽然程序里已经创建了一个新的字符串"10"，但是a导向的内存地址仍然是数值的10，因此，`我们需要给a赋值，让他重新导向新的字符串"10"的位址`。

```js
let a = 10;
a = a.toString(); //在这里赋值
console.log(typeof a, a);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221216_1671127904.png">

赋值完便成功了

> 注意点：undefined和 null 没有toString方法

## 方法2.调用String()

```js
let a = 10;
a = String(a); //这里的原理一样，得赋值回去给变量
```

`变量.toString();` 跟 `String(变量);` 原理一样，都需要赋值回去给变量，写作：`变量 = 变量.toString();` 跟 `变量 = String(变量);`

> String()里，undefined 跟null 可以被转换。
>
> 由于String()弹性较大，一般常用这个大过于.toString

***

# 类型转换-数值

将其他的数据类型转换为数值，使用`Number()`函数来将其转换

## 方法1.Number()

```js
let str = '619';
console.log(str);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221218_1671298329.png">

```js
let str = '619';
str = Number(str);
console.log(str);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221218_1671298393.png">

转换成功



> 所有类型的值都能转换为字符串，但不是所有类型的值都能透过`Number()`转换成数值。
>
> 如果是数字以外的值，就会转换成`NaN(not a number)`
>
> 如果是空字符串，就会转换成`0`
>
> 以下为例

```js
let str = '汉字';
str = Number(str);
console.log(str);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221218_1671298500.png">



## 方法2.parseInt()

将一个字符串转换为一个整数

```js
let a = '1字2符3儿';
a = parseInt(a);
console.log(typeof a,a );
```

为什么上述console只输出了 number 1

理由是，当parseInt在解析值时，会从左而右依序读取每一个字符串，直到读取到字符串中 所有的有效整数，但是当他读取到==字==时，后边尽管还有有效整数，也都会视为无效，因此结果只输出1。



> 假设当我们给parseInt的值本身就是数值时，parseInt会自动将该值转换为字符串 然后再去解析。



## 方法3.parseFloat()

将一个字符串转换为一个浮点数

而parseFloat原理也一样，从左至右读取到有效的浮点数(小数)值。



### Int跟Float总结

```js
let a = '3.14159265';
a = parseInt(a);
console.log(typeof a, a);
//
let b = '3.14159265';
b = parseFloat(b);
console.log(typeof b, b);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221218_1671362102.png">



如果对以下特殊值进行转换，会变成：

布林值：true转换为1、false转换为0

null：转换为0

undefined：转换为NaN

***

# 类型转换-布林

## 方法1.Boolean()

### 转换的情况：

- #### 数字:

  - `0` 和`NaN`  玩换为false		
  - 其余是true

- #### 字符串:

  - `空串` 转换为 false
  - 其余是true

- unll 和undefined 都转换为false
- 对象: 对象会转换为true

>所有表示 `空性的` `没有的` `错误的` 都会转换为false 
