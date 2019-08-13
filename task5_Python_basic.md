1.类和对象
关于python中类与方法的创建在格式上是和java类似的我们可以对应着那个来学这个。
构造函数和析构函数：

    class Car:
        def __init__(self, number):
            print("My number is {}".format(number))
        def __del__(self):
            print("I am destroyed!")
     
    Car("23333")


解释：和java中一样，在自定义一个类之前都是用class关键字来声明一个类，在Python中初始化和析构函数有固定的函数名："_init_" 和 "_del_ ", 而且二者的第一个参数都应该是一个指向实例本身的self参数，后边可以加我们需要的参数，在这里self参数是不需要人为传入的，Python会在调用实例方法的时候自动传入self参数。self是用来干嘛的？self参数是调用这个实例方法的实例本身的引用，即哪个对象调用了带有self参数的方法，self就会指代谁。
类的属性：

    class Car:
        count = 0
        def __init__(self, number):
            Car.count += 1
            self.number = number
            print("My number is {}".format(number))
     
        def __del__(self):
            self.__class__.count -= 1
            print("I am destroyed! My number is {}".format(self.number))
     
    print(Car.count)
    a1 = Car("1122")
    print(Car.count)
    a2 = Car("2233")
    print(Car.count)



 

 解释：在Python中属性分为两种：类属性和实例属性；区别：“类属性”在该类及其所有的实例中是共享的；而“实例属性”在实例之间不共享，每个实例都拥有一个属于实例本身的“实例属性”，在上边的这段程序中count就相当于类属性，number相当于实例属性，其中无论实在类外还是类内，通过“类名.类属性名”即可使用这个类的类属性，但是唯独在析构函数中不可以这么用，在析构函数中我们需要通过“self._class_.类属性名”的方式来访问类属性。

“self.number=number” ：使用初始化函数的参数number的值为实例属性number初始化，这样我们就可在析构的时候再次输出它了。
类的方法（方法”就是指在类中定义的函数）：

Python中类分为三种：“实例方法”，“静态方法”，“类方法”
实例方法：

“实例方法”是类的实例所特有的方法，实例方法只能通过实例的引用进行调用，并且在实例方法中可以通过self参数直接访问调用该方法的实例本身，上边有用到。
静态方法:

“静态方法”既可以通过各类名进行调用，也可以通过实例的引用进行调用。在Python中，静态方法在声明时需要使用修饰器“@staticmethod”修饰，就是在函数声明的上一行中添加修饰器；同时，“静态方法”中不需要传入self参数，因此我们无法直接获取调用静态方法的对象的引用。

    class cal:
        @staticmethod
        def add(x, y):
            return x+y
    print(cal.add(1,2))


 
类方法：

“类方法”也是既可以通过类名进行调用，也可以通过实例的引用进行调用。并且类方法需要传入一个参数（常命名为“cls”）作为调用该方法的类的引用，类似于类方法中的self，所以在这点上来看，类方法更像是实例方法，只不过它关注的不是调用该方法的对象而是类。Python中类方法需要使用修饰器“@classmethod”进行修饰。

    class C:
        name = "Say"
        @classmethod
        def foo(cls, content):
            print("{} {}".format(cls.name, content))
    C.foo("Hi!")
    c = C()
    c.foo("Bye!")




2.正则表达式

  1. 创建正则表达式对象和匹配Regex对象
        2. 正则表达式匹配更多模式
            2.1 利用括号分组
            2.2 在文本中匹配括号
        3. 用管道匹配多个分组
            3.1 匹配多个模式中的一个
        4. 用问号实现可选匹配：
            4.1.1 让正则表达式寻找包含区号或不包含区号的电话号码
        5. 用星号匹配零次或多次
        6. 用加号匹配一次或多次
        7. 用加号匹配一次或多次
        8. 贪心和非贪心匹配
        9. findall()方法
            9.1 search() 和 findall() 返回值的对比
            9.2 findall()分组情况，返回列表
        10. 字符分类总结
        11. 建立自己的字符分类
            11.1 非 ^ 的情况
            11.2 有 ^ 的情况
        12. 插入字符和美元字符
            12.1 使用^ 的情况
            12.2 使用$ 的情况
            12.3 使用 “+$ ”的情况
        13. 通配字符
            13.1 用点-星匹配所有字符
            13.2 用句点字符匹配换行
        14. 正则表达式符号复习
        15. 不区分大小写
        16. 用sub方法替换字符串
        17. 管理复杂的正则表达式
        18. 组合使用 re.IGNOREC ASE、re.DOTALL 和 re.VERBOSE
      


