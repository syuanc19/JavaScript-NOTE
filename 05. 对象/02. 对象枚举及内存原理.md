# JavaScript 入门笔记 10.对象枚举及内存原理

# 枚举属性//

可以利用`for-in`语句，将对象中的所有属性全部获取，因为实例上 有时后这些属性、对象，是其他人，或者程序给我们写出来的，所以我们需要枚举出来

- 语句

  - ```js
    for(let 你定义的属性名 in 对象){
        语句...
    }
    ```

  - 对象中有几个属性，`for-in`语句就循环几次，每次执行时，都会将一个属性名赋值给我们所定义的变量

  - 例

  - ```js
    let obj = {
        name: '1'
        age: 2
        ktx: 3
        maa: '4'
    }
    for(custName in obj){
        console.log(custName)
    }
    ```

  - ![image-20230101144119013](https://raw.githubusercontent.com/syuanc19/picbed/main/2023/01/upgit_20230101_1672555280.png)

  - ```js
    //承上例
    for(custName in obj){
        console.log(custName, obj[custName])
    }
    ```

    ![image-20230101144645030](https://raw.githubusercontent.com/syuanc19/picbed/main/2023/01/upgit_20230101_1672555605.png)

  - 因为`for-in`的特性，此时对象里的属性已经存到了我们自定的`custName`变量里，因此我们要操控变量，我们便使用先前提到的`[]`，所以写`obj[custName]`获取变量

- 注意! 并不是所有的属性都可以被枚举，比如 使用`Symbol()`添加的属性


***

# 可变类型//

![image-20230101150035043](https://raw.githubusercontent.com/syuanc19/picbed/main/2023/01/upgit_20230101_1672556435.png)

首先，一开始说到，js里所有的==原始值都是唯一==，且不可变的，如图 当我们a跟b都是10，那定位的就是同一个内存地址，不会额外创建原始值

> 总结，原始值中，地址内的值不可变

## #1 对象的内存原理

- 基础导图

![image-20230101152018915](https://raw.githubusercontent.com/syuanc19/picbed/main/2023/01/upgit_20230101_1672557619.png)

- 我们说的`对象可变类型`，实际上指的是如图中`0x11`的那一块区域可变，例如

![image-20230101152401573](https://raw.githubusercontent.com/syuanc19/picbed/main/2023/01/upgit_20230101_1672557841.png)



- 对象属于可变类型，对象创建完成后，可以随意的添加删除修改对象
  - 如果有两个变量同时指向一个对象，通过一个变量修改对象时，也会对另一个变量造成影响

***

