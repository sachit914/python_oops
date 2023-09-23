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

cust=Customer("nitsh")
greet(cust)
```

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