1. 创建正则表达式对象和匹配Regex对象

向 re.compile() 传入一个字符串值，表示正则表达式，它将返回一个 Regex 模式 对象(或者就简称为 Regex 对象)。Regex 对象的 search() 方法查找传入的字符串，寻找该正则表达式的所有匹配。如果字符串中没有找到该正则表达式模式，search() 方法将返回 None。如果找到了该模式， search() 方法将返回一个 Match 对象。Match 对象有一个 group() 方法，它返回被查找字符串中实际匹配的文本。

import re
# 因为正则表达式常常使用倒斜杠，向 re.compile()函数传入原始字符串就很方便
# r: 忽略所有的转义字符，打印出字符串中所有的倒斜杠
phoneNumber = re.compile(r'\d{3}-\d{3}-\d{3}') # Regex 对象
mo = phoneNumber.search('Mu Number is 400-000-999') # 返回一个 Match 对象
mo.group()
>> '400-000-999'

 

2. 正则表达式匹配更多模式
2.1 利用括号分组

添加括号将在正则表达式中创建“分组”: (\d\d\d)-(\d\d\d-\d\d\d\d)。然后可以使用 group()匹配对象方法，从一个分组中获取匹配的文本。

phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d-\d\d\d\d)')
mo = phoneNumRegex.search('My number is 415-555-4242.')
print(mo.group(1))
print(mo.group(2))
#一次就获取所有的分组 
print(mo.groups())

>> 415-555-4242
>> 555-4242
>> ('415', '555-4242')

  

2.2 在文本中匹配括号

括号在正则表达式中有特殊的含义，但是如果你需要在文本中匹配括号，怎么办?例如，你要匹配的电话号码，可能将区号放在一对括号中。传递给 re.compile()的原始字符串中，(和)转义字符将匹配实际的括号字符。

 #phoneNumRegex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
phoneNumRegex = re.compile(r'(\(\d{3}\)) (\d{3}-\d{4})')
mo = phoneNumRegex.search('My phone number is (415) 555-4242.')
print(mo.group(1))
>> (415)

 

3. 用管道匹配多个分组

字符 | 称为 管道。希望匹配许多表达式中的一个时，就可以使用它。例如， 正则表达式 r**Batman | Tina Fey **将匹配 Batman或 Tina Fey。 如果 Batman 和 Tina Fey 都出现在被查找的字符串中，第一次出现的匹配文本， 将作为 **Match **对象返回。

heroRegex = re.compile(r'Brain|head') # 中间不要有空格，不然第二个打印报错
mo1 = heroRegex.search('Brain and head')
print(mo1.group())
mo2 = heroRegex.search('head and Brain')
mo2.group()
print(mo2.group())

>> Brain
>> head

 


3.1 匹配多个模式中的一个

batRegex = re.compile(r'Bat(man|mobile|copter|bat)')
mo = batRegex.search('Batmobile lost a wheel')
print(mo.group())
print(mo.group(1)) # 只是返 回第一个括号分组内匹配的文本'mobile'
print(mo.groups())

>> Batmobile
>> mobile
>> ('mobile',)

 

4. 用问号实现可选匹配：

匹配的模式是可选的。就是说，不论这段文本在不在，正则表达式 都会认为匹配。字符 ? 表明它前面的分组在这个模式中是可选的，如果需要匹配真正的问号字符，就使用转义字符 \?

