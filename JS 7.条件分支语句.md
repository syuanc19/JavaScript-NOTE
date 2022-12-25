# JavaScript 入门笔记 7.条件分支语句

代码块，用`{}`表示，不管该行代码组是一行或是多行，也推荐写上`{}`，让我们的结构更清晰明朗

# let 和 var//

- `let`具有块作用域，`let`在代码块里声明的变量 无法在外部访问

  - ```js
    {
        let a = 10;
    }
    console.log(a);
    //报错 a is not definded
    //因为let快作用域的影响，使他在代码块内无法被提出
    ```

- 而`var`则无块作用域的特性

  - ```js
    {
        var a = 10;
    }
    console.log(a);
    //不报错 显示10
    ////因为var无快作用域的影响，使他在代码块内可以被提出
    ```

***

# 条件运算符 三元表达式//

执行顺序：

- 条件运算符在执行时，会先对条件表达式进行求值判断

```js
//格式
条件表达式? 表达式1 : 表达式2
```

- 如果结果为`true` 则执行表达式1
- 如果结果为`false` 则执行表达式2

例:

```js
let a = 10;
let b = 20;
a > b ? alert('a大') : alert('b大');
```

***

# 流程控制语句//

流程控制语句可以用来改变程序执行的顺序

- 条件判断语句
- 条件分支语句
- 循环语句

***

# if语句//

## #1 if语句

- 语法

   - ```js
     if(条件表达式)
     ```

     

- 执行流程

  - `if`语句在执行时 会先对`if`后的条件表达式进行求值判断，结果为`true`则执行`if`后的语句，如果为`false`则不执行

  - ```js
    let a = 100;
    let b = 50;
    if (a > b) alert('a win');//if里的结果是true，因此alert会响应 a win
    
    let a = 5;
    let b = 50;
    if (a > b) alert('a win'); //if里的结果是false，因此alert不响应
    ```

- `if`语句只会控制紧随其后的那一行代码

  - ```js
    let a = 0;
    if (a > 10)
    alert('a大于10') //a没有比10大，因此此行alert不响应
    alert('12345') //a虽然小于10，但是if语句只控制它后边的那一串，因此实际上这行是独立的语句，所以alert会正常响应
    ```

  - 但如果在同一分组内，那就可以让`if`控制整个分组，我们可以使用代码块`{}`，例如:

  - ```js
    if (a > 10){
        alert('123')
        alert('456')
    }    
    ```

- 如果`if`后的添加表达式不是`布尔值`，那么会先转换成`布尔值`然后再进行判断

  - ```js
    let a = 10;
    if (a == '10')
        alert('成功') //alert响应成功
    ```



## #2 if-else语句

- 语法

  ```js
  if(条件表达式){语句1...}else{语句2...}
  ```

- 执行流程

  - `if-else`语句在执行时 会先对条件表达式进行求值判断，结果为`true`则执行`if`后的语句，如果为`false`则执行`else`后的，例：

    ```js
    let age = 49;
    if (age > 60) {alert('大于60')} else {alert('小于60')};
    //alert输出为小于60
    ```

    

## #3 if-else if-else语句

- 语法

  - ```js
    if(条件表达式){语句1...}
    else if(条件表达式){语句2...}
    else if(条件表达式){语句3...}
    else{语句...}
    ```

- 执行流程

  - `if-else if-else`语句，会自动`由上至下依次`对if后的条件表达是进行求值判断，如果表达式的结果为`true`，则执行当前if后的语句，然后`短路`(跟`&&` `||`逻辑一样，找到`t/f`则结束运算)直接结束语句。 当所有条件表达式的结果匹配都是`false`时，才会执行`else`语句

***

# switch语句//

- 语法

  - ```js
     switch(表达式) {
        case 表达式:
      		代码...
        case 表达式:
      		代码...
        case 表达式:
      		代码...
        case 表达式:
      		代码...
    }
    ```

- 执行流程

  - `switch`语句在执行时，会依次将`switch`后的表达式和`case`后的表达式进行`全等(===)比较`，如果比较结果为`true`，则自当前`case`处开始执行代码；如果比较结果为`false`，则继续往下比较其他`case`后的表达式，直至找到`true`。

  - 我们先用`if-else if-else`语句写一段代码，之后用`switch`语句改写

  - ```js
    let num = 1;
    if (num === 1){alert('一')}
    	else if(num ===2){alert('二')}
    	else if(num ===3){alert('三')}
    ```

  - `switch`写法

  - ```js
    let num = 1;
    switch(num) {  //这里Number的意思是，往下所有的值都与num去相比
        case 1:
            alert('一')
            break
        case 2:
            alert('二')
            break
        case 3:
            alert('三')
            break
    }
    ```

  - 注意，刚刚有提到 `如果比较结果为true，则自当前case处开始执行代码`，也就是说  无论在第几行找到`true`，那么`switch`都会往下继续执行所有的`case`语句(无论匹不匹配)，所以上述语法中 使用了`break`，`break`可以在该段落用来强制结束`switch`语句。

## #1 default:

- 语法

  - ```js
    switch (表达式){
        case 表达式:
            代码...
        case 表达式:
    		代码...
        default:
        	代码...
    }
    ```

- 执行流程

  - 当所有比较结果为`false`时，则执行`default`

***

# 总结//

`switch`语句和`if`语句的功能是重复，`if`能做的事 在`switch`也能做，反之亦然

最大的不同是，`switch`预设就是全等判断，结构也比较清晰
