# python-notes
一点区别重点小笔记
一、
1.语法基础

(1)赋值

链式赋值

pi=PI=3.14159

多重赋值

x,y=y,x(元组）



2.数据类型


（1）复数型：
用j表示虚部

分离复数实部和虚部

-复数.real

-复数.image


复数的共轭

-复数.conjugate


（2）字符串表示：
单引号
双引号
三引号（三个单引号）：可以用来表示多行字符串

mystring='Hello world'

则mystring[1]就表示为e


“+”可以连接字符串



（3）映射类型：

用大括号{}界别



3.算术运算

（1）特殊符号

乘方用**（幂运算）

整除用//

（2）比较运算

可以写成3<4<7先计算3<4在计算4<7

(3)逻辑运算符

not and or


4.函数

（1）内建函数

取绝对值函数abs（） 四舍五入函数round（）

（2）非内建函数 

import 模块1，模块2（导入所有函数）

from 模块 import 模块属性（导入部分函数或类）

import 包名.子包名.模块名（使用的时候就是AAA.CCC.c1.func(1)

from 包名.子包名.模块名 import func1(使用的时候就是func（1）



二、

1.条件

（1）if语句

if expression：

    expr_true_suite
    
 elif expression2:
 
    expr2_true_suite
    
 else:
 
    none_of_the_above_suite
    
  
2.range()函数

range（start，end，step=1）

range（start，end）缺省step为1）

range（end）缺省start值为0，step为1

（start为起始值（包含），end为终值（不包含），step步长（不能为0）

>>>list(range(3,11,2))

>>>[3,5,7,9]

python 2中的range（）返回列表 ，生成真实列表

python 3中range（）与python 2中xrange（）相似 返回生成器（generator） 用多少生成多少


3.循环

（1）for循环

for iter_var in iterable_object:

    suite_to_repeat
    
iterable_object: string,list,tuple,dictionary,file

（2）else在各个循环都可以用（while 也可以）

##循环中的else##

-如果循环代码从break处终止，跳出循环

-正常结束循环，则质心else中代码


4.自定义函数

def function_name([arguments]):

    'optional documentation string'//DocString文档字符串函数注释，如果要查看函数DocString 则pring（funct.__doc__)
    
    function_suite
    
    
(1)关键字参数：通过使用参数名区分参数，允许改变参数列表中的参数顺序。

>>>def f（x,y):

    '''x and y both correct words or not'''
    
    if y:
    
    print(x,'and y both correct')
    
    print(x,'is OK')
    
>>>f(68,False)

68 is OK

>>>f(y=False,x=68)

68 is OK

>>>f(y=False,68)

SyntaxError:non-keyword arg after keyword arg//非关键字参数跟在了关键字参数后面

>>>f(x=68,False)

SyntaxError:non-keyword arg after keyword arg//一旦使用关键字参数，后面必须跟关键字参数


（2）传递函数:把函数名当作参数传递给另一个函数

>>>def addMe2Me(x):

    return (x+x)
    
>>>def self(f,y):

    print(f(y))
    
>>>self(addMe2Me,2.2)

4.4


(3)lambda函数（匿名函数）

>>>r=lambda x:x+x

>>>r(5)

10


5.变量作用域

（1）global语句

>>>def f(x):

    global a//global语句强调全局变量
    
    print(a)
    
    a=5
    
    print(a+x)
    
a=3

f(8)

print（a)

3 13 5


6.常用标准库函数

>>>import math

>>>dir(math)//可以查看math库里面的函数

>>>help(math.ceil)//可以查看函数功能及用法

math.ceil//向上取整

math.floor//向下取整

math.degrees//将弧度转角度

math.radians//将角度转弧度


>>>import os

>>>os.getcwd()//获得当前工作目录

'C:\\users\\a'

>>>path='C:\\test'

>>>os.chdir(path)//目录可以修改

'C:\\test'

>>>os.rename('test.txt','test1.txt')//修改文件名字

