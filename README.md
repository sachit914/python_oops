# python_oops

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
