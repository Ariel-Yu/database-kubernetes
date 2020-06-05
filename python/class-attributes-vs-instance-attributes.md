# Class Attributes vs Instance Attributes

## Class Attributes
- Class attributes belongs to the class and are shared with all the objects of the class
- Class attributes are instantiated **outside \_\_init\_\_**
- When to use class attributes
  - A class attribute can serve as a type. Which means that, a parent class with only attributes but no methods can be transformed into a class attribute of the child class instead
  - Constants
  - Track data of all instances of the class

```  
class People:
  limit = 10
  population = 0

  def __init__(self, name: str):
      if People.population < People.limit:
          self.name = name
          People.population += 1
      else:
          raise ValueError(f"Too many people in the world! {People.population} people already created.")
```

```
People("People1")
People("People2")

print(f"Total people created: {People.population}")
>> Total people created: 2

People("People3")
People("People4")
People("People5")
People("People6")
People("People7")
People("People8")
People("People9")
People("People10")

People("People11")
>>> Traceback (most recent call last):
      File "class/class_attribute.py", line 24, in <module>
        People("Elias11")
      File "class/class_attribute.py", line 10, in __init__
        raise ValueError(f"Too many people in the world! {People.population} people already created.")
    ValueError: Too many people in the world! 10 people have already been created.
```

- Class attributes mutate to instance attributes if they’re immutable ex: string
- Class attributes might or might not mutate to instance attributes if they’re mutable and depends on how you modify the class attributes ex: list

## Instance Attributes
- Instance attributes belongs to one and only one object
- Instance attributes should be instantiated **within \_\_init\_\_**

## References
- good: https://dzone.com/articles/python-class-attributes-vs-instance-attributes
- okay: https://www.toptal.com/python/python-class-attributes-an-overly-thorough-guide
