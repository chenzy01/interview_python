第一部分 Python基for础篇（80题）

1、为什么学习Python？
for money
2、通过什么途径学习的Python？
书，网络，公众号
3、Python和Java、PHP、C、C#、C++等其他语言的对比？
4、简述解释型和编译型编程语言？
概念：
编译型语言：把做好的源程序全部编译成二进制代码的可运行程序。然后，可直接运行这个程序。
解释型语言：把做好的源程序翻译一句，然后执行一句，直至结束！
区别：
编译型语言，执行速度快、效率高；依赖编译器、跨平台性差些。如C、C++、Delphi、Pascal，Fortran。
解释型语言，执行速度慢、效率低；依赖解释器、跨平台性好。如Java、Basic.
通俗的讲，编译语言是在编译后可以直接运行，而解释语言的执行需要一个解释环境。
 java很特殊，java程序也需要编译，但是没有直接编译称为机器语言，而是编译称为字节码，然后用解释方式执行字节码。


5、Python解释器种类以及特点？


6、位和字节的关系？


7、b、B、KB、MB、GB 的关系？
    1 B = 8b （8个bit/ 位） 一个字节（byte）等于8位（bit）
    1 kB = 1024 B (kB - kilobajt) 
    1 MB = 1024 kB (MB - megabajt)
    1 GB = 1024 MB (GB - gigabajt) 
    
8、请至少列举5个 PEP8 规范（越多越好）。
 1)缩进。4个空格的缩进（编辑器都可以完成此功能），不使用Tap，更不能混合使用Tap和空格。
  2)每行最大长度79，换行可以使用反斜杠，最好使用圆括号。换行点要在操作符的后边敲回车。
  3)类和top-level函数定义之间空两行；类中的方法定义之间空一行；函数内逻辑无关段落之间空一行；其他地方尽量不要再空行。
  4)模块内容的顺序：模块说明和docstring—import—globals&constants—其他定义。其中import部分，又按标准、三方和自己编写顺序依次排放，之间空一行。
  5)如果采用from XX import XX引用库，可以省略‘module.’，都是可能出现命名冲突，这时就要采用import XX

9、通过代码实现如下转换：
二进制转换成十进制：v = “0b1111011”
    >>> v='0b1111011'
    >>> int(v,2)
    123
十进制转换成二进制：v = 18 
>>> v=18
>>> bin(18)
'0b10010'
八进制转换成十进制：v = “011” 
>>> v='011'
>>> int(v,8)
9
十进制转换成八进制：v = 30 
>>> v=30
>>> oct(v)
'0o36'
十六进制转换成十进制：v = “0x12” 
>>>v = “0x12” 
>>> int('v',16)
18
十进制转换成十六进制：v = 87
>>> v=87
>>> hex(v)
'0x57'
10、请编写一个函数实现将IP地址转换成一个整数。
 	
。
如 10.3.9.12 转换规则为：

 10           00001010
 3            00000011
 9            00001001
 12           00001100

再将以上二进制拼接起来计算十进制结果：00001010 00000011 00001001 00001100 = ？

import socket, struct
 
def ip2long(ip):
    """
    Convert an IP string to long
    """
    packedIP = socket.inet_aton(ip)
    return struct.unpack("!L", packedIP)[0]

11、python递归的最大层数？
>>> import sys
#获取最大递归层数
>>> sys.getrecursionlimit
<built-in function getrecursionlimit>
>>> sys.getrecursionlimit ()
1000
#setrecursionlimit函数可以设置最大递归数

12、求结果：

v1 = 1 or 3 
>>> 1
v2 = 1 and 3
>>> 3
v3 = 0 and 2 and 1
>>> 0
v4 = 0 and 2 or 1
>>> 1
v5 = 0 and 2 or 1 or 4
>>> 1
v6 = 0 or Flase and 1
>>> 0
 在Python 中，and 和 or 执行布尔逻辑演算，如你所期待的一样，但是它们并不返回布尔值；而是，返回它们实际进行比较的值之一。
        在布尔上下文中从左到右演算表达式的值，使用and的话，如果布尔上下文中的所有值都为真，那么 and 返回最后一个值；如果布尔上下文中的某个值为假，则 and 返回第一个假值
     使用or的话， 如果有一个值为真，or 立刻返回该值；如果所有的值都为假，or 返回最后一个假值

    注意 ：or 在布尔上下文中会一直进行表达式演算直到找到第一个真值，然后就会忽略剩余的比较值；布尔环境中，0、”、[]、()、{}、None为假；其它任何东西都为真。但是可以在类中定义特定的方法使得类实例的演算值为假。

13、ascii、unicode、utf-8、gbk 区别？
ascii：英语字符与二进制位之间的关系，ASCII 码一共规定了128个字符的编码,对于超出一个字节的字符无法更好的表示。
unicode：规定必须用两个字节表示世界上几乎所有的字符,对于不足两个字节的字符，使用unicode表示会极大浪费存储空间。
utf-8：是一种变长的编码方式。它可以使用1~4个字节表示一个符号，根据不同的符号而变化字节长度。TF-8为Unicode的一种实现编码，Unicode编码可以通过一定的规则进行转变。
gbk：编码为中国特有编码，但也是在ANSI基础上演变出来的，包含两个字节，其中中文编码与Unicode的中文编码不一样。

14、字节码和机器码的区别？
机器码，学名机器语言指令，是电脑CPU直接读取运行的机器指令，运行速度最快
字节码是一种中间状态（中间码）的二进制代码（文件）。需要直译器转译后才能成为机器码。字节码的实现方式是通过编译器和虚拟机器。编译器将源码编译成字节码，特定平台上的虚拟机器将字节码转译为可以直接执行的指令。