>>>os.remove('test1.txt')//删除文件


>>>import random

>>>random.choice(['c++','python','java'])//可以从序列或许随机值

'java'

>>>random.randint(1,100)//生成1到100的随机整数

74

>>>random.ranrange(0,10,2)//从range生成的数字获取随机数字

8

>>>random.random()//生成从0到1的随机浮点数，包含0但是不包含1.0

>>>random.uniform(5,10)//生成从5到10的随即浮点数

>>>random.sample(range(100),10)//从集合里随机获取十个值

>>>nums=[1001,1002,1003,1004,1005]

>>>random.shuffle(nums)//将列表数据打乱



>>>import datetime

>>>from datetime import date

>>>date.today()

datetime.date(2018,7,29)

>>>from datetime inport time

>>>tm=time(23,20,35)

>>>print(tm)

23:20:35


7.异常

（1）try-except语句

try:

    raise
    
except exception as err:

    print(err)
    
或者空except子句和as捕捉所有异常

try:

    raise
    
except:

    print('something went wrong')
    
如果加上finally语句，不管是否发生异常，finally子句中的语句块都要被执行


（2）上下文管理器（Context manager）和with语句：定义和控制代码块执行前的准备动作和执行后的收尾动作

with open('file.txt') as f:

    for line in f:
    
        print(line,end='')
        
    
三、数据获取



1.本地数据获取



（1)文件打开

file_obj=open(filename,mode='r',buffering=-1...)//文件名，读写模式，是否要缓冲

mode默认值为r（读文件），也有w（写文件，清空或者新建）和a（文件尾部追加），

r+以读写模式打开，w+以读写模式打开（清空原内容），a+以读和追加模式打开

后面加b表示二进制文件读写和追加 例如rb rb+

buffering默认值为-1（0代表不缓冲，1或大于1的值表示缓冲一行或指定缓冲区大小）

二进制文件可以不使用缓冲，文本文件一定要使用缓冲


（2）写文件

>>>f=open('firstpro.txt','w')