batRegex = re.compile(r'Bat(wo)?man')
mo1 = batRegex.search('The Adventures of Batman')
print(mo1.group())
mo2 = batRegex.search('The Adventures of Batwoman')
print(mo2.group())
print(mo2.group(1)) # 这个才有分组，因为匹配的对象有：“wo”；  (wo)?部分表明，模式 wo 是可选的分组

>> Batman
>> Batwoman
>> wo

 

4.1.1 让正则表达式寻找包含区号或不包含区号的电话号码

phoneRegex = re.compile(r'(\d{3}-)?\d{3}-\d{4}')
mo1 = phoneRegex.search('My Number is 411-234-4566')
# 建议都打出来看看
print(mo1.group())
print(mo1.group(1))
print(mo1.groups())

mo2 = phoneRegex.search('My Number is 222-3445')
print(mo2.group())
print(mo2.group(1)) # 没有可选的组,为None
print(mo2.groups()) # 同上

>> 411-234-4566
>> 411-
>> ('411-',)
>> 222-3445
>> None
>> (None,)

  


5. 用星号匹配零次或多次

* (称为星号)意味着 匹配零次或多次，即星号之前的分组，可以在文本中出现任意次。它可以完全不存在，或一次又一次地重复。

// An highlighted block
batRegex = re.compile(r'Bat(wo)*man')
mo1 = batRegex.search('The Adventures of Batman')
print(mo1.group())

# 下面就有group(1)了
mo2 = batRegex.search('The Adventures of Batwoman')
print(mo2.group())
print(mo2.group(1))

mo3 = batRegex.search('The Adventures of Batwowowoman')
print(mo3.group())
print(mo3.group(1)) # group(1)与上面是相同，只看条件，不看量

>> Batman
>> Batwoman
>> wo
>> Batwowowoman
>> wo

  


6. 用加号匹配一次或多次

*意味着匹配零次或多次，+(加号)则意味着 匹配一次或多次。星号 不要求分组出现在匹配的字符串中，但加号不同，加号前面的分组必须 至少出现一次。这不是可选的。

batRegex = re.compile(r'Bat(wo)+man')
mo1 = batRegex.search("The Adventures of Batwoman")
print(mo1.group())

mo2 = batRegex.search("The Adventures of Batwowowoman")
print(mo2.group())

# 加号 要求 wo 至少出现一次。
# 如果需要匹配真正的加号字符，在加号前面加上倒斜杠实现转义:\+
mo3 = batRegex.search("The Adventures of Batman")
print(mo3 == None)
>> Batwoman
>> Batwowowoman
>> True

   


7. 用加号匹配一次或多次

如果想要一个分组重复特定次数，就在正则表达式中该分组的后面，跟上花括 号包围的数字。例如，正则表达式 (Ha){3} 将匹配字符串 ‘HaHaHa’，但不会匹配 ‘HaHa’， 因为后者只重复了 (Ha)分组两次。除了一个数字，还可以指定一个范围，即在花括号中写下一个最小值、一个逗号和 一个最大值。例如，正则表达式 (Ha){3,5} 将匹配’HaHaHa’、‘HaHaHaHa’和’HaHaHaHaHa’。也可以不写花括号中的第一个或第二个数字，不限定最小值或最大值。例如，(Ha){3,} 将匹配 3 次或更多次实例，(Ha){,5} 将匹配 0 到 5 次实例。花括号让正则表达式更简短；

    (Ha){3}
    (Ha)(Ha)(Ha)

    (Ha){3,5}
    ((Ha)(Ha)(Ha)) | ((Ha)(Ha)(Ha)(Ha)) | ((Ha)(Ha)(Ha)(Ha)(Ha))

    上面二者两组的正则表达式匹配同样的模式

haRegex = re.compile(r'(Ha){3}')
mo1 = haRegex.search('HaHaHa')
print(mo1.group())
mo2 = haRegex.search('HaHa')
print(mo2 == None)

>> HaHaHa
>> True

 


8. 贪心和非贪心匹配