15、三元运算规则以及应用场景？
三元运算符通常在Python里被称为条件表达式，这些表达式基于真(true)/假(false)的条件判断
python中的格式：为真时的结果 if 判定条件 else 为假时的结果 

16、列举 Python2和Python3的区别？

17、用一行代码实现数值交换：
a = 1
b = 2
a, b = b, a

18、Python3和Python2中 int 和 long的区别？
    Python 2非浮点数有int和long类型。int类型的最大值不能超过sys.maxint（见附录），而且这个最大值是平台相关的。长整型long可以通过在数字的末尾附上一个L来定义，它比int类型表示的数字范围更大。
    在Python 3里，只有一种整数类型int

19、xrange和range的区别？
    xrange用法与range完全相同，所不同的是xrange生成的不是一个数组，而是一个生成器，xrange做循环的性能比range好

20、文件操作时：xreadlines和readlines的区别？
readlines() 读取文件所有内容，按行为单位放到一个列表中，返回list类型。
xreadlines() 返回一个生成器，来循环操作文件的每一行。

21、列举布尔值为False的常见值？
在Python中所有的对象都可以进行真值测试，下面罗列一下判断为假的情况：
None
False
数值中的零，包括0，0.0，0j（虚数）
空序列，包括空字符串(”)，空元组(())，空列表([])
空的字典{}
自定义的对象的实例，该对象的__bool__方法返回False或者__len__方法返回0
除了以上的情况外，所有的对象在if或者while语句中的表现都为真。

22、字符串、列表、元组、字典每个常用的5个方法？
用x代表字符串、列表、元组或字典，常用的5个方法有：
x.strip(“”) 去掉空格
x.split(“y”) 按某个字符切割
x.count("字符串") 统计字符串（字符）出现的个数
x.[i] 按索引取字符
x.[1:3] 切片操作
x.in("abc") 判断某个字符（字符串）是否在另一个字符串当中
x.len("abc") 求字符串长度
x.find("字符") 寻找字符
x.replace("") 字符串替换

23、lambda表达式格式以及应用场景？
Lambda函数能接收任何数量的参数但只能返回一个表达式的值 
匿名函数不能直接调用print，因为lambda需要一个表达式．
应用场景:函数作为参数传递
lambda格式:lambda <变量名> : <逻辑表达式>   #冒号前是参数,可以有多个,用逗号隔开,冒号右边的返回值
#例如多变量：lambda x,y : x+y

24、pass的作用？
 1)、pass语句什么也不做，一般作为占位符或者创建占位程序，pass语句不会执行任何操作
 2)、保证格式完整 
 3)、保证语义完整

25、*arg和**kwarg作用
*args是可变的positional arguments列表（非关键字参数，传递的是元组），**kwargs是可变的keyword arguments列表（传递的是字典）。并且，*args必须位于**kwargs之前。*args和**kwargs允许给函数传不定数量的参数。

26、is和==的区别
is就是用来判断两个变量的id是否相等，当两个变量的id相等时，说明这两个变量指向的地址是相同的，那么这两个变量的一切属性都相同。（每个对象包含3个属性，id，type，value）
python为了实现对内存的有效利用，对小整数[-5,256]内的整数会进行缓存，不在该范围内的则不会缓存，具体如下
>>> a = 255
>>> b = 255
>>> a is b
True
>>> c = 257
>>> d = 257
>>> c is d
False
当你写成a==b时候，实际上比较的是id(a)这个地址指向的值是不是和id(b)这个地址指向的值一样。结果为True。（c == d 也是True）
总结
==比较操作符：用来比较两个对象是否相等，value(值)做为判断因素；
is同一性运算符：比较判断两个对象是否相同，id(地址)做为判断因素。

27、简述Python的深浅拷贝以及应用场景？
    浅拷贝创造了一个新的对象，但是新对象里也全部都是老对象里面子结构的引用。因此经过浅拷贝之后，通过赋值号来改变新内容当然不会改变原内容，但是一旦子结构中存在可变类型的对象，那么修改这些可变类型对象的值当然就会影响原内容。
而深拷贝与浅拷贝唯一的不同仅仅是在深拷贝时，遇到了原内容中的可变类型的子结构，不会直接创建一个引用指向它，而是重新创建一个新的对象并指向新创建的对象，并递归的进行深拷贝。
例如
浅拷贝：
x = [1,[2,3]]
y = copy.copy(x)#或者y=x[:]
y[1].append(4)
print(x,y)
y[1][0] = 666
print(x,y)

[1, [2, 3, 4]] [1, [2, 3, 4]]
[1, [666, 3, 4]] [1, [666, 3, 4]]

深拷贝：
x = [1,[2,3]]
y = copy.deepcopy(x)
y[1].append(4)
print(x,y)
y[1][0] = 666
print(x,y)

[1, [2, 3]] [1, [2, 3, 4]]
[1, [2, 3]] [1, [666, 3, 4]]

下面的代码将会直观的展示深拷贝与浅拷贝的区别。
x = ['a',['b',12]]
y = copy.copy(x)
z = copy.deepcopy(x)
print(id(x),id(x[0]),id(x[1]))
print(id(y),id(y[0]),id(y[1]))
print(id(z),id(z[0]),id(z[1]))

4369860232 4337588016 4369859592
4370811144 4337588016 4369859592
4370247176 4337588016 4370766728

Python中对象的赋值都是进行对象引用（内存地址）传递
使用copy.copy()，可以进行对象的浅拷贝，它复制了对象，但对于对象中的元素，依然使用原始的引用.
如果需要复制一个容器对象，以及它里面的所有元素（包含元素的子元素），可以使用copy.deepcopy()进行深拷贝
对于非容器类型（如数字、字符串、和其他'原子'类型的对象）没有被拷贝一说
如果元祖变量只包含原子类型对象，则不能深拷贝