>>>f.write('Hello,World!)

>>>f.close()//不推荐用法，推荐下面这个

>>>with open('firstpro.txt','w')as f:

        f.write('Hello, World!')//推荐用法，可进行文件异常处理，更简洁有效
        
        
（3）读文件

file_obj.read(size)//从文件中至多读出size字节数据，返回一个字符串

file_obj.read()//读文件直到文件结束，返回一个字符串

>>>with open('firstpro.txt','w')as f:

        p1=f.read(5)
        
        p2=f.read()
        
>>>p1

'Hello'

>>>p2

' World!'


(4)其他读写函数

file_obj.readlines()//读取多行数据，返回结果是一个列表，不删除换行符

file_obj.readline()//读取一行数据

file_obj.readlines()//写入多行数据，没有readline函数


（5）其他文件相关函数

file_obk.seek(offset,whence=0)//在文件中移动文件指针，从whence（0表示文件头部，1表示当前位置，2表示文件尾部）偏移offset个字节


（6）标准文件

stdin标准输入

stdout标准输出

stderr标准错误


2.网络数据获取


·抓取

    ·urlib内建模块
    
        -urlib.request
        
    ·Request第三方库
    
    ·Scrapy框架
    
·解析

    BeautifulSoup库
    
    re模块
    
    
（1）request库

官网：http://www.python-requests.org/

方法：request.get()//请求获取指定URL位置的资源，对应HTTP协议的GET方法


抓取网站前要看是否有爬虫协议在网站后面加robots.txt 有的话表示他有爬虫协议 例https://www.douban.com/robots.txt


>>> r = requests.get('https://api.github.com/user', auth=('user', 'pass'))

>>> r.status_code//查看状态码

200//正常

>>> r.headers['content-type']

'application/json; charset=utf8'

>>> r.encoding

'utf-8'

>>> r.text

u'{"type":"User"...'

>>> r.json()

{u'private_gists': 419, u'total_private_repos': 77, ...}

re.json()//假设某个网页格式是json格式，可以利用request库中内质json解码器解码

re.content()//假设内容是二进制 

re.text//自动推测文本编码并进行解码

re.encoding//修改文本编码，常用'utf-8'


(3）网页数据解析


BeautifulSoup是一个可以从HTML或XML文件中提取数据的Python库

官方网站：https://www.crummy.com/software/BeautifulSoup/bs4/doc/


from bs4 import BeautifulSoup


markup='<p class="titlt"><b>The Little Prince</b></p>'


soup=Beautifulsoup(markup,"lxml")


BeautigulSoup对象有四种：Tag（HTML或者XML文档中的标签像<b>）
    
    NavigableString（Tag当中的字符串，就像The Little Prince）
    
    BeautifulSoup（大部分都是，可以把它当作tag对象)
    
    Comment（ NavigableString的一个子类）
    
soup.b

Out[5]: <b>The Little Prince</b>//任何b标签内容都可以通过BeautifulSoup.Tag形式访问得到

type(soup.b)

Out[6]: bs4.element.Tag//可以看一下他的类型，就是Tag

tag=soup.p

tag.name

Out[8]: 'p'//Tag最重要属性name和Attribute，每个Tag通过name属性可以获得自己的名字

 tag.attrs
 
Out[9]: {'class': ['titlt']}//一个Tag可能包含多个属性，获取属性法一

tag['class']

Out[10]: ['titlt']//获取属性法二

tag.string

Out[11]: 'The Little Prince'//NavigableString对象用string属性来表示

type(tag.string)

Out[12]: bs4.element.NavigableString

BeautifulSoup还有一个最常用方法

soup.find_all('b')//可以寻找到所有b标签的内容，如果只需要找第一个标签内容，可以使用find（）方法

Out[13]: [<b>The Little Prince</b>]


import requests

from bs4 import BeautifulSoup

r=requests.get('https://book.douban.com/subject/26986954/')

soup=BeautifulSoup(r.text,'lxml')

pattern=soup.find_all('p','comment_content')

for item in pattern:

    print(item.string)
    


re正则表达式模块进行各类正则表达式处理

参考网站：https：//docs.python.org/3.5/library/re.html

正则表达式：通常是用来检索替换符合某个规则或者是模块的文本，

比如0到9表示取其中的一个数字，.表示除了换行符以外的任意字符，*表示重复0次或多次，加括号表示分组


假设我们要寻找的是前面一个字符串加上后面的一个字符串中间的某一个字符串，就可以把它用（.*?)来表示

import requests

from bs4 import BeautifulSoup

import re

sum=0

r=requests.get('https://book.douban.com/subject/26986954/')

soup=BeautifulSoup(r.text,'lxml')

pattern=soup.find_all('p','comment_content')

for item in pattern:

    print(item.string)
    
pattern_s=re.compile('span class="user-stars allstar(.*?)rating"')

p=re.findall(pattern_s,r.text)

for star in p:

    sum+=int(star)
    
print(sum)


3.序列

aStr='Hello, World!'//字符串

sList=['Hello,','World!']//列表

aTuple=('Sunday','happy')//元组