如： (Ha){3,5} 的匹配模式，会返回： ‘HaHaHaHaHa’;
Python的正则表达式默认是 “贪心” 的，这表示在有二义的情况下，它们会尽可能匹配最长的字符串。花括号的 “非贪心” 版本匹配尽可能最短的字符串，即在结束的花括号后跟着一个问号。
注意: 问号在正则表达式中可能有两种含义: 声明非贪心匹配或表示可选的分组。这两种含义是完全无关的。

greedyHaRegex = re.compile(r'(Ha){3,5}')
mo1 = greedyHaRegex.search('HaHaHaHaHa')
print(mo1.group())
nongreedyHaRegex = re.compile(r'(Ha){3,5}?')
mo2 = nongreedyHaRegex.search('HaHaHaHaHa')
print(mo2.group())

>> HaHaHaHaHa
>> HaHaHa

  


9. findall()方法

Regex 对象有一个 findall() 方法。search() 将返回一个 Match 对象，包含被查找字符串中的 第一次 匹配的文本，而 findall() 方法将返回一组字符串，包含被查找字符串中的所有匹配；
9.1 search() 和 findall() 返回值的对比

phoneNumRegex = re.compile(r'\d{3}-\d{3}-\d{4}')
mo = phoneNumRegex.search('Wang:222-111-3333,Work:111-666-0000')
print(mo.group())

#findall()不是返回一个 Match 对象，而是返回一个字符串列表，只要在正则表达式中没有分组。
#列表中的每个字符串都是一段被查找的文本，它匹配该正则表达式
phoneList = phoneNumRegex.findall('Wang:222-111-3333,Work:111-666-0000')
print(phoneList)

>> 222-111-3333
>> ['222-111-3333', '111-666-0000']



9.2 findall()分组情况，返回列表

#如果在正则表达式中有分组，那么 findall 将返回元组的列表。
#每个元组表示一个找到的匹配，其中的项就是正则表达式中每个分组的匹配字符串
phoneNumRegex = re.compile(r'(\d{3})-(\d{3})-(\d{4})')
tuples = phoneNumRegex.findall('Wang:222-111-3333,Work:111-666-0000')
print(tuples)

>> [('222', '111', '3333'), ('111', '666', '0000')]

 

10. 字符分类总结

\d 是正则表达式 (0|1|2|3|4|5|6|7|8|9) 的缩写；

常用字符分类的缩写代码:

\d: 0 到 9 的任何数字

\D: 除 0 到 9 的数字以外的任何字符

\w: 任何字母、数字或下划线字符(可以认为是匹配“单词”字符)

\W: 除字母、数字和下划线以外的任何字符

\s: 空格、制表符或换行符(可以认为是匹配“空白”字符)

\S: 除空格、制表符和换行符以外的任何字符

如： 字符分类**[0-5]**只匹配数字 0 到 5。

xmasRegex = re.compile(r'\d+\s\w+')
xmas = xmasRegex.findall('12 drummers, 11 pipers, 10 lords, 9 ladies, 8 maids, 7 swans, 6 geese, 5 rings, 4 birds, 3 hens, 2 doves, 1 partridge')
print(xmas)
#解释： 正则表达式\d+\s\w+匹配的文本有一个或多个数字(\d+)，接下来是一个空白字 符(\s)，接下来是一个或多个字母/数字/下划线字符(\w+)

>> ['12 drummers', '11 pipers', '10 lords', '9 ladies', '8 maids', '7 swans', '6 geese', '5 rings', '4 birds', '3 hens', '2 doves', '1 partridge']

  


11. 建立自己的字符分类

想匹配一组字符，但缩写的字符分类 (\d、\w、\s 等) 太宽泛。可以用方括号定义自己的字符分类。例如，字符分类 [aeiouAEIOU] 将匹配所有元音字符，不论大小写；也可以使用短横表示字母或数字的范围。例如，字符分类 [a-zA-Z0-9] 将匹配所有小写字母、大写字母和数字。
注意： 在方括号内，普通的正则表达式符号不会被解释，意味着，不需要前面加上倒斜杠转义**. 、*、?或()字符**。例如，字符分类将匹配数字 0 到 5 和一个 句点。你不需要将它写成 [0-5.]。