28、Python垃圾回收机制？
29、Python的可变类型和不可变类型？
Python的每个对象都分为可变和不可变，主要的核心类型中，数字、字符串、元组是不可变的，列表、字典、set是可变的。
对不可变类型的变量重新赋值，实际上是重新创建一个不可变类型的对象，并将原来的变量重新指向新创建的对象（如果没有其他变量引用原有对象的话（即引用计数为0），原有对象就会被回收）。

30、求结果：
v = dict.fromkeys(['k1','k2'],[])
v[‘k1’].append(666)
print(v)
v[‘k1’] = 777
print(v)
输出：
{'k2': [666], 'k1': [666]}
{'k2': [666], 'k1': 777}

（Python 中 list 是可变类型，在作为参数传递的时候是传引用的。
所以 fromkeys 函数把所有 key 都指向了同一个空列表。改动其中任何一个，其他的都改掉了）

31、求结果：

>>[6,6,6,6]

32、列举常见的内置函数？
 Python有许多内置的函数和类型，下面是官网给出的所有的内置函数和类型。 


33、filter、map、reduce的作用？
python 中的filter， map, reduce方法解释:
filter:
filter方法调用：
resultlst = filter(func, seq)
@param func: 可调用对象，接受seq中的元素作为参数
@param seq: 可迭代对象，其中每个元素都要被传入func执行一次；
filter的作用：
对seq可迭代序列或者对象的每一个元素调用一次func，如果func返回值为True，则将该元素插入返回结果列表。反之，则丢弃；
例如：
a = [1,2,3,4,5]
result = filter(lambda x : x > 3, a)
则返回结果是：[4,5]
 
注意，filter的func可调用对象必须返回一个具有“bool属性”的值。所谓具有bool属性，即是指该返回值要能够与bool真值进行比较。在python中，几乎所有对象都能够判断真假。filter方法本身返回的是seq元素的列表子集。并非func返回的结果，func只是告诉filter在seq中怎么去选取元素构成列表返回（也就是能够使func调用对象返回bool真值的那些元素）

map:
map方法调用：
map(func, seq)
@param func: 可调用对象，接受seq中的元素作为参数；
@param seq: 可迭代对象。其中每个迭代元素都会被传入map函数执行一次；
map方法的作用：
对seq可迭代对象中的每个元素，作为func参数调用一次, 并把func结果添加到返回列表中；
例如：
a = [1,2, 3,4,5]
resultlst = map(lambda x : x + 1， a)
返回结果是：[2,3,4,5,6]
 
假如我们使用filter中同样的lambda表达式来调用a中的元素，即：
a = [1,2, 3,4,5]
resultlst = map(lambda x : x > 3， a)
返回结果是：[False,False,Flase,True,True]
 
这就是说，map函数对seq中的每个元素，将一定会有一个与之对应的返回值。这个返回值就是将该元素传递给func后，由func执行返回的结果。
 
reduce:
reduce方法调用：
reduce(func, seq [, init])
@param func: 特殊的可调用对象。所谓特殊，是该可调用对象要接受两个参数。
@param seq: 可迭代对象，同样，该对象中的每个元素将会被func处理一次；
@param init: 初始值。
reduce方法的作用：
对seq中的从左到右的每两个元素，调用func。然后将本次结果传递到下一次调用。
例如：
a = [1,2,3,4,5]
reduce(lambda x, y : x +y, a)
则返回值为：15
加入我们设定init的值，即：
a = [1,2,3,4,5]
reduce(lambda x, y : x +y, a， 3)
则返回值为：18
 
注意：传递给reduce的func,必须要能接受两个参数。并返回一个结果。这个结果将会是传递给func进行下次一调用；上面的例子，调用过程是：
1,func(1, 2) 返回 x1
2,func(x1, 3) 返回 x2
3,func(x2, 4) 返回 x3

34、一行代码实现9*9乘法表
print('\n'.join(' '.join("%dx%d=%-2d" % (x, y, x*y) for x in range(1, y+1)) for y in range(1, 10)))

35、如何安装第三方模块？以及用过哪些第三方模块？
在Python中，安装第三方模块，是使用包管理工具pip进行安装；
在Mac或Linux系统中，自带pip，在Window系统中，需要先在命令行窗口下检查是否已安装pip工具，若无，则必须先安装pip，后才能利用pip安装第三方模块。
用过的第三方模块：PIL,Numpy,Panda,Flask,SQLAlchemy,Pillow

36、至少列举8个常用模块都有那些？
requests,flask,sqlalchemy,numpy,panda,pip,PIL,django,sys,datatime,math,time,os,render

37、re的match和search区别？
match（）函数只检测RE是不是在string的开始位置匹配（只从开始进行匹配）， search()会扫描整个string查找匹配（任意位置进行匹配）, 也就是说match（）只有在0位置匹配成功的话才有返回，如果不是开始位置匹配成功的话，match()就返回none；search()会扫描整个字符串并返回第一个成功的匹配；
模式：
re.match(pattern, string[, flags])
re.search(pattern, string[, flags])

另外：
findall
re.findall(pattern, string[, flags])
返回string中所有与pattern相匹配的全部字串，返回形式为数组。
finditer
 re.finditer(pattern, string[, flags])
返回string中所有与pattern相匹配的全部字串，返回形式为迭代器。

若匹配成功，match()/search()返回的是Match对象，finditer()返回的也是Match对象的迭代器，获取匹配结果需要调用Match对象的group()、groups或group(index)方法
group()：母串中与模式pattern匹配的子串；
group(0)：结果与group()一样；
groups()：所有group组成的一个元组，group(1)是与patttern中第一个group匹配成功的子串，group(2)是第二个，依次类推，如果index超了边界，抛出IndexError；
findall()：返回的就是所有groups的数组，就是group组成的元组的数组，母串中的这一撮组成一个元组，那一措组成一个元组，这些元组共同构成一个list，就是findall()的返回结果。另，如果groups是只有一个元素的元组，findall的返回结果是子串的list，而不是元组的list了。

