# python_oops
https://www.youtube.com/watch?v=Mf2RdpEiXjU&t=2111s

<details>
  <summary>basic class creation and object declaration </summary>

```
class Atm:
  def __init__(self):
    self.pin=""
    self.balance=0

    self.menu()

  def menu(self):
    user_input=input("""
    Hello how would you like to proceed?
    1.  Enter 1 to create pin
    2.  Enter 2 to deposit
    3.  Enter 3 to withdraw
    4.  Enter 4 to check balance
    5.  Enter 5 to exit
    """)

    if user_input=="1":
      self.create_pin()
    elif user_input=="2":
      self.deposite()
    elif user_input=="3":
      self.withdraw()
    elif user_input=="4":
      self.check_balance()
    else:
      print("bye")


  def create_pin(self):
    self.pin=input("enter your pin")
    print("pin created successfully")

  def deposite(self):
    temp=input("enter you pin")
    if temp==self.pin:
      amount=int(input("enter the amount"))
      self.balance=self.balance+amount
      print("Deposit successful")
    else:
      print("invalid pin")

  def withdraw(self):
    temp=input("enter you pin")
    if temp==self.pin:
      amount=int(input("enter the amount"))
      if amount<self.balance:
        self.balance=self.balance-amount
        print("operation successful")
      else:
        print("insufficiant funds")
    else:
      print("invalid pin")

  def check_balance(self):
    temp=input("enter your pin")
    if temp==self.pin:
      print(self.balance)
    else:
      print("invalid pin")


```
## class diagram
```
+----------------------------+
|           Atm              |
+----------------------------+
| - pin: str                 |
| - balance: int             |
+----------------------------+
| + __init__(): None         |
| + menu(): None             |
| + create_pin(): None       |
| + deposite(): None         |
| + withdraw(): None         |
| + check_balance(): None    |
+----------------------------+
```

```
#python shell

from main import Atm

sbi=Atm()                    object1

sbi.deposite()
1234
300000
sbi.check_balance()


hdfc=Atm()                        object2
hdfc.check_balance()

```

## object diagram
```
+---------------------+                +---------------------+
|    Object: sbi      |                |    Object: hdfc     |
|    Class: Atm       |                |    Class: Atm       |
+---------------------+                +---------------------+
| pin: "1234"         |                | pin: "12345"        |
| balance: 30         |                | balance: 0          |
+---------------------+                +---------------------+
```

##note 
the object can acess both method and function of class

</details>


<details>

  <summary>Constructor</summary>

## when to use constructor

constructor are used when you dont want to give specific control to user
eg when app opens automatically constructor are triggred
eg when app opened gps is oned

eg
Database Connection:

Initialize a connection to a database upon creating a new DatabaseConnection instance.
User Profile:

Set default values, such as a profile picture, when creating a new UserProfile.
Music Player:

Load the last played song or a default playlist upon instantiating a MusicPlayer.
Shopping Cart:

Initialize a new ShoppingCart with an empty list of products or offer a welcome gift for first-time users.
GPS Service:

Turn on the GPS automatically when a GPSService instance is created.
  
</details>


<details>
  <summary>self</summary>
  
```
class Demo:
    def __init__(self):
        self.pin=""
        print(id(self))

ob1=Demo()
ob2=Demo()

id(ob1) == self which means ob1 is self
```
  ### note
  id(ob1) == self which means ob1 is self


  ```
class Atm:
  def __init__(self):
    self.pin=""
    self.balance=0

  def create_pin(self):
    self.pin=input("enter your pin")
    print("pin created successfully")

 
```

def create_pin(self)
  self.pin is same as sbi.pin

  
sbi.create_pin() is same like self.create_pin()

self contains sbi object address

class method and variable can be accessed by its object
</details>


<details>
  <summary>encapsulation</summary>

  ```
class Atm:
  def __init__(self):
    self.pin=""
    self.balance=0
```


  ## instance variable :-
  whatever varaible we are creating inside consructor are called instance variable

  the value of instance variable is different for differnt object

  eg in above code ebery object will have separeate pin and balance

  ## note
  the object can acess both variable and function of class

  ```
sbi.balance="eeeewjdsj"
sbi.deposite()

the code will crash because some random string value is set

so its not good pratice to show all variable

so to make the variable private we use __ before a variable


```

