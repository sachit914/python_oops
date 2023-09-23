# python_oops

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

+---------------------+                +---------------------+
|    Object: sbi      |                |    Object: hdfc     |
|    Class: Atm       |                |    Class: Atm       |
+---------------------+                +---------------------+
| pin: "1234"         |                | pin: "12345"        |
| balance: 30         |                | balance: 0          |
+---------------------+                +---------------------+


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