38、什么是正则的贪婪匹配？
贪婪与非贪婪模式影响的是被量词修饰的子表达式的匹配行为，贪婪模式在整个表达式匹配成功的前提下，尽可能多的匹配，而非贪婪模式在整个表达式匹配成功的前提下，尽可能少的匹配。正则默认开启贪婪模式
编程中如何区分两种模式
　　默认是贪婪模式；在量词后面直接加上一个问号？就是非贪婪模式。
　　量词：{m,n}：m到n个
　　　　　*：任意多个
　　　　　+：一个到多个
　　　　　？：0或一个

39、求结果： a. [ i % 2 for i in range(10) ] b. ( i % 2 for i in range(10) )
a. [ i % 2 for i in range(10) ] 
>>>[0, 1, 0, 1, 0, 1, 0, 1, 0, 1]
b. ( i % 2 for i in range(10) )
>>><generator object <genexpr> at 0x000000000215E678>

a通过列表生成式形成了一个列表，而b则式一个generator(生成器)，区别仅在于最外层的[]和()。
要打印b的内容，要通过generator的next（）方法，或通过for循环打印出来
for n in b:
	print (n)

0
1
0
1
0
1
0
1
0
1

40、求结果： a. 1 or 2 b. 1 and 2 c. 1 < (2==2) d. 1 < 2 == 2
>>> 1 or 2
1
>>> 1 and 2
2
>>> 1 < (2==2)
False
>>> 1 < 2 == 2
True

41、def func(a,b=[]) 这种写法有什么坑？
Python函数在定义的时候，默认参数b的值就被计算出来了，即[]，因为默认参数b也是一个变量，它指向对象[]，每次调用该函数，如果改变了b的内容，则下次调用时，默认参数的内容就变了，不再是函数定义时的[]了。
所以，定义默认参数要牢记一点：默认参数必须指向不变对象！
要修改上面的例子，我们可以用None这个不变对象来实现：
def func(a,b=None):
    if b is None:
        b = []	
        pass
(请注意，参数定义的顺序必须是：必选参数、默认参数、可变参数和关键字参数。)
任意函数，都可以通过类似func(*args, **kw)的形式调用它，无论它的参数是如何定义的。

42、如何实现 “1,2,3” 变成 [‘1’,’2’,’3’] ?== 
我的代码：
a = "1,2,3"
def StrToList(a):
    tolist =  list(a.split(','))
    return tolist

43、如何实现[‘1’,’2’,’3’]变成[1,2,3] ?
我的代码：
def listtoint(a):
	results = [int(i) for i in a]
	return results

def listtoint(a):
	results = list(map(int,a))
	return results
统一调用：
>>>strtoint = ['1','2','3']
>>>resutl = listtoint(strtoint)
>>>[1, 2, 3]


44、比较： a = [1,2,3] 和 b = [(1),(2),(3) ] 以及 b = [(1,),(2,),(3,) ] 的区别？
a = [1,2,3] ，a是一个列表，列表中元素可修改，如进行元素增加，删除，切片等操作
b = [(1),(2),(3) ] ，b中(1),(2),(3),python解释器把它当做一个表达式，即(1)=1,(2)=2,所以 [(1),(2),(3) ]= [1,2,3]=a
b = [(1,),(2,),(3,) ],b中每个元素是单个值的元组，元祖中的内容不可修改，但列表可以增加新的元组。

45、如何用一行代码生成[1,4,9,16,25,36,49,64,81,100] ?
代码1：result = [x**2 for x in range(1,11)]
代码2：result = list(map(lambda x: x**2,range(1,11)))

46、一行代码实现删除列表中重复的值 ?
1）、采用set 方法
>>> res = [1,2,5,3,6,3,2,1,5,2]
>>> res = list(set(res))
>>> res
[1, 2, 3, 5, 6]

2）、将列表的值转换为自动的key
>>> res1 = [1,2,5,3,6,3,2,1,5,2]
>>> res2 = {}.fromkeys(res1).keys()
>>> res2
dict_keys([1, 2, 3, 5, 6])

3）、迭代
res3 =  [1,2,5,3,6,3,2,1,5,2]
res4=[]
for i in res3:
    if not i in res4:
        res4.append(i)
print(list4)

47、如何在函数中设置一个全局变量 ?
1）、python 查找变量的顺序是：先局部变量，再全局变量
2）、在一个函数过程中声明的变量，首先可看做是局部变量；若要在该过程内使用全局变量，在变量面前使用关键字“global”声明。
3）、局部变量的作用域属于其所属函数的作用域，既函数完成，该变量既结束；而全局变量作用于整个脚本，直到脚本结束才完成。
具体说明参考以下网址：
https://blog.csdn.net/dongtingzhizi/article/details/8973569
https://blog.csdn.net/Eastmount/article/details/48766861

48、logging模块的作用？以及应用场景？
日志:一种用来记录当软件在运行时所发生的事件的方法
日志作用：
1）、程序调试
2）、监控系统或软件运行时的情况是否正常
3）、运行故障分析与问题定位
python logging 模块的默认级别：
日志等级（level）
描述
DEBUG
最详细的日志信息，典型应用场景是 问题诊断
INFO
信息详细程度仅次于DEBUG，通常只记录关键节点信息，用于确认一切都是按照我们预期的那样进行工作
WARNING
当某些不期望的事情发生时记录的信息（如，磁盘可用空间较低），但是此时应用程序还是正常运行的
ERROR
由于一个更严重的问题导致某些功能不能正常运行时记录的信息
CRITICAL
当发生严重错误，导致应用程序不能继续运行时记录的信息
logging模块的四大组件
组件
说明
loggers
提供应用程序代码直接使用的接口
handlers
用于将日志记录发送到指定的目的位置
filters
提供更细粒度的日志过滤功能，用于决定哪些日志记录将会被输出（其它的日志记录将会被忽略）
formatters
用于控制日志信息的最终输出格式
参考资料：
https://www.cnblogs.com/yyds/p/6901864.html

