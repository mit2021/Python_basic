1.列表
1.1 标志
由系列按照特定顺序排列的元素组成。元素之间可以没有任何关系。方括号（[]）来表示列表，元素以逗号（，）分割。基本操作(创建，append( )，pop( ) ,del( ), 拷贝）。元组标志、基本操作（创建及不可变性）

```
#output the table and the element
bicycles = ['trek','cannondale','redline','specialized']  
#打印出列表
print(bicycles)
#索引由0开始，访问列表元素
print(bicycles[0])
print(bicycles[1])
#访问列表元素，并添加格式
#元素字母均大写
print(bicycles[1].upper())
#元素字母均小写
print(bicycles[1].lower())
#元素首字母大写
print(bicycles[1].title())
 
#output the second/third/last/penultimate
print(bicycles[1].title(),bicycles[2].title(),bicycles[-1].title(),bicycles[-2].title())   
 
#element
message = "my first bicycle was a "+ bicycles[0].title() +"."		
print(message)


#!/usr/bin/python
#-*- coding:latin-1 -*-
#import os, sys
 
 
#修改列表元素
#定义列表
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)
#索引为0元素替换
motorcycles[0] = 'ducati'
print(motorcycles)
 
Output:
['honda', 'yamaha', 'suzuki']
['ducati', 'yamaha', 'suzuki']
 
 
#列表添加元素
#列表末尾添加
motorcycles = ['honda','yamaha','suzuki']
motorcycles.append('ducai')
print(motorcycles)
#空列表逐一添加元素
new_motorcycles = []
new_motorcycles.append('honda')
new_motorcycles.append('yamaha')
new_motorcycles.append('suzuki')
new_motorcycles.append('ducai')
new_motorcycles.append('dayang')
print(new_motorcycles)
#列表中插入元素
motorcycles = ['honda','yamaha','suzuki']
motorcycles.insert(0,'ducati')
motorcycles.insert(3,'Forth Band ')
print(motorcycles)
 
Output:
['honda', 'yamaha', 'suzuki', 'ducai']
['honda', 'yamaha', 'suzuki', 'ducai', 'dayang']
['ducati', 'honda', 'yamaha', 'Forth Band ', 'suzuki']
 
 
#列表删除元素
#del索引为0元素
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)
del motorcycles[0]
print(motorcycles)
#del索引为1元素
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)
del motorcycles[1]
print(motorcycles)
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)
del motorcycles[-1]
print(motorcycles)
del motorcycles[-2]
print(motorcycles)
#IndexError: list assignment index out of range
#del motorcycles[-2]
#print (motorcycles)
 
Output:
['honda', 'yamaha', 'suzuki']
['yamaha', 'suzuki']
['honda', 'yamaha', 'suzuki']
['honda', 'suzuki']
['honda', 'yamaha', 'suzuki']
['honda', 'yamaha']
['yamaha']
 
 
#方法pop（）可删除列表末尾的元素，并可继续使用它。术语
#pop源自类比：列表就像一个栈，而删除列表末尾的元素相当于弹出栈顶元素
#从motorcycles中弹出一款摩托车
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)
popped_motorcycles = motorcycles.pop()
print(motorcycles)
print(popped_motorcycles)
#假设列表中摩托车是按照购买时间存储，则可得到最后购买的是哪款摩托车
motorcycles = ['honda','yamaha','suzuki']
Last_purchased = motorcycles.pop()
message = "The last motorcycles I owned was a " 
print(message+Last_purchased.title()+".")
#弹出列表中任何位置处的元素
motorcycles = ['honda','yamaha','suzuki']
print(motorcycles)
first_owned = motorcycles.pop(0)
print(motorcycles)
print(first_owned)
print("The first motorcycle I owned was a "+first_owned.title()+".")
#根据值删除元素
motorcycles = ['honda','yamaha','suzuki','ducati']
print(motorcycles)
removed_motorcycles = motorcycles.remove('ducati')
print(removed_motorcycles)
print(motorcycles)
 
Output:
['honda', 'yamaha', 'suzuki']
['honda', 'yamaha']
suzuki
The last motorcycles I owned was a Suzuki.
['honda', 'yamaha', 'suzuki']
['yamaha', 'suzuki']
honda
The first motorcycle I owned was a Honda.
['honda', 'yamaha', 'suzuki', 'ducati']
None
['honda', 'yamaha', 'suzuki']
 
 
 
#方法remove()只删除第一个指定值，如果指定值在列表中可能出现多次，就需要使用循环来判断
motorcycles = ['honda','yamaha','suzuki','ducati']
print(motorcycles)
too_expensive = 'ducati'
motorcycles.remove(too_expensive)
print(motorcycles)
print("A "+too_expensive.title()+" is too expensive for me.")
 
Output:
['honda', 'yamaha', 'suzuki', 'ducati']
['honda', 'yamaha', 'suzuki']
A Ducati is too expensive for me.




Python - 4 - 操作列表


4.1 遍历整个列表
使用 for 循环

#!/usr/bin/python
# -*-  coding: latin-1 -*-
import os, sys

#4.1 遍历整个列表,使用for循环
magicians = ['alice','david','carolina']
for magician in magicians:
	print(magician)

output:
alice
david
carolina


#4.1.1  对列表中的每个元素，都将执行循环指定的步骤
#4.1.2  在for循环中执行更多操作
#对每位魔术师输出表演很精彩
magicians = ['alice','david','carolina']
for magician in magicians:
	print(magician.title()+" , that was a great trick!")
	print("I can't wait to see your next trick, "+magician.title()+".\n")

output:	
Alice , that was a great trick!
I can't wait to see your next trick, Alice.

David , that was a great trick!
I can't wait to see your next trick, David.

Carolina , that was a great trick!
I can't wait to see your next trick, Carolina.


#4.1.3  在 for 循环结束后执行一些操作
magicians = ['alice','david','carolina']
for magician in magicians:
	print(magician.title()+" , that was a great trick!")
	print("I can't wait to see your next trick, "+magician.title()+".\n")

print("Thank you, eceryone, That was a great magic shou!")

output:
Alice , that was a great trick!
I can't wait to see your next trick, Alice.

David , that was a great trick!
I can't wait to see your next trick, David.

Carolina , that was a great trick!
I can't wait to see your next trick, Carolina.

Thank you, eceryone, That was a great magic shou!



#4.1	避免缩进错误
#4.2.1	忘记缩进   IdentationError: expected an indented block
#4.2.2	忘记缩进额外的代码行
magicians = ['alice','david','carolina']
for magician in magicians:
	print(magician.title()+" , that was a great trick!")
print("I can't wait to see your next trick, "+magician.title()+".\n")

print("Thank you, eceryone, That was a great magic shou!")

output:
Alice , that was a great trick!
David , that was a great trick!
Carolina , that was a great trick!
I can't wait to see your next trick, Carolina.

Thank you, eceryone, That was a great magic shou!



#4.2.3	不必要的缩进  IndentationError: unexpected indent
#message = "Hello Python world!"
#	print(message)


#4.2.4	循环后不必要的缩进,逻辑错误，语法可能无误
magicians = ['alice','david','carolina']
for magician in magicians:
	print(magician.title()+" , that was a great trick!")
	print("I can't wait to see your next trick, "+magician.title()+".\n")

	print("Thank you, eceryone, That was a great magic shou!")

output:
Alice , that was a great trick!
I can't wait to see your next trick, Alice.

Thank you, eceryone, That was a great magic shou!
David , that was a great trick!
I can't wait to see your next trick, David.

Thank you, eceryone, That was a great magic shou!
Carolina , that was a great trick!
I can't wait to see your next trick, Carolina.

Thank you, eceryone, That was a great magic shou!



#4.2.5	遗漏了冒号 SyntaxError: invalid syntax
#magicians = ['alice','david','carolina']
#for magician in magicians
#	print(magician)





#4-2	动物
#4-2.1
animals = ['cat','dog','rabbit']
for animal in animals:
	print(animal)

output:
cat
dog
rabbit

#4-2.2
animals = ['cat','dog','rabbit']
for animal in animals:
	print(animal)
	print("A "+animal+" would make a great pet.")

output:
cat
A cat would make a great pet.
dog
A dog would make a great pet.
rabbit
A rabbit would make a great pet.

#4-2.3
animals = ['cat','dog','rabbit']
for animal in animals:
	print(animal)
	print("A "+animal+" would make a great pet.")
print("Any of these animals would make a good pet!")

output:
cat
A cat would make a great pet.
dog
A dog would make a great pet.
rabbit
A rabbit would make a great pet.
Any of these animals would make a good pet!

#	创建数值列表
#4.3.1	使用函数range(),"差一行"，从指定的第一个值开始，到达指定的第二个值后停止。
#要打印数字1~5，需要使用range(1,6),使用range时若输出不符合预期尝试将指定值加或减1
for value in range(1,5):
	print(value)

##output:
#1
#2
#3
#4


for value in range(1,6):
	print(value)

##output:
#1
#2
#3
#4
#5


#	使用range()创建数字列表
#	函数list()将range()的结果直接转换为列表
numbers = list(range(1,6))
print(numbers)

##output
#[1, 2, 3, 4, 5]


#	输出1~10内的偶数
even_numbers = list(range(2,11,2))
print(even_numbers)

##output
#[2, 4, 6, 8, 10]


#	输出1~10内的奇数
odd_numbers = list(range(1,10,2))
print(odd_numbers)

##outpt
#[1, 3, 5, 7, 9]


#	创建1~10平方的列表
squares = []
for value in range(1,11):
	square = value**2
	squares.append(square)
	#squares.append(value**2)
print(squares)

##output
#[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]



#4.3.3	对数字列表执行简单的统计计算
digits = [1,2,3,4,5,6,7]
print(min(digits))
print(max(digits))
print(sum(digits))

##output
#1
#7
#28



#4.3.4	列表解析：将for循环和创建新元素的代码合并成一行，并自动附加新元素
#要使用这种语法，首先指定一个描述性的列表名，如squares；然后，指定一个左方括号，
#并定义一个表达式，用于生成你要存储到列表中的值，在该实例中，表达式为value**2，
#它计算平方值。编写for循环，用于给表达式提供值，再加上右方括号。
squares = [value**2 for value in range(1,11)]
print(squares)

##output
#[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]




	
#	创建空列表cubes，cube元素append添加，for loop print cube
cubes = []
for number in range(1,11):
	cube = number**3
	cubes.append(cube)
print(cubes)
for cube in cubes:
	print(cube)

##output:
##[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
#1
#8
#27
#64
#125
#216
#343
#512
#729
#1000


#	列表解析  SyntaxError: keyword can't be an expression 
#print(cube in cubes = [number**3 for number in range(1,11)])

#4-9	列表解析	
cubes = [number**3 for number in range(1,11)]
print(cubes)
for cube in cubes:
	print(cube)

##output:
##[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
#1
#8
#27
#64
#125
#216
#343
#512
#729
#1000


#4.4	使用列表的一部分
#4.4.1	切片：处理列表中的部分元素，要创建切片，可指定要使用的第一个元素和最后一个元素
#的索引。在到达指定的第二个索引前面的元素后停止。若未指定第一个索引，python将自动从列表
#开头开始；若未指定终止索引，则至列表末尾。负数索引返回离列表末尾相应距离的元素
players = ['charles','martina','michael','florence','eli']
#输出前三位 TypeError: list indices must be integers or slices, not tuple
#print(players[0,3])
print(players[0:3])

##output：
##['charles', 'martina', 'michael']

#输出第二至第四位
print(players[1:4])

##output
##['martina', 'michael', 'florence']

#无起始索引
print(players[:4])

##output:
##['charles', 'martina', 'michael', 'florence']

#无终止索引
print(players[2:])

##output
##['michael', 'florence', 'eli']

#负数索引，返回离列表末尾相应距离的元素
print(players[-3:])

##output
##['michael', 'florence', 'eli']



#4.4.2 遍历切片，在for循环中使用切片
players = ['charles','martina','michael','florence','eli']
for player in players[0:3]:
	print(player)
	
##output:
#charles
#martina
#michael


#4.4.3 复制列表
#创建包含整个列表的切片
my_foods = ['pizza','falafel','carrot cake']
friend_foods = my_foods[:]
#friend_foods = my_foods
print("my favorite foods are ")
print(my_foods) 
print("my friend's favorite foods are ")
print(friend_foods)

##output:
#my favorite foods are
#['pizza', 'falafel', 'carrot cake']
#my friend's favorite foods are
#['pizza', 'falafel', 'carrot cake']

#每个列表添加一种食品
my_foods.append('cannoli')
friend_foods.append('ice cream')
print("my favorite foods are ")
print(my_foods) 
print("my friend's favorite foods are ")
print(friend_foods)

##output
#my favorite foods are
#['pizza', 'falafel', 'carrot cake', 'cannoli']
#my friend's favorite foods are
#['pizza', 'falafel', 'carrot cake', 'ice cream']

#简单地将my_foods 赋值给 friend_foods,让Python将新变量friend_foods关联到包含
#在my_foods中的列表，因此这两个变量都指向同一个列表
my_foods = ['pizza','falafel','carrot cake']
#friend_foods = my_foods[:]
friend_foods = my_foods
print("my favorite foods are ")
print(my_foods) 
print("my friend's favorite foods are ")
print(friend_foods)
my_foods.append('cannoli')
friend_foods.append('ice cream')
print("my favorite foods are ")
print(my_foods) 
print("my friend's favorite foods are ")
print(friend_foods)

##output:
#my favorite foods are
#['pizza', 'falafel', 'carrot cake']
#my friend's favorite foods are
#['pizza', 'falafel', 'carrot cake']
#my favorite foods are
#['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']
#my friend's favorite foods are
#['pizza', 'falafel', 'carrot cake', 'cannoli', 'ice cream']






#4.5	元组：不能修改的值称为不可变的，而不可变的列表被称为元组
#4.5.1 定义元组：（）而非[]   可使用索引来访问其元素
dimensions = (200, 50)
print(dimensions[0])
print(dimensions[1])

##output
#200
#50

#修改元组元素值 TypeError: 'tuple' object does not support item assignment
#dimensions[0] = "77"

#4.5.2 遍历元组中的所有值
dimensions = (200,50)
for dimension in dimensions:
	print(dimension)

##output:
#200
#50

#4.5.3 修改元组变量
#虽元组元素不可修改，但可对存储元组的变量赋值
dimensions = (200,50)
print("Original dimensions: ")
for dimension in dimensions:
	print(dimension)
dimensions = (400,100)
print("\nModified dimensions: ")
for dimension in dimensions:
	print(dimension)

##output
#Original dimensions:
#200
#50

#Modified dimensions:
#400
#100










```



3.string字符串
3.1 定义及基本操作（+，*，读取方式）
最新的Python 3版本中，字符串是以Unicode编码的，也就是说，Python的字符串支持多语言，对于单个字符的编码，Python提供了`ord()`函数获取字符的整数表示，`chr()`函数把编码转换为对应的字符
3.2 字符串相关方法
以Unicode表示的`str`通过`encode()`方法可以编码为指定的bytes
`ord()`函数获取字符的整数表示，`chr()`函数把编码转换为对应的字符
纯英文的`str`可以用ASCII编码为`bytes`，内容是一样的，含有中文的`str`可以用UTF-8编码为bytes。
4.字符串格式化问题
Python中，采用的格式化方式和C语言是一致的，用`%`实现
在字符串内部，`%s`表示用字符串替换，`%d`表示用整数替换，有几个`%?`占位符，后面就跟几个变量或者值，顺序要对应好.常见的占位符有：
%d 整数;   %f 浮点数;   %s  字符串; %x  十六进制整数;

