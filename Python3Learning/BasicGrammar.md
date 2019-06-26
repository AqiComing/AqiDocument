1.0 基本语法：
#1.1 多行语句
#Python通常一行写完一条语句，但是如果语句很长，我们可以用（\）来实现多行语句
total=item_one+\
	item_two+\
	item_three、

2.数据类型

标准的数据类型有六个：Number、String、List、Tuple、Set、Dictionary
不可变数据（3 个）：Number（数字）、String（字符串）、Tuple（元组）；(不可变是指当该数据类型的对应变量的值发生了改变，那么它对应的内存地址也会发生改变)

#Type和Instance区别
type()不会认为字类是一种父类类型，
isinsitance()会认为子类实例就是一种父类

#2.1 Number 数字类型
Python中有四种数字类型，int,bool,float,complex
python3取消了2中的long类型，统一用int
bool (布尔), 如 True。
complex (复数), 如 1 + 2j、 1.1 + 2.2j

#1、Python可以同时为多个变量赋值，如a, b = 1, 2。
#2、数值的除法包含两个运算，/返回一个浮点型，//返回一个整数(舍弃小数部分)
#3、在混合计算时，Python会把整型转换成为浮点数。


#2.2 字符串（string）
#2.2.1 反斜杠用来转义，但是r可以让反斜杠不发生转义，
如 r"this is a line with \n" 则\n会显示，并不是换行

#2.2.2 向一个索引位置赋值，比如word[0] = 'm'会导致错误。

#2.2.3 * 重复输出字符串 a*2 
a='hello' a*2='hellohello'

#2.2.4 字符串格式化 
print ("我叫 %s 今年 %d 岁!" % ('小明', 10))
	%s 格式化字符串
	%d 格式化整数

#Python 三引号
python三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符
para_str = """这是一个多行字符串的实例
多行字符串可以使用制表符
TAB ( \t )。
也可以使用换行符 [ \n ]。
"""
print (para_str)

#三引号可以很方便的使用HTML和SQL语句

#3 列表
列表是写在方括号 [] 之间、用逗号分隔开的元素列表,列表的元素是可以修改的。

#我们可以通过索引和切片操作列表
#Demo 反转字符串
#input: 你好，中国 return 中国，你好 
def reverseWords(input):
    inputWords=input.split(',')
	# inputWords[-1::-1] 有三个参数
    # 第一个参数 -1 表示最后一个元素
    # 第二个参数为空，表示移动到列表末尾
    # 第三个参数为步长，-1 表示逆向
    inputWords=inputWords[-1::-1]
	#重组字符串
    outputWords=','.join(inputWords)
    return outputWords

#元组
元组（tuple）与列表类似，不同之处在于元组的元素不能修改。元组写在小括号 () 里，元素之间用逗号隔开。

#1 与字符串一样，元组的元素不能修改。但是可以对元组进行连接，如：
tup1 = (12, 34.56);
tup2 = ('abc', 'xyz')
tup3 = tup1 + tup2;

#2 创建空元组 
tup1=()
# 元组只包含一个元素，需要再元素后面添加逗号，否则（）会被当做运算符
tupq=(50,)

#3 删除元组
元组的元素是不允许删除的，但是我们可以使用del语句来删除整个元组
tup = ('Google', 'Runoob', 1997, 2000)
del tup;

#元组的运算
#复制：
('Hi!',) * 4  -->('Hi!', 'Hi!', 'Hi!', 'Hi!')
#元素是否存在
3 in (1, 2, 3)-->Ture

#字典
字典是另一种可变容器模型，且可存储任意类型对象。
字典的每个键值(key=>value)对用冒号(:)分割，每个对之间用逗号(,)分割，整个字典包括在花括号({})中 ,格式如下所示：
键必须是唯一的，且必须是不可变的，如字符串，数字，元组。
#字典中的key '1'和1 为两个不同key
confusion[1] = 1
confusion['1'] = 2

#1 修改字典
dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
dict['Age'] = 8               # 更新 Age
dict['School'] = "菜鸟教程"  # 添加信息

#删除字典元素
del dict['Name'] # 删除键 'Name'
dict.clear()     # 清空字典
del dict         # 删除字典

#集合
集合（set）是一个无序的不重复元素序列，可以使用大括号 { } 或者 set() 函数创建集合，注意：创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。

#运算
a - b  # 集合a中包含而集合b中不包含的元素
a | b  # 集合a或b中包含的所有元素
a & b  # 集合a和b中都包含了的元素
a ^ b  # 不同时包含于a和b的元素

#集合的基本操作
#添加元素
s.add(x)
s.update( x )
thisset.update({1,3})

#移除元素
s.remove(x)