49、请用代码简答实现stack ？
栈数据结构的特点：后进先出（Last In First Out - LIFO）
网络例子，栈的实现：
(栈可以用顺序表方式实现，也可以用链表方式实现)
class Stack(object):
    # 初始化栈为空列表
    def __init__(self):
        self.items = []

    # 判断栈是否为空，返回布尔值
    def is_empty(self):
        return self.items == []

    # 返回栈顶元素
    def peek(self):
        return self.items[len(self.items) - 1]

    # 返回栈的大小
    def size(self):
        return len(self.items)

    # 把新的元素堆进栈里面（程序员喜欢把这个过程叫做压栈，入栈，进栈……）
    def push(self, item):
        self.items.append(item)

    # 把栈顶元素丢出去（程序员喜欢把这个过程叫做出栈……）
    def pop(self, item):
        return self.items.pop()


if __name__ == __main__:
    # 初始化一个栈对象
    my_stack = Stack()
    # 把'h'丢进栈里
    my_stack.push('h')
    # 把'a'丢进栈里
    my_stack.push('a')
    # 看一下栈的大小（有几个元素）
    print my_stack.size()
    # 打印栈顶元素
    print my_stack.peek()
    # 把栈顶元素丢出去，并打印出来
    print my_stack.pop()
    # 再看一下栈顶元素是谁
    print my_stack.peek()
    # 这个时候栈的大小是多少？
    print my_stack.size()
    # 再丢一个栈顶元素
    print my_stack.pop()
    # 看一下栈的大小
    print my_stack.size
    # 栈是不是空了？
    print my_stack.is_empty()
    # 哇~真好吃~
    print ('Yummy~')
参考：https://blog.csdn.net/xuqiang20121991/article/details/54139431

