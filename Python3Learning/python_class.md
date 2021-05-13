# python class

class Person:




# python class __new__与__init__

1. __init__ 是初始化方法/构造函数，有一个参数self,来查看__new__返回对象是否是类的对象，如果是，传进来 实现实例化
2. __new__ 必须有返回值，返回实例化出来的实例（未初始化的状态），cls