pList=[('AXP','American','78.52'),('BA','Japan','184.76'),('CVX','Cambodia','33.71)]//由元组构成的列表


序列对象可以迭代，索引从0到N-1或者从-N到-1，一次可以访问一个或多个元素，也叫切片。


（1）序列类型运算符

x in s

x not in s

s+t

s*n,n*s

s[i]

s[i:j]

s[i:j:k]


>>>week=['Mon','Tue','Wed','Thu','Fri','Sat','Sun']

>>>print(week[1],'\n',week[-2],'\n',week[1:4],'\n',week[:6],'\n',week[::-1])

Tue

Sat

['Tue','Wed','Thu']//索引从1开始，4-1=3个元素

['Mon','Tue','Wed','Thu','Fri','Sat']//从头开始六个元素

['Sun','Sat','Fri','Thu','Wed','Tue','Mon']//逆序

>>>'apple'*3

'appleappleapple'

>>>'pine'+'apple'//+连接

'pineapple'

>>>'BA'in('BA','THe BOEIng Company','122.64')//in和not in可以用来判断某个对象是否包含在它其后的某个序列当中

True


(2)序列类型转换内建函数


list（）//可以把一个字符串转成一个列表

tuple（）//可以把一个字符串转成一个元组

str（）//把一个列表或者元组转成字符串


>>>list('Hello, World!')

['H','e','l','l','o',',',' ','W','o','r','l','d','!']]

>>>tuple('Hello, World!')

('H','e','l','l','o',',',' ','W','o','r','l','d','!')


(3)序列类型其他常用内建函数

enumerate（）//返回一个enumerate对象，元素是由元素的索引和值构成的一个个元组，类似于(0,'a'),(1,'b')

len（）//求字符串长度

max（）//求最大值

min（）//求最小值

reversed()//逆序

sorted()//排序

sum()//求和

zip()//由一系列可迭代的对象作为参数，返回一个zip对象，把对象对应的元素打包成一个个元组



4.字符串

(1)

可以用单引号''、双引号""、三引号（可以换行)''''''表示字符串

r""原始字符串，可以用来表示类似像文件路径等包含特殊富豪的字符串

>>>s1="I'm a student"

>>>s1

I'm a student

>>>s2='''hello

world'''

>>>s2

'hello\nworld'//三引号可以让字符串保持原貌

>>>s3=r'd:\Python\test.py'

>>>s3

'd:\Python\test.py'


(2)输出形式

format_string.format(arguments_to_convert)//format函数

print（'There are {0:d}punctuation marks.'.format(count))//大括号是替换后面的参数的占位符，数字表示参数对应的序号，冒号后面是格式说明符


类型说明符
b 二进制，以2为基数输出数字

o 八进制，以8为基数输出数字

x 十六进制，以16为基数输出数字，9以上的数字用小写字母（类型符为X使用大写字母）表示

c 字符，将整数转换成对应的unicode字符输出

d 十进制整数，以10为基数输出数字

f 浮点数，以浮点数输出数字

e 指数记法，以科学记数法输出数字，用e（类型是E时用大写E）表示幂


其他常用格式说明符

+m.nf 输出带符号（若正整数输出“++号）的数，保留n位小数，整个输出占m列（若实际宽度超过m则突破m的限制）

<     左对齐，默认用空格填充右边

0>5d  右对齐，用0填充左边，宽度为5

^     居中对齐

{{}}  输出一个{}


>>>age,height = 21,1.758

>>>print("Age:{0:5d},Height:{1:5.2f}".format(age,height))

Age:21   ,Height: 1.76//21右边用3个空格符填充，1.76保留两位小数，一个空格填充加1.76则站五列。



（3）字符串常用方法

split（） replace（） join（）encode（） decode（）



5.列表

可扩展的容器对象

包含不同类型对象

(1)重要函数

list.sort() //排序或者a=sorted(list)（sorted函数没有改变原本列表，只是生成列表副本）

list.pop()//弹出最后一个值,如果加上参数，就是弹出参数代表的索引代表值

list.append(x)//把x加入列表

list1.extend(list2)//可以把两个列表合并


（2)列表解析

[expression for expr in sequence1

            for expr2 in sequence2...
            
            foe exprN in sequenceN
            
            if condition]
            
两种语法

1、不带if条件，首先迭代sequence里面的所有内容，每一次迭代都把sequence里面的内容放到前面的对象里面去，然后再在表达式里面应用这样的一个对象，形成一个列表

2、加入判断语句，只有满足条件的内容，才把sequence里面的相应内容放到这个对象里面去，再在表达式里面应用这样的一个对象，形成一个列表。

例：

>>>[x for x in range(10)]

[0,1,2,3,4,5,6,7,8,9]

>>>[x ** 2 for x in range(10)]

[0,1,4,9,16,25,36,49,64,81]