50、常用字符串格式化哪几种？
1）、使用format方法格式化字符串
[[fill]align][sign][#][0][width][,][.precision][type]
fill           【可选】空白处填充的字符
align        【可选】对齐方式（需配合width使用）
<，内容左对齐
>，内容右对齐(默认)
＝，内容右对齐，将符号放置在填充字符的左侧，且只对数字类型有效。 即使：符号+填充物+数字
^，内容居中
sign         【可选】有无符号数字
+，正号加正，负号加负；
 -，正号不变，负号加负；
空格 ，正号空格，负号加负；
#            【可选】对于二进制、八进制、十六进制，如果加上#，会显示 0b/0o/0x，否则不显示
，            【可选】为数字添加分隔符，如：1,000,000
width       【可选】格式化位所占宽度
.precision 【可选】小数位保留精度
type         【可选】格式化类型
传入” 字符串类型 “的参数
s，格式化字符串类型数据
空白，未指定类型，则默认是None，同s
传入“ 整数类型 ”的参数
b，将10进制整数自动转换成2进制表示然后格式化
c，将10进制整数自动转换为其对应的unicode字符
d，十进制整数
o，将10进制整数自动转换成8进制表示然后格式化；
x，将10进制整数自动转换成16进制表示然后格式化（小写x）
X，将10进制整数自动转换成16进制表示然后格式化（大写X）
传入“ 浮点型或小数类型 ”的参数
e， 转换为科学计数法（小写e）表示，然后格式化；
E， 转换为科学计数法（大写E）表示，然后格式化;
f ， 转换为浮点型（默认小数点后保留6位）表示，然后格式化；
F， 转换为浮点型（默认小数点后保留6位）表示，然后格式化；
g， 自动在e和f中切换
G， 自动在E和F中切换
%，显示百分比（默认显示小数点后6位）

2）、使用 百分号%形式
%[(name)][flags][width].[precision]typecode
(name)      可选，用于选择指定的key
flags          可选，可供选择的值有:
+       右对齐；正数前加正好，负数前加负号；
-        左对齐；正数前无符号，负数前加负号；
空格    右对齐；正数前加空格，负数前加负号；
0        右对齐；正数前无符号，负数前加负号；用0填充空白处
width         可选，占有宽度
.precision   可选，小数点后保留的位数
typecode    必选
s，获取传入对象的__str__方法的返回值，并将其格式化到指定位置
r，获取传入对象的__repr__方法的返回值，并将其格式化到指定位置
c，整数：将数字转换成其unicode对应的值，10进制范围为 0 <= i <= 1114111（py27则只支持0-255）；字符：将字符添加到指定位置
o，将整数转换成 八  进制表示，并将其格式化到指定位置
x，将整数转换成十六进制表示，并将其格式化到指定位置
d，将整数、浮点数转换成 十 进制表示，并将其格式化到指定位置
e，将整数、浮点数转换成科学计数法，并将其格式化到指定位置（小写e）
E，将整数、浮点数转换成科学计数法，并将其格式化到指定位置（大写E）
f， 将整数、浮点数转换成浮点数表示，并将其格式化到指定位置（默认保留小数点后6位）
F，同上
g，自动调整将整数、浮点数转换成 浮点型或科学计数法表示（超过6位数用科学计数法），并将其格式化到指定位置（如果是科学计数则是e；）
G，自动调整将整数、浮点数转换成 浮点型或科学计数法表示（超过6位数用科学计数法），并将其格式化到指定位置（如果是科学计数则是E；）
%，当字符串中存在格式化标志时，需要用 %%表示一个百分号
注：Python中百分号格式化是不存在自动将整数转换成二进制表示的方式
参考：https://www.cnblogs.com/caibao666/p/6430109.html

51、简述 生成器、迭代器、可迭代对象 以及应用场景？
迭代器是可迭代对象，必须实现__iter__()和next()方法；可迭代对象必须实现__iter__()方法，可迭代对象不一定是迭代器；生成器一定是迭代器，自动实现了__iter__()和next()方法
参考：https://blog.csdn.net/jinixin/article/details/72232604
           http://kaito-kidd.com/2018/04/18/python-advance-iterator-generator/

52、用Python实现一个二分查找的函数。
Python实现二分查找算法，代码如下：
#!/usr/bin/python
#coding=utf-8

def search(find, find_list):
    low = 0
    high = len(find_list)

    while low <= high:
        #mid取整数
        mid = (low + high) // 2
        if find == find_list[mid]:
            return (mid +1)
        #左边查询
        elif find < find_list[mid]:
            high = mid - 1
        #右边查询
        else:
            low = mid + 1
    #查找不到返回 -1
    return -1

search_list = [1,3,4,6,55,3,88,22,56]
search_list.sort()
print("原序列为：",search_list)
try:
    find =int( input("输入一个整数："))
except:
    print("请输入整数")
    exit()

result = search(find, search_list)
if result != -1:
    print("要查找的值{}，在列表中第{}位".format(find, result))
else:
    print("查询无数据")
参考资料：
https://blog.csdn.net/SeeTheWorld518/article/details/47844693

53、谈谈你对闭包的理解？
概念：闭包，一个函数（外函数）中嵌套了另一个函数（内函数），内函数调用了外函数的变量，并且内函数被当成外函数的返回对象（外函数的返回值是内函数的引用，即内函数的名字）。
参考：https://www.cnblogs.com/Lin-Yi/p/7305364.html

54、os和sys模块的作用？
os模块负责程序与操作系统的交互，提供了访问操作系统底层的接口;sys模块负责程序与python解释器的交互，提供了一系列的函数和变量，用于操控python的运行时环境。
参考：https://blog.csdn.net/liu5257/article/details/53740214

55、如何生成一个随机数？
使用random模块中一些常用的方法
random.uniform()：生成指定范围内的随机符点数。
random.uniform(10,20)  #18.2635256
random.randint()：生成指定范围内的整数。
random.randint(12,20) #生成的随机数n: 12 <= n <= 20
random.randrange()：  从指定范围内，按指定基数递增的集合中，下限必须小于上限
random.randrange(0, 101, 2) #42  或 random.randrange(0, 101) #49
random.random() ：生成随机浮点数，范围是0-1
random.random()  #0.881
random.sample()：从多个字符中选取特定数量的字符
random.sample('abcdefghij',3)  #['a', 'd', 'b']
random.choice()：选取随机字符
random.choice('abcdefg&#%^*f') #'d'
random.shuffle() : 随机排序
 items = [1, 2, 3, 4, 5, 6]
>>> random.shuffle(items)
>>> items
[3, 2, 5, 6, 4, 1]

56、如何使用python删除一个文件？
参考：https://www.cnblogs.com/mttnor/p/python.html

57、谈谈你对面向对象的理解？
面向对象：面向对象的编程---object oriented programming，简称：OOP，是一种编程的思想。OOP把对象当成一个程序的基本单元，一个对象包含了数据和操作数据的函数。面向对象的出现极大的提高了编程的效率，使其编程的重用性增高。
面向对象一些特点：
1、多态（polymorphism）：一个函数有多种表现形式，调用一个方法有多种形式，但是表现出的方法是不一样的。
2、继承（inheritance）子项继承父项的某些功能，在程序中表现某种联系
3、封装（encapsulation）把需要重用的函数或者功能封装，方便其他程序直接调用
4、类：对具有相同数据或者方法的一组对象的集合
5、对象：对象是一个类的具体事例
6、实例化：是一个对象事例话的实现
7、标识：每个对象的事例都需要一个可以唯一标识这个事例的标记
8、实例属性：一个对象就是一组属性的集合
9、事例方法：所有存取或者更新对象某个实例一条或者多条属性函数的集合。
10、类属性：属于一个类中所有对象的属性，
11、类方法：

58、Python面向对象中的继承有什么特点？
59、面向对象深度优先和广度优先是什么？
60、面向对象中super的作用？
61、是否使用过functools中的函数？其作用是什么？
62、列举面向对象中带爽下划线的特殊方法，如：__new__、__init__
63、如何判断是函数还是方法？
64、静态方法和类方法区别？
65、列举面向对象中的特殊成员以及应用场景
66、1、2、3、4、5 能组成多少个互不相同且无重复的三位数
67、什么是反射？以及应用场景？
68、metaclass作用？以及应用场景？
69、用尽量多的方法实现单例模式。
70、装饰器的写法以及应用场景。
71、异常处理写法以及如何主动跑出异常（应用场景）
72、什么是面向对象的mro
73、isinstance作用以及应用场景？

74、写代码并实现：

Given an array of integers, return indices of the two numbers such that they add up to a specific target.You may assume that each input would 
have exactly one solution, and you may not use the same element twice.
Example:
          Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
           return [0, 1]

75、json序列化时，可以处理的数据类型有哪些？如何定制支持datetime类型？
76、json序列化时，默认遇到中文会转换成unicode，如果想要保留中文怎么办？
77、什么是断言？应用场景？
78、有用过with statement吗？它的好处是什么？
79、使用代码实现查看列举目录下的所有文件。
80、简述 yield和yield from关键字。

第二部分 网络编程和并发（34题）

1、简述 OSI 七层协议。
2、什么是C/S和B/S架构？
3、简述 三次握手、四次挥手的流程。
4、什么是arp协议？
5、TCP和UDP的区别？
6、什么是局域网和广域网？
7、为何基于tcp协议的通信比基于udp协议的通信更可靠？
8、什么是socket？简述基于tcp协议的套接字通信流程。
9、什么是粘包？ socket 中造成粘包的原因是什么？ 哪些情况会发生粘包现象？
10、IO多路复用的作用？
11、什么是防火墙以及作用？
12、select、poll、epoll 模型的区别？
13、简述 进程、线程、协程的区别 以及应用场景？
14、GIL锁是什么鬼？
15、Python中如何使用线程池和进程池？
16、threading.local的作用？
17、进程之间如何进行通信？
18、什么是并发和并行？
19、进程锁和线程锁的作用？
20、解释什么是异步非阻塞？
21、路由器和交换机的区别？
22、什么是域名解析？
23、如何修改本地hosts文件？
24、生产者消费者模型应用场景及优势？
25、什么是cdn？
26、LVS是什么及作用？
27、Nginx是什么及作用？
28、keepalived是什么及作用?
29、haproxy是什么以及作用？
30、什么是负载均衡？
31、什么是rpc及应用场景？
32、简述 asynio模块的作用和应用场景。
33、简述 gevent模块的作用和应用场景。
34、twisted框架的使用和应用？

第三部分 数据库和缓存（46题）

1、列举常见的关系型数据库和非关系型都有那些？
2、MySQL常见数据库引擎及比较？
3、简述数据三大范式？
4、什么是事务？MySQL如何支持事务？
5、简述数据库设计中一对多和多对多的应用场景？
6、如何基于数据库实现商城商品计数器？
7、常见SQL（必备）
详见武沛齐博客：https://www.cnblogs.com/wupeiqi/articles/5729934.html
8、简述触发器、函数、视图、存储过程？
9、MySQL索引种类
10、索引在什么情况下遵循最左前缀的规则？
11、主键和外键的区别？
12、MySQL常见的函数？
13、列举 创建索引但是无法命中索引的8种情况。
14、如何开启慢日志查询？
15、数据库导入导出命令（结构+数据）？
16、数据库优化方案？
17、char和varchar的区别？
18、简述MySQL的执行计划？
19、在对name做了唯一索引前提下，简述以下区别： 

select * from tb where name = ‘Oldboy-Wupeiqi’ 
select * from tb where name = ‘Oldboy-Wupeiqi’ limit 1

20、1000w条数据，使用limit offset 分页时，为什么越往后翻越慢？如何解决？
21、什么是索引合并？
22、什么是覆盖索引？
23、简述数据库读写分离？
24、简述数据库分库分表？（水平、垂直）
25、redis和memcached比较？
26、redis中数据库默认是多少个db 及作用？
27、python操作redis的模块？
28、如果redis中的某个列表中的数据量非常大，如果实现循环显示每一个值？
29、redis如何实现主从复制？以及数据同步机制？
30、redis中的sentinel的作用？
31、如何实现redis集群？
32、redis中默认有多少个哈希槽？
33、简述redis的有哪几种持久化策略及比较？
34、列举redis支持的过期策略。
35、MySQL 里有 2000w 数据，redis 中只存 20w 的数据，如何保证 redis 中都是热点数据？ 
36、写代码，基于redis的列表实现 先进先出、后进先出队列、优先级队列。
37、如何基于redis实现消息队列？
38、如何基于redis实现发布和订阅？以及发布订阅和消息队列的区别？
39、什么是codis及作用？
40、什么是twemproxy及作用？
41、写代码实现redis事务操作。
42、redis中的watch的命令的作用？
43、基于redis如何实现商城商品数量计数器？
44、简述redis分布式锁和redlock的实现机制。
45、什么是一致性哈希？Python中是否有相应模块？
46、如何高效的找到redis中所有以oldboy开头的key？

第四部分 前端、框架和其他（155题）

1、谈谈你对http协议的认识。
2、谈谈你对websocket协议的认识。
3、什么是magic string ？
4、如何创建响应式布局？
5、你曾经使用过哪些前端框架？
6、什么是ajax请求？并使用jQuery和XMLHttpRequest对象实现一个ajax请求。
7、如何在前端实现轮训？
8、如何在前端实现长轮训？
9、vuex的作用？
10、vue中的路由的拦截器的作用？
11、axios的作用？
12、列举vue的常见指令。
13、简述jsonp及实现原理？
14、是什么cors ？
15、列举Http请求中常见的请求方式？
16、列举Http请求中的状态码？
17、列举Http请求中常见的请求头？
18、看图写结果：


19、看图写结果：


20、看图写结果：


21、看图写结果：


 

22、看图写结果：


23、看图写结果：


24、django、flask、tornado框架的比较？
25、什么是wsgi？
26、django请求的生命周期？
27、列举django的内置组件？
28、列举django中间件的5个方法？以及django中间件的应用场景？
29、简述什么是FBV和CBV？
30、django的request对象是在什么时候创建的？
31、如何给CBV的程序添加装饰器？
32、列举django orm 中所有的方法（QuerySet对象的所有方法）
33、only和defer的区别？
34、select_related和prefetch_related的区别？
35、filter和exclude的区别？
36、列举django orm中三种能写sql语句的方法。
37、django orm 中如何设置读写分离？
38、F和Q的作用?
39、values和values_list的区别？
40、如何使用django orm批量创建数据？
41、django的Form和ModeForm的作用？
42、django的Form组件中，如果字段中包含choices参数，请使用两种方式实现数据源实时更新。
43、django的Model中的ForeignKey字段中的on_delete参数有什么作用？
44、django中csrf的实现机制？
45、django如何实现websocket？
46、基于django使用ajax发送post请求时，都可以使用哪种方法携带csrf token？
47、django中如何实现orm表中添加数据时创建一条日志记录。
48、django缓存如何设置？
49、django的缓存能使用redis吗？如果可以的话，如何配置？
50、django路由系统中name的作用？
51、django的模板中filter和simple_tag的区别？
52、django-debug-toolbar的作用？
53、django中如何实现单元测试？
54、解释orm中 db first 和 code first的含义？
55、django中如何根据数据库表生成model中的类？
56、使用orm和原生sql的优缺点？
57、简述MVC和MTV
58、django的contenttype组件的作用？
59、谈谈你对restfull 规范的认识？
60、接口的幂等性是什么意思？
61、什么是RPC？
62、Http和Https的区别？
63、为什么要使用django rest framework框架？
64、django rest framework框架中都有那些组件？
65、django rest framework框架中的视图都可以继承哪些类？
66、简述 django rest framework框架的认证流程。
67、django rest framework如何实现的用户访问频率控制？
68、Flask框架的优势？
69、Flask框架依赖组件？
70、Flask蓝图的作用？
71、列举使用过的Flask第三方组件？
72、简述Flask上下文管理流程?
73、Flask中的g的作用？
74、Flask中上下文管理主要涉及到了那些相关的类？并描述类主要作用？
75、为什么要Flask把Local对象中的的值stack 维护成一个列表？
76、Flask中多app应用是怎么完成？
77、在Flask中实现WebSocket需要什么组件？
78、wtforms组件的作用？
79、Flask框架默认session处理机制？
80、解释Flask框架中的Local对象和threading.local对象的区别？
81、Flask中 blinker 是什么？
82、SQLAlchemy中的 session和scoped_session 的区别？
83、SQLAlchemy如何执行原生SQL？
84、ORM的实现原理？
85、DBUtils模块的作用？
86、以下SQLAlchemy的字段是否正确？如果不正确请更正：

from datetime import datetime
from sqlalchemy.ext.declarative
import declarative_base
from sqlalchemy import Column, Integer, String, DateTime

Base = declarative_base()
class UserInfo(Base):
    __tablename__ = 'userinfo'
    id = Column(Integer, primary_key=True, autoincrement=True)
    name = Column(String(64), unique=True)
    ctime = Column(DateTime, default=datetime.now())

87、SQLAchemy中如何为表设置引擎和字符编码？
88、SQLAchemy中如何设置联合唯一索引？
89、简述Tornado框架的特点。
90、简述Tornado框架中Future对象的作用？
91、Tornado框架中如何编写WebSocket程序？
92、Tornado中静态文件是如何处理的？如： <link href="{{static_url("commons.css")}}" rel="stylesheet" />
93、Tornado操作MySQL使用的模块？
94、Tornado操作redis使用的模块？
95、简述Tornado框架的适用场景？
96、git常见命令作用：
97、简述以下git中stash命令作用以及相关其他命令。
98、git 中 merge 和 rebase命令 的区别。
99、公司如何基于git做的协同开发？
100、如何基于git实现代码review？
101、git如何实现v1.0 、v2.0 等版本的管理？
102、什么是gitlab？
103、github和gitlab的区别？
104、如何为github上牛逼的开源项目贡献代码？
105、git中 .gitignore文件的作用?
106、什么是敏捷开发？
107、简述 jenkins 工具的作用?
108、公司如何实现代码发布？
109、简述 RabbitMQ、Kafka、ZeroMQ的区别？
110、RabbitMQ如何在消费者获取任务后未处理完前就挂掉时，保证数据不丢失？
111、RabbitMQ如何对消息做持久化？
112、RabbitMQ如何控制消息被消费的顺序？
113、以下RabbitMQ的exchange type分别代表什么意思？如：fanout、direct、topic。
114、简述 celery 是什么以及应用场景？
115、简述celery运行机制。
116、celery如何实现定时任务？
117、简述 celery多任务结构目录？
118、celery中装饰器 @app.task 和 @shared_task的区别？
119、简述 requests模块的作用及基本使用？
120、简述 beautifulsoup模块的作用及基本使用？
121、简述 seleninu模块的作用及基本使用?
122、scrapy框架中各组件的工作流程？
123、在scrapy框架中如何设置代理（两种方法）？
124、scrapy框架中如何实现大文件的下载？
125、scrapy中如何实现限速？
126、scrapy中如何实现暂定爬虫？
127、scrapy中如何进行自定制命令？
128、scrapy中如何实现的记录爬虫的深度？
129、scrapy中的pipelines工作原理？
130、scrapy的pipelines如何丢弃一个item对象？
131、简述scrapy中爬虫中间件和下载中间件的作用？
132、scrapy-redis组件的作用？
133、scrapy-redis组件中如何实现的任务的去重？
134、scrapy-redis的调度器如何实现任务的深度优先和广度优先？
135、简述 vitualenv 及应用场景?
136、简述 pipreqs 及应用场景？
137、在Python中使用过什么代码检查工具？
138、简述 saltstack、ansible、fabric、puppet工具的作用？
139、B Tree和B+ Tree的区别？
140、请列举常见排序并通过代码实现任意三种。
141、请列举常见查找并通过代码实现任意三种。
142、请列举你熟悉的设计模式？
143、有没有刷过leetcode？
144、列举熟悉的的Linux命令。
145、公司线上服务器是什么系统？
146、解释 PV、UV 的含义？
147、解释 QPS的含义？
148、uwsgi和wsgi的区别？
149、supervisor的作用？
150、什么是反向代理？
151、简述SSH的整个过程。
152、有问题都去那些找解决方案？
153、是否有关注什么技术类的公众号？
154、最近在研究什么新技术？
155、是否了解过领域驱动模型？