通过在字符分类的左方括号后加上一个插入字符 (^)，就可以得到 非字符类 。 非字符类 将匹配不在这个字符类中的所有字符。
11.1 非 ^ 的情况

vowelRegex = re.compile(r'[aeiouAEIOU]')
vowel = vowelRegex.findall('RoboCop eats baby food. BABY FOOD.')
print(vowel)
>> ['o', 'o', 'o', 'e', 'a', 'a', 'o', 'o', 'A', 'O', 'O']

   


11.2 有 ^ 的情况

# 通过在字符分类的左方括号后加上一个插入字符 **(^)**，就可以得到“非字符类”。 非字符类将匹配不在这个字符类中的所有字符

consonanRegex = re.compile(r'[^aeiouAEIOU]')
consonan = consonanRegex.findall('RoboCop eats baby food. BABY FOOD.')
print(consonan)
>> ['R', 'b', 'C', 'p', ' ', 't', 's', ' ', 'b', 'b', 'y', ' ', 'f', 'd', '.', ' ', 'B', 'B', 'Y', ' ', 'F', 'D', '.']

   


12. 插入字符和美元字符

在正则表达式的开始处使用插入符号 “(^)”，表明匹配必须发生在被查找文本开始处。类似地，可以再正则表达式的末尾加上美元符号 "()&quot;∗∗，表示该字符串必须以这个正则表达式的模式结束。可以同时使用∗∗∗∗和∗∗

)"∗∗，表示该字符串必须以这个正则表达式的模式结束。可以同时使用∗∗∗∗和∗∗，表明整个字符串必须匹配该模式，也就是说，只匹配该字符串的某个子集是不够的。
12.1 使用^ 的情况

beginWithHello = re.compile(r'^Hello')
beginWith1 = beginWithHello.search('Hello world')
print(beginWith1.group())

beginWith2 = beginWithHello.search('He said hello')
print(beginWith2 == None)
>> Hello
>> True

   


12.2 使用$ 的情况

#表达式 r'\d$'匹配以数字 0 到 9 结束的字符串
endWithNumber = re.compile(r'\d$')
endWith1 = endWithNumber.search('Your number is 000')
print(endWith1.group())

endWith2 = endWithNumber.search('Your number is two')
print(endWith2 == None)

>> 0
>> True

   


12.3 使用 “+$ ”的情况

# 正则表达式 r'^\d+$'匹配从开始到结束都是数字的字符串。
wholeStringIsNum = re.compile(r'^\d+$')
whole1 = wholeStringIsNum.search('1234567890')
print(whole1.group())

whole2 = wholeStringIsNum.search('1234567ss890')
print(whole2 == None)

whole3 = wholeStringIsNum.search('123456  7ss890')
print(whole3 == None)

>> 1234567890
>> True
>> True

   


13. 通配字符

’.（句号）’ 称为通配符。 匹配除了换行之外的所有字符。

注意： 句点字符只匹配一个字符，要匹配真正的句点，就是用倒斜杠转义: \ 。

atRegex = re.compile(r'.at')
at = atRegex.findall('The cat in the hat sat on the flat mat.')
print(at)
>> ['cat', 'hat', 'sat', 'lat', 'mat']



13.1 用点-星匹配所有字符

有时候想要匹配所有字符串。例如，假定想要匹配字符串 ‘First Name:’，接下来 是任意文本，接下来是 ‘Last Name:’，然后又是任意文本。
可以用 点-星(.*) 表示“任意文本”。句点字符表示 “除换行外所有单个字符”，星号字符表示 “前面字符出现零次或多次” 。

nameRegex = re.compile(r'First Name: (.*) Last Name: (.*)')
mo = nameRegex.search('First Name: AI Last Name: Sweety')
print(mo.group(1))
print(mo.group(2))

mo1 = nameRegex.findall('First Name: AI Last Name: Sweety')
print(mo1)

>> AI   # AI后 Last Name 前，跟再多的单词都会被提出来
>> Sweety
>> [('AI', 'Sweety')]

   


