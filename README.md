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
