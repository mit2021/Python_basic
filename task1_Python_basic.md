**1.环境搭建**

**1.1 anaconda环境配置**
1st 选框 ：将Anaconda设置添加到系统环境，如果没有勾选，需要使用Anaconda 命令行
2nd 选框 ： 将Anaconda设置为系统默认的Python 3.5 环境 
![anaconda 环境配置](https://img-blog.csdnimg.cn/20190804224244354.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)

**1.2解释器**
解释器负责执行`.py`文件。
Python解释器类型包括：
CPython（C语言开发）、
[IPython](http://ipython.org/)（功能与CPython相同，交互性增强）、
[PyPy](http://pypy.org/)（动态编译；代码执行速度提高；和CPython存在差异，两者解释执行结果可能不同）
![PyPy](https://img-blog.csdnimg.cn/20190804230836549.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)
[Jython](https://www.jython.org/index.html)（Java平台Python解释器）
![Jython](https://img-blog.csdnimg.cn/20190804230647269.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)

[IronPython](https://ironpython.net/)（微软.NET平台解释器）

![IronPython](https://img-blog.csdnimg.cn/20190804230411319.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)
2.python初体验

2.1 print and input

```
#!/usr/bin/python
# -*-  coding: latin-1 -*-
import os, sys
#print 'Hello World, Datawhale'     #SyntaxError: Missing parentheses in call to 'print'. Did you mean print('Hello World, Datawhale')?
print ('Hello World, Datawhale')
print('Good,Morning,Datawhale')    # 对比逗号是否会出现空格效果
print('Goood Morning, Datawhale')

#output:
#Hello World, Datawhale
#Good,Morning,Datawhale
#Goood Morning, Datawhale

print('100+100=',100+100)     #单引号内为字符串

#output: 100+100=200


# input 支持交互式命令行；编译器仅能通过变量赋值，达到input 的效果？
>>> name = raw_input()
Datawhale
>>> name
Datawhale


```

3.python基础讲解

3.1 python变量特性+命名规则
变量特性：存储信息并可调用，值可变化
命名规则; 变量是标识符的一种；标识符命名规则：
  a.首字符为字母或下划线
  b.其他部分：字母、数字、下划线
  c.名称区分大小写

3.2 注释方法
#

```
print('100+100=',100+100)     #单引号内为字符串
```

3.3 python中“：”作用
 3.3.1  数组中默认选择全部
 3.3.2 数组中指定范围
 3.3.3 列表中指定元素范围
 

```
list[e:]即第e+1项到最后一项
list[:e]即第一项到第e项
list[e:f]即第e+1 项到f项
```

3.4 学会使用dir( )及和help( )

    dir([object])    #返回模块的属性列表。
    help()      # 了解模块、类型、对象、方法、属性的详细信息

3.5 import使用 
python中，每个`.py`文件被称之为**模块**，每个具有`__init__.py`文件的目录被称为**包**。只要模块或者包所在的目录在`sys.path`中，就可以使用import 模块或import 包来使用。

3.6 pep8介绍
Python代码编码规范基于Python主要发行版本的**标准库**。Python的C语言实现的C代码规范请查看相应的**PEP指南**。这篇文档以及PEP 257（文档字符串的规范）改编自Guido的原始文章《Python Style Guide》，同时添加了一些来自Barry的指南。
这篇规范指南随着时间的推移而逐渐演变，随着语言本身的变化，过去的约定也被废弃。 许多项目有自己的编码规范，规范之间出现冲突时，应该以项目自身的规范为主要参考。

4.python数值基本知识

4.1 python中数值类型，int，float，bool，e记法等
整数；
浮点数；
字符串： ' 或 " 括起来，用反斜杠 \ 转义特殊字符
布尔值： True、False； and/or/not 运算
空值：None ， 不能等同于0
列表：元素类型可以不同；嵌套
元组：元素不能修改、小括号 () ，逗号隔开
集合：成员关系测试和删除重复元素
字典：无序的对象集合

4.2 运算符
4.2.1 算数运算符：
+、-、*、/、%取模、**幂、//取整

4.2.2 逻辑运算符
 and  /  or   /    not 

4.2.3 成员运算符
 in  / not in 

4.2.4 身份运算符
is / is not 
4.2.5 运算符优先级
![运算符优先级](https://img-blog.csdnimg.cn/20190805005302132.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODg3Mjc3MQ==,size_16,color_FFFFFF,t_70)