#点-星使用“贪心”模式:它总是匹配尽可能多的文本。要用“非贪心”模式匹配所有文本，就使用点-星和问号。
#像和大括号一起使用时那样，问号告诉 Python 用非贪心模式匹配。

#贪心模式和非贪心模式的区别
nongreedyRegex = re.compile(r'<.*?>')
mo = nongreedyRegex.search('<To serve man> for dinner.>')
print(mo.group())
greedyRegex = re.compile(r'<.*>')
mo1 = greedyRegex.search('<To serve man> for dinner.>')
print(mo1.group())
>> <To serve man>
>> <To serve man> for dinner.>

"""
解释：
两个正则表达式都可以翻译成“匹配一个左尖括号，接下来是任意字符，接下来是一个右尖括号”。
但是字符串'<To serve man> for dinner.>'对右肩括号有两种可能的匹配。
在非贪心的正则表达式中，Python 匹配最短可能的字符串:'<To serve man>'。 
在贪心版本中，Python 匹配最长可能的字符串:'<To serve man> for dinner.>'。
"""

   


13.2 用句点字符匹配换行

点-星将匹配除换行外的所有字符。通过传入 re.DOTALL 作为 **re.compile()**的第 二个参数，可以让句点字符匹配所有字符，包括换行字符。

noNewlineRegex = re.compile('.*')
noNewline = noNewlineRegex.search('Serve the public trust.\nProtect the innocent. \nUphold the law.').group()
print(noNewline)

newlineRegex = re.compile('.*', re.DOTALL)
newline = newlineRegex.search('Serve the public trust.\nProtect the innocent.\nUphold the law.').group()
print(newline)

>> Serve the public trust.
>> Serve the public trust.
>> Protect the innocent.
>> Uphold the law.
"""
j解释：
正则表达式 noNewlineRegex 在创建时没有向 re.compile()传入 re.DOTALL，它将匹配所有字符，直到第一个换行字符。
但是，newlineRegex 在创建时向 re.compile()传 入了 re.DOTALL，它将匹配所有字符。

"""

  


14. 正则表达式符号复习

?: 匹配零次或一次前面的分组。

*: 匹配零次或多次前面的分组。

+: 匹配一次或多次前面的分组。

{n}: 匹配 n 次前面的分组。

{n,}: 匹配 n 次或更多前面的分组。

{,m}: 匹配零次到 m 次前面的分组。

{n,m}: 匹配至少 n 次、至多 m 次前面的分组。

{n,m}?或*?或+?: 对前面的分组进行非贪心匹配。

^spam： 意味着字符串必须以 spam 开始。

spam$： 意味着字符串必须以 spam 结束。

. 匹配所有字符，换行符除外。

\d、\w 和\s: 分别匹配数字、单词和空格。

\D、\W 和\S: 分别匹配出数字、单词和空格外的所有字符。

[abc]: 匹配方括号内的任意字符(诸如 a、b 或 c)。

[^abc]: 匹配不在方括号内的任意字符。
15. 不区分大小写

#表达式匹配 完全不同的字符串:
regex1 = re.compile('RoboCop')
regex2 = re.compile('ROBOCOP') 
regex3 = re.compile('robOcop')
regex4 = re.compile('RobocOp')

"""
有时候只关心匹配字母，不关心它们是大写或小写。
要让正则表达式 不区分大小写，可以向 re.compile()传入 re.IGNORECASE 或 re.I，作为第二个参数。
"""
robocop = re.compile(r'robocop', re.I)
ro1 = robocop.search('RoboCop is part man, part machine, all cop.').group()
print(ro1)

ro2 = robocop.search('ROBOCOP protects the innocent.').group()
print(ro2)

ro3 = robocop.search('Al, why does your programming book talk about robocop so much?').group()
print(ro3)

>> RoboCop
>> ROBOCOP
>> robocop

   


16. 用sub方法替换字符串

Regex 对象的 **sub()**方法需要传入两个参数。第一个参数是一个字符串，用于取代发现的匹配。第二个参数是一个字符串，即正则表达式。sub() 方法返回替换完成后的字符串。