```
class Atm:
  def __init__(self):
    self.__pin=""
    self.__balance=0

  def create_pin(self):
    self.__pin=input("enter your pin")
    print("pin created successfully")

```

suppose you junior programmer wants to acess
use getter and setter

```
class Atm:
  def __init__(self):
    self.__pin=""
    self.__balance=0

self.__menu()

def get_pin(self):
  return self.__pin

def set_pin(self)
  if type(new_pin)==str:                //we can validate  value when other programmer sends improper dataType
    self.__pin=new_pin
    print("pin changed")
  else:
    print("not allowed")
```
## what we did above

need for encapsulation

private attributes

getter and setter methods



</details>


<details>

  <summary>Refernce variable  1:50:23 </summary>
  

  created a object     
  
  Atm()                object is created and got a memory location but the location value is not stored in any varuiaable so ites lost


  sbi=Atm()          in this the oblect memory location is stored in sbi variable

  # pass by refrence

  ```
class Customer:
    def __init__(self,name):
        self.name=name

def greet(customer):
    print("Hello",customer.name)
    print(id(customer))

cust=Customer("nitsh")
greet(cust)
print(id(cust))
```

![o1](https://github.com/sachit914/python_oops/assets/137917052/c91ae341-bcaa-408c-b2c9-78a85df384ab)


## can return object

  ```
class Customer:
    def __init__(self,name):
        self.name=name

def greet(customer):
    print("Hello",customer.name)

    cust2=Customer("nitesh")
    return cust2

cust=Customer("Ankita")
new_cust=greet(cust)
print(new_cust.name)
```




  ```
class Customer:
    def __init__(self,name):
        self.name=name

def greet(customer):
    print(id(customer))
    customer.name="Nithesh"
    print(customer.name)                          //prints nithesh

cust=Customer("Ankita")
print(id=(cust))

greet(cust)
print(cust.name)                                 //prints nithesh
```

![o3](https://github.com/sachit914/python_oops/assets/137917052/1971a7af-cff9-482f-93ec-733bc5858673)


# note 

objects of class are mutable like lists ,dict

# collection of objects

```
c1=customer("nithesh",34)
c2=customer("ankita",45)
c3=customer("neha",32)

L=[c1,c2,c3]

for i in L:
  print(i.name)
```

</details>



<details>

  <summary>static   2:16:00 </summary>

# instance variable and static variable 

### instance variable
instance variable are those varible where every object has different value

### note
**instance variable are always inside constructor**

eg pin, balance for atm object

### static or class variable

### note
**class variable are created outside constructor**

static varible are those varible whose value  is same for all objects

eg bank ifsc code 
eg serial no. for customer


```
class Atm:

  # static/class variable
  counter=1

  def __init__(self):
    #instance variable
    self.pin=""
    self.balance=0
    print(id(self))
    self.sno=Atm.counter
    Atm.counter=Atm.counter+1
```

```
class Atm:

  # static/class variable
  counter=1

  def __init__(self):
    #instance variable
    self.pin=""
    self.balance=0
    print(id(self))
    self.sno=Atm.counter
    Atm.counter=Atm.counter+1

    # self.menu()

//staticmethods are  those methods where we can access the methods without creating objects
  @staticmethod                                             
  def get_counter():                                        
    return Atm.counter
```

```
Atm.get_counter()
```

</details>


<details>

  <summary>
    Inhertitance
  </summary>

![o4](https://github.com/sachit914/python_oops/assets/137917052/3353bec5-6d38-4e6b-84a8-3de10c22be96)


# agregration

  ![o5](https://github.com/sachit914/python_oops/assets/137917052/bb82ce9e-2be2-4fc1-9db7-926f3e39d943)

```
class Customer:
    def __init__(self,name,gender,address):
        self.name=name
        self.gender=gender
        self.address=address

    def edit_profile(self,new_name,new_city,new_pin,new_state):
        self.name=new_name
        self.address.change_address(new_city,new_pin,new_state)


class Address:
    def __init__(self,city,pincode,state):
        self.city=city
        self.pincode=pincode
        self.state=state

    def change_address(self,new_city,new_pin,new_state):
        self.city=new_city
        self.pincode=new_pin
        self.state=new_state


add=Address("kolkata",700156,"delhi")
cust=Customer("nithesh","male",add)

cust.edit_profile("jack","gurgaon",122011,"haryana")

print(cust.address.pincode)
print(cust.address.city)
```

# inhertitance

![o6](https://github.com/sachit914/python_oops/assets/137917052/fddfd901-50f2-4e00-8aef-1754a92e4d3a)

suppose we plan of creating class but we see that the class can have function which we can inherit rather than repeating the same code logic

in above class diagram login and registration feature are same so we can basically inherit the functionality rather than re coding the logic

```
class User:
    def login(Self):
        print("Login")

    def register(self):
        print("Register")

class Student(User):
    def enroll(self):
        print("enroll")

    def review(self):
        print("review")

stu1=Student()
stu1.enroll()
stu1.review()
stu1.login()
stu1.register()
```


# inheriting constructor  2:57:16

```
class Phone:
    def __init__(self,price,brand,camera):
        print("Inside phone constructor")
        self.price=price
        self.brand=brand
        self.camera=camera

class SmartPhone(Phone):
    pass

s=SmartPhone(20000,"Apple",13)
print(s.brand)
```

# inheriting Private Members
```
class Phone:
    def __init__(self,price,brand,camera):
        print("Inside phone constructor")
        self.price=price
        self.__brand=brand
        self.camera=camera

class SmartPhone(Phone):
    pass

s=SmartPhone(20000,"Apple",13)
print(s.__brand)
```
we cant access parent call hidden values


# Polymorphism  3:01:02

```
class Phone:
    def __init__(self,price,brand,camera):
        print("Inside phone constructor")
        self.price=price
        self.brand=brand
        self.camera=camera

    def buy(self):
        print("Buying A phone")

class SmartPhone(Phone):
    def buy(self):
        print("Buying a smatphone")                        //this buy function executes(also known as method overriding)


s=SmartPhone(20000,"Apple",13)
s.buy
```
note 

polymorphism has method Overriding 

method Overloading

operator Overloading

```
class Parent:
    def __init__(self,num):
        self.__num=num
    
    def get_num(self):
        return self.__num
    
class Child(Parent):
    def __init__(self,val,num):                                //child constructor is executed first
        self.__val=val
    
    def get_val(self):
        return self.__val
    
son=Child(100,10)
print("Parent: Num",son.get_num())          // we get error because parent constructor is not initialized ,there is no get_nun
```

if child dont have is own constructor then parent constructor is used


# super keyword  3:10:24

we use super keyword to invoke parent method and constructor
 ```
class Phone:
    def __init__(self,price,brand,camera):
        print("Inside phone constructor")
        self.__price=price
        self.brand=brand
        self.camera=camera

    def buy(self):                                                      control comes here          <-----|
        print("Buying a phone")                                                                           |
                                                                                                          |
class SmartPhone(Phone):                                                                                  |
    def buy(self):                                                                                        |
        print("Buying a smartphone")                                                                      |
        super().buy()                       //invoke parent buy method()   after this controll will go to |

s=SmartPhone(200000,"Apple",13)

s.buy()
```

output

Inside phone constructor

Buying a smartphone

Buying a phone


```
class SmartPhone(Phone):                                                                                  
    def buy(self):                                                                                        
        print("Buying a smartphone")                                                                                           
s=SmartPhone(200000,"Apple",13)

s.buy()
s.super().buy()                                       doesnt work
```
note super key word dosent work out of class

by using super key word we can access only parents method and constructor 

we cant access attribute

# invoking parents constructor using super keyword
```

class Phone:
    def __init__(self,price,brand,camera):
        print("Inside Phone Constructor")
        self.__price=price
        self.brand=brand
        self.camera=camera

class SmartPhone(Phone):
    def __init__(self,price,brand,camera,os,ram):
        super().__init__(price,brand,camera)                       //super should be first line 
        self.os=os
        self.ram=ram
        print("Inside smartphone constructor")

s=SmartPhone(20000,"samsung",12,"Android",2)

print(s.os)
print(s.brand)
```

## note imp  3:15:00 
how much child needs to do will be done in child 

remaining will inherit from parent so no need to re code 


## example

```
class Parent:
    def __init__(self):
        self.num=100

class Child(Parent):
    def __init__(self):
        super().__init__()
        self.var=200

    def show(self):
        print(self.num)                 //son.num
        print(self.var)

son=Child()
son.show()
```


</details>

<details>

  <summary>Types of Inheritance  3.22.16</summary>

1 single level :child class can acess parent class elements

2 multi level : child class can access parent class as well as parents parent classs element ,parent class can acess parents parent call values

3 hierarchical : a parent can have multiple child class 

4 multiple a class can have multiple parents

5) hybrid inheritance : is cobination of any inheritance



![24](https://github.com/sachit914/python_oops/assets/137917052/1f63ec50-e43e-44b2-a106-dd6baa3e436c)


![25](https://github.com/sachit914/python_oops/assets/137917052/37a469a4-a022-48f0-a815-b782ba4354f4)


multiple inheirtance is only available in python not in java

```
# multiple

class Phone():
  def __init__(self,price,brand,camera):
    print("inside phone constructor")
    self.__price=price
    self.brand=brand
    self.camera=camera

  def buy(self):
    print("Buying a phone")

class Product:
  def review(Self):
    print("customer review")

class  SmartPhone(Phone,Product):                   first phone constructor is called if phone dont have then product constructor is called
  pass

s=SmartPhone(20000,"apple",12)

s.buy()
s.review()


```

conflict
```
# multiple      mro example
# -------------------------------------------------->which buy method will execute first

class Phone():
  def __init__(self,price,brand,camera):
    print("inside phone constructor")
    self.__price=price
    self.brand=brand
    self.camera=camera

  def buy(self):                   --------------------------->buy method
    print("Buying a phone")

class Product:
  def buy(Self):                       -------------------->buy method
    print("buy")

class  SmartPhone(Phone,Product):         since phone is written first in parameter the buy method in phone executes first           
  pass

s=SmartPhone(20000,"apple",12)

s.buy()
s.review()

```
## note 
in which order we inherit we give priority in same way


</details>


<details>
  <summary>
    method and operator overloading     3:35:41
  </summary>


## in polymorphism we 
1. method overriding
2. method overloading
3. operator overloading

## method overloading 

Method overloading is a programming concept where two or more methods in the same class have the same name but different parameters.

```
class Geometry:
  def area(self,radius):
    return 3.14*radius*radius

  def area(self,l,b):                               method overloading works only on java
    return l*b

obj=Geometry()
print(obj.area(4))


```

## operator overloading

 With operator overloading, you can define how an operator behaves for user-defined data types. For instance, if you've defined a Vector class, you can define the behavior of the + operator to add two vectors together.


</details>



<details>

  <summary>
    Abstract classes and models
  </summary>

  ## abstract class
  - abstract class  is designed to be a blueprint for other classes
    
## abstract methods
  - you can define abstract methods, which do not have a body in the abstract class, but they must be implemented by any concrete
  -  A method that is declared but does not have an implementation in the abstract class. Any subclass inheriting the abstract class must provide an implementation for these methods, or it will also become abstract.

<details>
  <summary>code</summary>
  
  ```
  from abc import ABC, abstractmethod

class Polygon(ABC):

    @abstractmethod
    def area(self):
        """Return the area of the polygon."""
        pass

class Triangle(Polygon):
    
    def __init__(self, base, height):
        self.base = base
        self.height = height

    def area(self):
        """Return the area of the triangle."""
        return 0.5 * self.base * self.height

class Rectangle(Polygon):
    
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        """Return the area of the rectangle."""
        return self.width * self.height

```

</details>
  
</details>
