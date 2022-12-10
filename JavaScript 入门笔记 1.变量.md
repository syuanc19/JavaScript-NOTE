# JavaScript 入门笔记 1.变量

***

# 概述

变量可以用来保存字面量，并且可以保存任意的字面量。

一般都是通过变量来使用字面量，而不直接使用字面量，而且也可以通过变量来对字面量进行一个描述



# 1. 定义变量

```javascript
// 变量类型 变量名 = 变量值;
     var    num  = 1;
```

概述：变量 是一个装东西的盒子，能将用户的资料存放起来。

例如饭店房间，一个房间等于一个变量。

声明一个变量并赋值，称之为==初始化==

例如 var score= 10; // 将 10 赋值给 score

| js中的输入输出语句 |                            |
| ------------------ | -------------------------- |
| `alert(msg)`       | 弹窗                       |
| `console.log(msg)` | 让浏览器控制台打印输出信息 |
| `prompt(info)`     | 弹出输入框，让用户输入     |


# 2. 变量的使用

## 输入

```js
var name = "syuan.chen";
var age = 25;
console.log(name)
console.log(age)
```

<img align=left title="效果展示" style="border-radius: 10px 10px 10px 10px; box-shadow: black 3px 3px 15px; opacity: 0.7; " src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670605406.png">

## 输入+输出

```javascript
var name = prompt("输入名子");
// 定义 name = 输入的值
alert(name);
// 弹窗 name
```
<img align=left title="效果展示" style="border-radius: 10px 10px 10px 10px; box-shadow: black 3px 3px 15px; opacity: 0.7; " src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670606682.png">

<img align=left title="效果展示" style="border-radius: 10px 10px 10px 10px; box-shadow: black 3px 3px 15px; opacity: 0.7; " src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670606692.png">


***

## 变量语法扩展

### 更新变量

> 一个变量更新后，它原有的值就会被覆盖

```js
var age = 25;
age = 35;
// 最后的结果值就是35
```



### 同时声明多个变量

```js
var age = 15;
var address = "Earth";
var salary = 50000;
```

> 太繁琐，可以简写为以下

```js
var age = 15,
	address = "Earth",
	salary = 50000;
// 逗号分隔，分号结尾
```



## 声明变量的特殊情况

### 只声明不赋值

```js
var age
console.log(age)
// 输出 undefined
```

<img align=left title="效果展示" style="border-radius: 10px 10px 10px 10px; box-shadow: black 3px 3px 15px; opacity: 0.7; " src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670607714.png">



### 不声明只赋值

```js
age = 25;
console.log(age);
// 可以输出，但不提倡这么用
```

<img align=left title="效果展示" style="border-radius: 10px 10px 10px 10px; box-shadow: black 3px 3px 15px; opacity: 0.7; " src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670609707.png">



### 不声明不赋值

```js
console.log(age)
// 报错
```

<img align=left title="效果展示" style="border-radius: 10px 10px 10px 10px; box-shadow: black 3px 3px 15px; opacity: 0.7; " src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670609513.png">

***

# 3. 变量的命名规则

- 遵从(A-Z a-z) (0~9) (_) ($)
- 严格区分大小写。 var name;和 var Name; 是两个变量
- 不能以数字开头
- 不能是var for while等等关键字
- 遵守驼峰命名法，如 myFirstSalary

***

# 4. 两变量交换

![变量交换](https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221210_1670683023.png)

```js
var temp; // 定义一个temp
var var1="var1"; // 定义变量1
var var2="var2"; // 定义变量2
temp = var1; // 把 变量1 赋值给 temp
var1 = var2; // 把 变量2 赋值给 变量1
var2 = temp; //把 temp 赋值给 变量2
// 借助了创建临时变量达成两变量交换，逻辑跟顺序很重要！
```