namesRegex = re.compile(r'Agent \w+') # 一个或多个字母，这里中间有空格，请注意
name = namesRegex.sub('CENSORD','Agent Alice gave the secret documents to Agent Bob.')
print(name)

>> CENSORD gave the secret documents to Agent Bob.

  


# sub()的第一 个参数中，可以输入\1、\2、\3......。表示“在替换中输入分组 1、2、3......的文本”
# 假定想要隐去密探的姓名，只显示他们姓名的第一个字母。
#要做到这一 点，可以使用正则表达式 Agent (\w)\w*，传入 r'\1****'作为 sub()的第一个参数。字符串中的\1 将由分组 1 匹配的文本所替代，
#也就是正则表达式的(\w)分组。

agentNamesRegex = re.compile(r'Agent (\w)\w*')
agent = agentNamesRegex.sub(r'\1****', 'Agent Alice told Agent Carol that Agent Eve knew Agent Bob was a double agent.')
print(agent)

# 解释： 下面是提取匹配跟随Agent后面的一个字母，匹配到第一个字母就返回
a = re.compile(r'Agent (\w)')
b = a.findall(r'Agent Alice told Agent Carol that Agent Eve knew Agent Bob was a double agent.')
print(b)

# 贪心匹配，匹配到跟随Agent后面的一单词的最后一个字母，匹配最后一个返回
c = re.compile(r'Agent (\w)*')
d = c.findall(r'Agent Alice told Agent Carol that Agent Eve knew Agent Bob was a double agent.')
print(d)

>> A**** told C**** that E**** knew B**** was a double agent.
>> ['A', 'C', 'E', 'B']
>> ['e', 'l', 'e', 'b']

   


17. 管理复杂的正则表达式

告诉 re.compile()，忽略正则表达式字符 串中的空白符和注释，从而缓解这一点。要实现这种详细模式，向 re.compile() 传入变量 re.VERBOSE，作为第二个参数。

phoneRegex = re.compile(r'''(
    (\d{3}|\(\d{3}\))?  # area code 
    (\s|-|\.)? # separator
    \d{3} # first 3 digits
    (\s|-|\.) # separator
    \d{4}  # last 4 digits
    (\s*(ext|x|ext.)\s*\d{2,5})? # extension
    )''', re.VERBOSE)  

"""
解释：
正则表达式字符串中的注释规则，与普通的 Python 代码一样:# 符号和它后面直到行末的内容，都被忽略。
而且，表示正则表达式的多行字符串中，多余的空白字符 也不认为是要匹配的文本模式的一部分。
"""

 


18. 组合使用 re.IGNOREC ASE、re.DOTALL 和 re.VERBOSE

希望在正则表达式中使用 re.VERBOSE 来编写注释，还希望使用 re.IGNORECASE 来忽略大小写的情况。re.compile() 函数只接受一个值作为它的第二参数。可以使用管道字符 ( | ) 将变量组合起来，从而绕过这个限制。管道字符称为 “按位或” 操作符。如果希望正则表达式不区分大小写，并且句点字符匹配换行，可以构造 **re.compile()**调用:

someRegex = re.compile('foo',re.IGNORECASE | re.DOTALL)
#使用第二个参数的全部 3 个选项
someRegexValue = re.compile('foo',re.IGNORECASE | re.DOTALL | re.VERBOSE)



