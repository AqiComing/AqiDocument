# list 特性
1. 

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





    