1.函数关键字
关键字参数:关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。使用关键字参数允许函数调用时参数的顺序与声明时不一致，因为 Python 解释器能够用参数名匹配参数值。

2.函数的定义:
组织好的，可重复使用的，用来实现单一，或相关联功能的代码段;内建函数与用户自定义函数
2.1 自定义函数规则：
规则：
 函数代码块以` def` 关键词开头，后接函数标识符名称和圆括号 ()。 
 任何传入参数和自变量必须放在圆括号中间，圆括号之间可以用于定义参数。
  函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。函数内容以冒号起始，并且缩进。 ` return`[表达式] 结束函数，选择性地返回一个值给调用方。不带表达式的`return`相当于返回` None`。
  


3.函数参数与作用域
正式参数类型：
3.1  必需参数
以正确的顺序传入函数。调用时的数量必须和声明时的一样
3.2  关键字参数
关键字参数和函数调用关系紧密，函数调用使用关键字参数来确定传入的参数值。
 3.3 默认参数
 调用函数时，如果没有传递参数，则会使用默认参数。
 3.4 不定长参数
 能处理比当初声明时更多的参数


4.函数返回值
函数需要先定义后调用，函数体中` return` 语句的结果就是返回值。如果一个函数没有` reutrn `语句，其实它有一个隐含的 `return `语句，返回值是 `None`，类型也是` 'NoneType'`。函数体中没有` return `语句时，函数运行结束会隐含返回一个` None` 作为返回值，类型是 `NoneType`，与 `return 、return None `等效，都是返回 `None`。

5.file

打开文件方式（读写两种方式）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811200804368.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)

文件对象的操作方法
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019081120104667.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)

学习对excel及csv文件进行操作

