# JavaScript 入门笔记 2.数据类型

## 数据类型

1. 数值 (Number)
2. 大整数 (BigInt)
3. 字符串 (String)
4. 布尔值 (Boolean)
5. 空值 (Null)
6. 未定义 (Undefined)
7. 符号 (Symbol)

## 数值 (Number)

在js中，所有整数跟浮点数(小数)，都是Number类型

```js
let a = 100;
console.log(a);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221215_1671037723.png">

Number类型在console里会是蓝色的

在js中，数值并不是无限大的，数值超过一定范围会显示近似值(小数同理)，另如infinity是一个表示无穷的特殊数字，打印 9999**9999时 ，就会显示infinity



由于电脑底层使用的是二进制，因此如果以下为例

```js
let a = 0.1+0.2;
console.log(a);
```

<img src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221215_1671038137.png">

会打印出如图的结果，道理就跟十进制的日常算法 去算10/3一样，会得到0.3333333的无穷数。

## 大整数 (BigInt)

只能表示整数

如果要创建一个大整数，必须在数字后面加 n，以下为例

```js
a = 999999999999999999999999999999999; //未+n
console.log(a);
//console输出 1e+33
```

```js
a = 999999999999999999999999999999999n; //已+n
console.log(a);
//console输出 999999999999999999999999999999999n
```

> 大整数的上限，是依据`内存`而定，内存能装多少 大整数就能显示多少

## 进制数字表示法

二进制 0b

八进制 0o

十六进制 0x `(一般内存地址都用十六进制表示)`

即使表示方式是十进制以外的进制，输出的打印结果仍然是采用十进制表示

## 类型检查

使用`typeof`，typeof用来检查不同值的类型，会根据不同的值传回不同的结果

```js
let a = 10;
let b = 5n;
let ccc = false;
console(typeof a); //输出 Number
console(typeof b); //输出 BigInt
console(typeof ccc); //输出 Boolean
```

> js里，变量是没有类型的 如上例的a b ccc，typeof检查的是`变量里的值`的类型。
