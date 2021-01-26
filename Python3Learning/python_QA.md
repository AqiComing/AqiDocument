# list 特性
1. list追加 append() 在列表中追加一个元素，将追加的内容放入 方法无返回
listA=[1,2,3,4,5]
listB=[2,3,4,5,6,6]
listA.append(listB) 
print(listA)-->> [1,2,3,4,5,[2,3,4,5,6,6]]

2. list 并入 extend 方法无返回
listA=[1,2,3,4,5]
listB=[2,3,4,5,6,6]
listA.extend(b)
print(listA)-->>[1,2,3,4,5,2,3,4,5,6,6]

3. 合并 +
并入等同于 listA=listA+listB  '+'同样适用于tuple

# tuple



# 字典
  1. dict的初始化方式
    1. dict可以接受一个每个元素为tuple类型的tuple
        b=dict((('test','test'),('hello','hello')))
        print(b) 
        -->{'test': 'test', 'hello': 'hello'}

  2. 删除键值对 del

      test={"name":"zhao","age":23}
      del test['name']
      print(test)

  3. 合并字典 update
      如果test中包含和gender中一样的键，则更新它的值

      test={"name":"zhao","age":23}
      gender={"gender":1}
      test.update(gender)
      print(test)

  4. dict.items  以列表返回可遍历的(键, 值) 元组数组
    HE={"test":1,"hello":2,"jack":3}
    HE.items--> [('test', 1), ('hello', 2), ('jack', 3)]

    1. 按照值排序
    HE={"test":1,"hello":2,"jack":3}
    hello=sorted(HE.items(),key=lambda x:x[1])
    print(dict(hello))
  
  5. 字典推导式
    dic={x:random.randint(1,8) for x in ['a','b','c','d']}



# set 特性
 class set([iterable--可迭代对象]) 创建一个无序不重复的元素集，可进行关系测试，删除重复数据，计算‘交’、‘差’、‘并’集
  1. 创建空的集合，必须用set函数,
      a=set()
  

    x=set('hello')
    y=set('test')
    交集： x&y
    并集： x|y
    差集： x-y  x有而y没有的

# range 特性
1. python3中range() 函数返回的是一个可迭代对象(range对象)，python2是一个list
2. range(x,Y) x必须<y 否则是一个空的可迭代对象
    list(range(1,-1))--> []


# 迭代器与生成器
迭代器：可以记住遍历位置的对象，list tuple都是迭代器，使用next iter方法进行迭代
生成器：使用了 yield 的函数被成为生成器，生成器是一个返回迭代器的函数，遇到yeild就会返回







    