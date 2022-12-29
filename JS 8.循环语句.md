# JavaScript 入门笔记 8.循环语句

# 循环简述//

循环语句可以使指定的代码反复执行n次

js中一共有三种循环语句

- `while`循环
- `do-while`循环
- `for`循环

通常编写一个循环，要有三个要件

- 初始化表达式

  - ```js
    let a = 0 //初始化表达式
    ```

- 条件表达式

  - ```js
    if (a < 5){} //条件表达式
    ```

- 更新表达式 (用来修改初始变量)

  - ```js
    ++a //更新表达式
    ```

  ```js
  let a = 0; //初始化表达式
  while(a < 5){ //条件表达式
      alert('1')
      ++a //更新表达式
  }
  //这里的循环由于有了完整的规则，便不会进入死循环
  ```

  

***

# while循环//

- 语法

  - ```js
    while(条件表达式){
    	语句...
    }
    ```

- 执行流程

  - `while`在执行时，会先对条件表达式进行判断，如果结果为`true`则执行循环，执行完毕则继续判断，如果又为`true` 则再次执行，如此反复，反复判断执行直到条件表达式结果为`false`

    > 判断->true->执行->判断->true->执行->判断...........->false->结束

> 我们可以把`while`语句当成会反复判断与执行的`if`语句

## #1 完整while范例

```js
let a = 0;
while(true){
    alert('循环开始')
    ++a
    if(a === 5){
        break
        alert('循环结束')
    }
}
```

`while`为`true`，所以会无限执行，但是我们利用了`++a`让变量自增，又设立了`if(a === 5)`时调用`break`的规则，因此 该范例语句会在自增5次 达成`if`里条件表达式的`(a === 5)`后，停止循环。

> [while循环 自我练习](https://github.com/syuanc19/js-practice-myself/blob/main/while%E7%BB%83%E4%B9%A0.md)

***

# do-while循环//

- 语法

  - ```js
    do{
        语句...
    }while(条件表达式)
    ```

- 执行流程

  - `do-while`语句在执行时，会先执行`do`后的循环体，执行完毕后，才会对`while`后的条件表达式进行判断

  

- 和`while`的区别
  - `while`是先判断，后执行
  - `do-while`是先执行，后判断
  - `do-whie`可以确保循环至少执行一次，因此 当我们希望我们的循环至少执行一次时，可以使用`do-while`

***

# for循环//

- 语法

  - ```js
    for(初始化表达式; 条件表达式; 更新表达式){
        语句...
    }
    ```

  - 可以看到，`for`循环由于表达式规则都在同个地方，因此优点是能让代码变得更加清晰，以下为例 把`while`循环用`for`循环写出

  - ```js
    //while写法
    let i = 0;
    while(i < 5){
        alert(i)
        i++
    }
    ```

  - ```js
    //for写法
    for(i=0; i<5; i++){
        alert(i)
    }
    ```

- 执行流程

  1. 先执行`初始化表达式`，初始化变量
  2. 执行`条件表达式`，判断是否执行
  3. 判断结果为`true`，则执行`语句`
  4. 执行`更新表达式`，对初始化变量进行修改
  5. 重复`2.` 直到判断为`false`为止

- 因此，初始化表达式在整个`if`循环的生命周期中，只会执行1次

- 利用`let`在`if`语句里初始化的变量，只能在该`if`循环中使用；而由于`var`是全局变量，因此不在此限

## #1 创建死循环的方式

```js
while(true){}
for(;;){}
```

***

# break//

- `break`用來终止`switch`和循环语句

  - ```js
    for (let i = 0; i < 5; i++){
        if(i === 3){
            break //这里的break不是给if用，而是给for循环使用，当i=3满足if时，for循环会被break终止
        }
    }
    ```

- `break`只会终止`离他最近`的循环

  - ```js
        for (let i = 0; i < 5; i++) {
            console.log(i)
            for (let j = 0; j < 5; j++) {
                console.log('内层循环--->', j)
            }
        }
    ```

  - <img align=left src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221229_1672274974.png">

  - `当我们在内循环添加break后`

  - ```js
        for (let i = 0; i < 5; i++) {
            console.log(i)
            for (let j = 0; j < 5; j++) {
                if (j === 1) break //添加break
                console.log('内层循环--->', j)
            }
        }
    ```

  - <img align=left src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221229_1672275045.png">

  - 由于`break`只对靠自己最近的循环作用，因此上例的break并不影响外层循环，只影响内层循环

***

# CONTINUE//

- `continue`用来跳过当次循环

  - ```js
        for (i = 0; i < 5; i++) {
            if (i === 3) {
                continue
            }
            console.log(i)
        }
    ```

  - <img align=left src="https://raw.githubusercontent.com/syuanc19/picbed/main/2022/12/upgit_20221229_1672275271.png">

  - 当i===3时触发`continue`，因此i=3时循环被跳过

- `continue`只会终止`离他最近`的循环

