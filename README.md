# Python-32-
Python学习笔记(32)
# p112 面向对象的三大特征_封装的实现方式
class Car:
    def__init__(self,brand):
        self.brand=brand
    def start(self):
        print('汽车已启动...')

car=Car('宝马X5')
car.start()
print(car.brand)

#在PYthon中没有专门的修饰符用于属性的私有，如果该属性不希望在类对象外部被访问，前边使用两个"_"
class Student:
    def __init__(self,name,age):
        self.name=name
        self.__age=age  #年龄不希望在类的外部被使用
    def show(self):
        print(self.name,self.__age)

stu=Student('张三'，20)
stu.show()
print(stu.name)
print(stu.__age)  #输出没有这样的属性
print(dir(stu)
print(stu._Student__age)  #在类的外部可以通过_Student__age进行访问



# p113 继承及其实现方式
#继承代码的实现
class Person(object)  #Person子类，object父类  Person继承父类
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def info(self):
        print('姓名:{0},年龄:{1}'.format(self.name,self.age))
#定义子类
class Student(Person):  
    def __init__(self,name,age,score):  #这里调用父类Person中的实例参数
        super().__init__(name,age)
        self.score=score
#测试
stu=Student('Jacl',20,'1001')
stu.info()



# p114 方法重写
class Person(object):
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def info(self):
        print('姓名:{0},年龄:{1}'.format(self.name,self.age))
#定义子类
class Student(Person):
    def __init__(self,name,age,score):
        super().init__(name,age)
        self.score=score
    def info(self):
    super().info()       #调用父类中被重写的方法
    print('学号:{0}'.format(self.score))
#测试
stu=Student('Jack',20,'1001')
stu.info()



# p115 object类
class Student():
    def __init__(self,name,age):
        self.name=name
        self.age=age
    def __str__(self):  #__str__内置函数的作用是重写
        return '我的名字是{0},今年{1}岁'.format(self.name,self.age)
stu=Student('张三',20)
print(dir(stu))  #内置函数dir()可以查看一个类的所有属性
print(stu)



# p116 多态的实现
class Animal(object):
    def eat(self):
        print('动物会吃')
class Dog(Animal):
    def eat(self):
        print('狗吃骨头')
class Cat(Animal):
    def eat(self):
        print('猫吃鱼')

class Person:
    def eat(self):
        print('人吃五谷杂粮')

#定义一个函数
def fun(obj):
    obj.eat()

#开始调用函数
fun(Cat())
fun(Dog())
fun(Animal())
print('---------------')
print(Person())  #这里即使不是obj的子类依然可以输出，因为Python是一门动态语言，它只关心你是否定义



# p117 特殊属性
class A:
    pass
class B:
    pass
class C(A,B):
    def __init__(self,name,age):
        self.name=name
        self.age=age
#创建一个C类的对象
x=C('Jack',20)  #X是C类的一个实例对象
print(x.__dict__)  #实例对象的属性字典
print(C.__dict__)
print('-------------------')
print(x.__class__)  #输出了对象所属的类
print(C.__bases__)  #输出C类的父类类型的元素
print(C.__base__)  #哪一个类写在前面输出那个类，也就是基类
print(C.__mro__)  #查看类的层次结构
print(A.__subclasses__())  #查看A类的子类列表
