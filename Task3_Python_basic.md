```
# -*-  coding: latin-1 -*-
import os, sys


#能够将相关信息关联起来；能够高效模拟现实世界中的精彩
#6.1一个简单的字典
alien_0 = {'color':'green','points':5}
print(alien_0['color']) 
print(alien_0['points'])


#output:
#green
#5

#6.2字典是一系列键-值对。每个键都与一个值相关联，值可以是数字、字符串、列表乃至字典。事实上
#可将任何Python对象用作字典中的值；字典中键-值对数量不受限制；


#6.2.1访问字典中的值
new_points = alien_0['points']
#当str(mew_points)时编译通过，命令行执行结果报错
print("You just earned" + str(new_points) + "points")

#output : You just earned5points

#6.2.2添加键值对
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)

#output:
{'color': 'green', 'points': 5, 'x_position': 0, 'y_position': 25}

```
6.2.3 创建空字典
可使用一对花括号定义一个字典，再分别添加各个键值对
6.2.4 修改字典中的值
指定字典名、用方括号扩起的键以及该键相关联的新值
6.2.5 删除键值对
`del` 指定字典名和要删除的键


7. 集合（set）是一个无序的不重复元素序列。

可以使用大括号 { } 或者 set() 函数创建集合，注意：创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。 
 格式：

    parame = {value01,value02,...}
    or
    set(value)
7.1 添加元素
7.2、移除元素
7.3、计算集合元素个数
7.4、清空集合
7.5、判断元素是否在集合中存在


8.判断语句
Python条件语句是通过一条或多条语句的执行结果（True或者False）来决定执行的代码块。Python程序语言指定任何非0和非空（null）值为true，0 或者 null为false。其中"判断条件"成立时（非零），则执行后面的语句，而执行内容可以多行，以缩进来区分表示同一范围。else 为可选语句，当需要在条件不成立时执行内容则可以执行相关语句。if 语句的判断条件可以用>（大于）、<(小于)、==（等于）、>=（大于等于）、<=（小于等于）来表示其关系。由于 python 并不支持 switch 语句，所以多个条件判断，只能用 elif 来实现，如果判断需要多个条件需同时判断时，可以使用 or （或），表示两个条件有一个成立时判断条件成功；使用 and （与）时，表示只有两个条件同时成立的情况下，判断条件才成功。


9. Python三目运算符
条件为真时的结果 if 判段的条件 else 条件为假时的结果 。Python 中的三目运算符目的是得到一个结果，未必就是将该结果return，或者进行简单的变量赋值 。
Python 可通过 if 语句来实现三目运算符的功能，因此可以近似地把这种 if 语句当成三目运算符。作为三目运算符的 if 语句的语法格式如下：

 

       True_statements if expression else False_statements


10.循环语句：
Python for循环可以遍历任何序列的项目，如一个列表或者一个字符串。语法：for循环的语法格式如下：

    for iterating_var in sequence:
       statements(s)
在 python 中，for … else 表示这样的意思，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。
