# JavaScript 入门笔记 3.字符串及其他数据类型

## #1 字符串 string

在js中，使用单引号`''`或双引号`""`来表示字符串，而反单引号==``==也称为(模版)长字符串，可以跨行使用，并且会保存空格等等格式。

模板字符串==``==最大特点是，在引号内可以使用函数，如下例

```js
let name = "陈先生";
let str = `你好，${name}`;
console.log(str);
// 打印出 你好，陈先生
```

> 由于引号内可以放入函数的特型，我们可以透过模版字符串==``==动态的去嵌入变量

***

# 其他的数据类型

## #1 布林值 boolean

- 布林值主要用来进行逻辑判断

- 布林值只有true 和false 

```js
let num = true;
console.log(typeof num); //输出为boolean
```

## #2 空值 null

- 空值用来表示空对象
- 空值只有一个null
- 使用typeof检查一个空值(null)时，会返回一个object
- typeof无法检查空值

```js
let a = null;
console.log(typeof a); //输出为object
```

## #3 未定义 undefined

- 当声明一个变量但没有赋值时，他就是undefined
- 跟null一样，也是唯一值

```js
let a;
console.log(a); //输出为undefined
```

## #4 符号 symbol

- 用来创建唯一的标识

```js
let c = symbol() //调用symbol() 创建了一个符号，此时c变成了一个符号(symbol)
```

***

# 小结

原始值一共有七种

1. number
2. bigint
3. string
4. boolean
5. null
6. undefined
7. symbol

​	七种原始值是组成各种数据的基石，原始值在js中是不可变的类型，一经创建就不能修改。

***