3.re模块

        匹配对象以及group()和groups()方法：当处理正则表达式时，除了正则表达式对象之外，还有另一个对象类型：匹配对象。这些是成功调用match()或者search()返回的对象。匹配对象有两个主要的方法：group()和groups()。

        group()要么返回整个匹配对象，要么根据要求返回特定子组。

            >>> a = re.search(r"(\w)(.\d)","as.21")
            >>> a
            <_sre.SRE_Match object; span=(1, 4), match='s.2'>
            >>> a.group()  #返回整个匹配对象
            's.2'
            >>> a.group(0)
            's.2'
            >>> a.group(1) #根据要求返回特定子组
            's'
            >>> a.group(2)
            '.2'

         

        groups()仅返回一个包含唯一或者全部子组的元组。

            >>> a.groups()
            ('s', '.2')  #返回全部子组，是包含在一个元组中的

         

        如果没有子组的要求，那么当group()仍然返回整个匹配时，groups()返回一个空元组。

            >>> a = re.search(r"\d+","334354") #没有子组匹配
            >>> a.group() #返回整个匹配
            '334354'
            >>> a.groups() #返回空元组
            ()

         

 

 

    re.match(pattern,string,flags=0)

        match()试图从字符串的起始部分对模式进行匹配，如果成功则返回一个匹配对象，失败则返回None.

            >>> import re
            >>> re.match(r"www","www.baidu.com")
            <_sre.SRE_Match object; span=(0, 3), match='www'> # 返回的是匹配对象
             
            >>> type(re.match("www","www.baidu.com")) # 查看返回类型
            <class '_sre.SRE_Match'>
             
            >>> print(re.match("com","www.baidu.com"))
            None

         

 

     re.search(pattern, string, flags=0)

         搜索整个字符串并返回第一个成功的匹配，成功则返回一个匹配对象，失败则返回None.

            >>> re.search("com","www.baidu.com")
            <_sre.SRE_Match object; span=(10, 13), match='com'>
             
            >>> re.search("com","www.baidu.com.com.com")
            <_sre.SRE_Match object; span=(10, 13), match='com'> # 只返回第一个匹配的位置

         

 

     re.findall(pattern, string, flags=0)

         在字符串中找到正则表达式所匹配的所有子串，并返回一个列表。如果没有找到匹配，则返回空列表。

            >>> re.findall("com","www.baidu.com.com.com") 
            ['com', 'com', 'com']
            >>> re.findall("aa","www.baidu.com.com.com")
            []

         

 

    re.fullmatch(pattern, string, flags=0)

         完全匹配string，

            >>> print(re.fullmatch("com","com"))
            <_sre.SRE_Match object; span=(0, 3), match='com'>
             
            >>> print(re.fullmatch("com","comssa"))  #必须要完全匹配
            None

         

 

     re.finditer(pattern,string,flags=0)

         查找所有匹配成功的字符串，并返回iteror

            >>> re.finditer("com","www.baidu.com.com.com") #返回迭代器对象
            <callable_iterator object at 0x00000247617F06D8>
             
            >>> list(re.finditer("com","www.baidu.com.com.com"))
            [<_sre.SRE_Match object; span=(10, 13), match='com'>, <_sre.SRE_Match object; span=(14, 17), match='com'>, <_sre.SRE_Match object; span=(18, 21), match='com'>]

         

 

 

    re.sub()和re.subn() 

         re.sub用于替换字符串中的匹配项，
        pattern : 正则中的模式字符串。
        repl : 替换的字符串，也可为一个函数。
        string : 要被查找替换的原始字符串。
        count : 模式匹配后替换的最大次数，默认 0 表示替换所有的匹配。

            >>> re.sub(r"[ae]","?","adsdeef")
            '?dsd??f'
            >>> re.subn(r"[ae]","?","adsdeef")  # subn()比sub()多返回了一个替换的总数
            ('?dsd??f', 3)


4.datetime模块学习

datetime模块提供了处理日期和时间的类，既有简单的方式，又有复杂的方式。它虽然支持日期和时间算法，但其实现的重点是为输出格式化和操作提供高效的属性提取功能。

datetime.date	表示日期，常用的属性有：year, month和day
datetime.time	表示时间，常用属性有：hour, minute, second, microsecond
datetime.datetime	表示日期时间
datetime.timedelta	表示两个date、time、datetime实例之间的时间间隔，分辨率（最小单位）可达到微秒
datetime.tzinfo	时区相关信息对象的抽象基类。它们由datetime和time类使用，以提供自定义时间的而调整。
datetime.timezone	Python 3.2中新增的功能，实现tzinfo抽象基类的类，表示与UTC的固定偏移量


5.http请求
安装Requests库

GET请求

POST请求 

响应码code和响应头headers的处理

请求超时设置