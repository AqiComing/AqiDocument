# sort() 是list的内置函数 sorted是python的内置函数
1. sort()只排序，不返回 sorted返回一个新的可迭代对象

# reduce() 对一个可迭代对象进行带入方法，将前两个元素的结果与第三个元素进行计执行
    listA=[1.2.....]
    reduce(lambda x,y:x+y,listA)


# map() 对一个可迭代对象中的元素依次代入方法，然后并返回执行结果的迭代器
    listB=[2,58,2.....]
    map(lambda x:x*x,listB)

# filter() 将一个可迭代对象的元素依次带入函数中，然后让函数进行判断，判断结果为true的元素被返回，放入迭代器中被返回
    listC=[1,2,3,4,5,6,7]
    result=filter(lambda x:x%2==1,listC)
    [x for x in result]===>[1,3,5,7]


# slice() 切片 需要带入到tuple或者列表中使用
    a=(1,2,3,4,5,6,4,3)
    a[2:6:2]<==>a[slice(2,6,2)]

# join() 用于将序列中的元素，用指定额字符串连接成一个新的字符串
    str='--'
    A='hello'
    str.join(A)--> 'h--e--l--l--o' 注意用法

# is 与 == 
 is 判断是id是否一致， 浅拷贝is返回true  ==判断是值是否相等


    