>>>[x ** 2 for x in range(10) if x ** 2<50]

[0,1,4,9,16,25,36,49]

>>>[(x+1,y+1) for x in range(2) for y in range (2)]

[(1,1),(1,2),(2,1),(2,2)]


6.元组（元素不可以改变）

>>>2014

2014//创建一个只有一个元素的元组是不存在的

>>>2014,

(2014,)//可以加一个逗号


（1）元组的作用

1、在映射类型中当作键使用


2、函数的特殊类型参数

    通过元组充当可变长的函数参数
    
例：

>>>def foo(args1,*argst):

        print(args1)
        
        print(argst)
        
>>>foo('Hello,','Wangdachui','Niuyun','Linling')

Hello,

('Wangdachui','Niuyun','Linling')


3、函数的特殊返回值

返回对象个数  返回类型

0            None

1            object

>1           tuple

例：

>>>def foo():

        return 1,2,3
        
>>>foo()

(1,2,3)



四、强大的数据结构和Python扩展库

1.字典-一种映射类型//通过键来确定成员

-键（key），可以是数字，字符串或者元组等等一些不可变的类型

-值（value），值无序，仅与key有关

-key-value对


（1）创建字典

-直接使用{}

>>>ainfo={'Wang':3000,'Nie':2000,'Chen':9000}

-利用dict函数//只要存在对应关系，就可以形成映射对

>>>info=[('Wang',3000),('Niu',2000),('Chen',9000)]

>>>binfo=dict(info)

>>>cinfo=dict([['Wang',3000],['Niu',2000],['Ling',9000]])

>>>dinfo=dict(Wang=3000,Niu=2000,Ling=9000)


fromkeys（）赋值所有，第一个参数为序列，第二个参数为不可变类型

>>>adict={}.fromkeys(('Wang','Niu',;Ling),3000)//用fromkeys（）将3000赋值给所有keys

（2）生成字典

通过zip（）将两个列表对应起来


2.字典的使用

（1)字典的基本操作

>>>ainfo['Wang']//键值查找

3000

>>>ainfo['Ling']=8000//更新

>>>ainfo

{'Wang':3000,'Niu':2000,'Ling':8000}

>>>ainfo['Huang']=1000//添加

>>>ainfo

{'Wang':3000,'Niu':2000,'Ling':8000,'Huang':1000}

>>>'Niu' in ainfo//成员判断

>>>False

>>>del ainfo['Huang']//删除字典成员

>>>ainfo

{'Wang':3000,'Niu':2000,'Ling':8000}


(2）字典的内建函数

dict（）

len（）

hash（）//判断某一个对象是不是可哈希的，即可不可变，可哈希则出现哈希值


（3）字典方法

ainfo.keys()//输出所有键

ainfo.values()//输出所有值

ainfo.items()//遍历所有值

ainfo.update(binfo)///整合两份字典，更改或增加

ainfo.get()//返回指定键的值，不存在则返回默认值，None可以有default设置

#删除字典#

例1：

>>>aStock={'AXP':78.51,'BA':184.76}

>>>bStock=aStock

>>>aStock={}

>>>bStock

{'AXP':78.51,'BA':184.76}

例2：

>>>aStock={'AXP':78.51,'BA':184.76}

>>>bStock=aStock

>>>aStock.clear()

>>>aStock

{}

>>>bStock

{}


（4）字典相关使用小案例

·Json格式

·搜索引擎关键词查询

>>>import requests

>>>kw={'q':'Python dict'}

>>>r=requests.get('http://cn.bing.com/search',params=kw)

>>>r.url

>>>print(r.text)


(5)可变长关键字参数//用**表示

>>>def func(args1,*argst,**arged):

        print(arge1)
        
        print(argst)
        
        print(argsd)
        
>>>func('Hello,','Wang','Niu','Ling',a1=1,a2=2,a3=3)

Hello,

('Wang','Niu','Ling')

{'a1':1,'a2':2,'a3':3}

