---
tags:
  - cs/oop
date created: Sat, Mar 2nd 2024, 1:08 pm
date modified: Sun, Nov 3rd 2024, 1:36 am
---

(objected-Oriented Programming)
Object = state + behavior
attribute ↔ variables ↔ obj.my_attribute
method ↔ function() ↔ obj.my_method()

every Numpy array has attributes shape
method like max or resize

dir() list all attributes and methods

Object-oriented programming, as well as procedural programming, are just ways of organizing your code. Many languages allow for use of either style. For example, Python has OOP-based architecture, but you have likely been writing procedural code in it for awhile now!

```python
class Customer:
	pass
# class <name>: starts a class definition
# code inside class is indented
# use pass to create an "empty" class
c1 = Customer()
c2 = Customer() 
# use ClassName() to create an object of class ClassName
```

```python
class Customer:
	# Using a parameter
	def identify(self, name):
		print("I am Customer" + name)

cust = Customer() # call class first
cust.identify("Eris Odoro")		
"I am Customer Eris Odoro" # output



class Customer:
	def set_name(self, new):
		self.name = new # attributes
	
		def identify(self):
			print("I am customer"+self.name) 	
cust = Customer()
cust.set_name("abc")
cust.identify()

"I am customer abc"
```

```python
# Include a set_name method
class Employee:
  
  def set_name(self, new_name):
    self.name = new_name # attributes
  
# Create an object emp of class Employee  
emp = Employee()

# Use set_name() on emp to set the name of emp to 'Korel Rossi'
emp.set_name('Korel Rossi')

# Print the name of emp
print(emp.name)
```

constructor
two way of set attributes:
1. define attributes in method of class
2. define constructor and define all attributes there
	1. try to avoid define attributes elsewhere

Constructor: __init__() method is called every time an object is created.

```python
class Customer:
	def __int__(self,name):
		self.name=name
		print("The __init__method was called")
cust = Customer("abc") # init is implicitly called
print(cust.name)
```

# Inheritance and Polymorphism

![[oop1.png]]
The instance attributes are those parameters except self.
You shouldn't be able to change the data in all the instances of the class through a single instance. Imagine if you could change the time on all the computers in the world by changing the time on your own computer! If you want to change the value of the class attribute at runtime, you need to do it by referring to the class name, not through an instance.

## Alternative  Constructor

use @classmethod decorator

question:
what is decorator?
it is high-order function

## Inheritance

New class functionality = Old class functionality + extra
Child class has all of the  parent data, but parent doesn't have all of the child data
```python
class MyChild(Myparent):
	pass



child1 = child(123)
acct = Myparent(500)

isinstance(child1, child) # True
isinstance(acct,child) # False
isinstance(child1, Myparent)#True
isinstance(acct,Myparent)#True


```

MyChild : class that will inherit the functionality and add more
MyParent : class whose functionality is being extended/inherited
Parent is inherited by child, child inherit from Parent
The purpose of child classes -- or sub-classes, is to customize and extend functionality of the parent class.

## Customizing functionality via inheritance

Customizing constructors
```python
class BankAccount:
	def __init(self,balance):
		self.balance = balance
	def withdraw(self,amount):
		self.balance -=amount
# Empty class inherited from BankAccount
class SavingAccount(BankAccount):
	# Constructor specifically for SavingsAccount with an additional parameter
	def __init__(self,balance, interest_rate):
		# call the parent constructor using ClassName.__init__()
		BankAccount.__init__(self,balance) # <-- self is a Saving Account but also a BankAccount
		# add more functionality
		self.interest_rate=interest_rate
	# New Functionality
	def compute_interest(self,n_periods = 1):
		return self.balance * ( (1 + self.interest_rate) ** n_periods - 1)
	
```
Can run constructor of the parent class first by Parent.__init__(self, args...)
Add more functionality
Don't have to call the parent constructors

![[oop2.png]]
Inheritance is powerful because it allows us to reuse and customize code without rewriting existing code. By calling methods of the parent class within the child class,

```python
class Employee:
    def __init__(self, name, salary=30000):
        self.name = name
        self.salary = salary

    def give_raise(self, amount):
        self.salary += amount

        
class Manager(Employee):
    def display(self):
        print("Manager ", self.name)

    def __init__(self, name, salary=50000, project=None):
        Employee.__init__(self, name, salary)
        self.project = project

    # Add a give_raise method
    def give_raise(self,amount, bonus=1.05):
        Employee.give_raise(self,amount*bonus)
    
    
mngr = Manager("Ashta Dunbar", 78500)
mngr.give_raise(1000)
print(mngr.salary)
mngr.give_raise(2000, bonus=1.03)
print(mngr.salary)

79550.0  -> 78500+1000*1.05
81610.0 ->2000*1.03+79550 
```

Class attributes CAN be inherited, and the value of class attributes CAN be overwritten in the child class.

Class attributes is like global attributes that no need self

## Question

Need more practice to understand the inheritance, and use cs61a as reference

# Operator, overloading: comparison

```python
class Parent:
    def __eq__(self, other):
        print("Parent's __eq__() called")
        return True

class Child(Parent):
    def __eq__(self, other):
        print("Child's __eq__() called")
        return True

p = Parent()
c = Child()

p == c 
"Child's __eq__() called"
True
```
Python always calls the _child's_ `__eq__()` method when comparing a child object to a parent object.

String representation
Printing an object
![[nparry1.png]]
To format a string with variables, you can either use keyword arguments in `.format` (`'Insert {n} here'.format(n=num)`),
refer to them by position index explicitly (like `'Insert {0} here'.format(num)`) or implicitly (like `'Insert {} here'.format(num)`). You can use double quotation marks inside single quotation marks and the way around, but to nest the same set of quotation marks, you need to escape them with a slash like `\"`.

## String representation of objects

There are two special methods in Python that return a string representation of an object. `__str__()` is called when you use `print()` or `str()` on an object,
`__repr__()` is called when you use `repr()` on an object, print the object in the console without calling `print()`, or instead of `__str__()` if `__str__()` is not defined.

`__str__()` is supposed to provide a "user-friendly" output describing an object, and `__repr__()` should return the expression that, when evaluated, will return the same object, ensuring the reproducibility of your code.
```python
class Employee:
    def __init__(self, name, salary=30000):
        self.name, self.salary = name, salary
            
    # Add the __str__() method
    def __str__(self):
        return "Employee name:{0},\nEmployee salary:{1}".format(self.name,self.salary)

emp1 = Employee("Amar Howard", 30000)
print(emp1)
emp2 = Employee("Carolyn Ramirez", 35000)
print(emp2)
# output
Employee name:Amar Howard, 
Employee salary:30000 
Employee name:Carolyn Ramirez, 
Employee salary:35000
```

```python
class Employee:
    def __init__(self, name, salary=30000):
        self.name, self.salary = name, salary
      

    def __str__(self):
        s = "Employee name: {name}\nEmployee salary: {salary}".format(name=self.name, salary=self.salary)      
        return s
      
    # Add the __repr__method  
    def __repr__(self):
        return "Employee('{name}',{salary})".format(name = self.name,salary = self.salary)   

emp1 = Employee("Amar Howard", 30000)
print(repr(emp1))
emp2 = Employee("Carolyn Ramirez", 35000)
print(repr(emp2))

# output
Employee('Amar Howard',30000) 
Employee('Carolyn Ramirez',35000)
```

## Exception

![[nparry2.png]]

## Exception Handling

![[py1.png]]

## Raising Exception

![[py2.png]]

## Customize Exception

![[oop3.png]]
```python
cust = Customer("Larry Torres",-100)
# console output
Traceback (most recent call last):
File "script.py", line 11, in <module>
cust = Customer("Larry Torres",-100)
File "script.py", line 6, in __init__ 
	raise BalanceError("Balance has to be non-negative!")
BalanceError: Balance has to be non-negative!
```

## Catching custom exceptions

```python
try:
	cust = Customer("Larry Torres",-100)
except BalanceError:
	cust = Customer("Larry Torres", 0)
```

```python
# MODIFY the function to catch exceptions
def invert_at_index(x, ind):
    try:
        print(1/x[ind])
        
    except ZeroDivisionError:
        print("Cannot divide by zero!")

    except IndexError:
        print("Index out of range!")
 
a = [5,6,0,7]

# Works okay
print(invert_at_index(a, 1))

# Potential ZeroDivisionError
print(invert_at_index(a, 2))

# Potential IndexError
print(invert_at_index(a, 5))
# output
0.16666666666666666 
None 
Cannot divide by zero! 
None 
Index out of range! 
None
```

```python
class SalaryError(ValueError): pass
class BonusError(SalaryError): pass

class Employee:
  MIN_SALARY = 30000
  MAX_BONUS = 5000

  def __init__(self, name, salary = 30000):
    self.name = name    
    if salary < Employee.MIN_SALARY:
      raise SalaryError("Salary is too low!")      
    self.salary = salary
    
  # Rewrite using exceptions  
  def give_bonus(self, amount):
    if amount > Employee.MAX_BONUS:
       raise BonusError("The bonus amount is too high!")  
        
    elif self.salary + amount <  Employee.MIN_SALARY:
       raise SalaryError("The salary after bonus is too low!")
      
    else:  
      self.salary += amount
```
Notice that if you `raise` an exception inside an `if` statement, you don't need to add an `else` branch to run the rest of the code. Because `raise` terminates the function, the code after `raise` will only be executed if an exception did not occur.

Previously, you defined an `Employee` class with a method `get_bonus()` that raises a `BonusError` and a `SalaryError` depending on parameters. But the `BonusError` exception was inherited from the `SalaryError` exception. How does exception inheritance affect exception handling? -> `except` block for a parent exception will catch child exceptions

```python
# compare 1
emp = Employee("Katze Rik",50000)
try:
  emp.give_bonus(7000)
except SalaryError:
  print("SalaryError caught")
except BonusError:
  print("BonusError caught")
# output
SalaryError caught



# compare 2
emp = Employee("Katze Rik",50000)
try:
  emp.give_bonus(7000)
except BonusError:
  print("BonusError caught")
except SalaryError:
  print("SalaryError caught")
# output
BonusError caught
```
bonusError is inherited from SalaryError
Finding:
It's better to include an `except` block for a child exception before the block for a parent exception, otherwise the child exceptions will be always be caught in the parent block, and the `except` block for the child will never be executed. therefore, those pass parents exception but failed child exception will be showed as parents exception messages, even though child's exception has its own message, because the parents exception catch both child and parent exception, and child will never be executed.
So:
It's better to list the `except` blocks in the increasing order of specificity, i.e. children before parents, otherwise the child exception will be called in the parent `except` block.

To handle exceptions correctly and take advantage of the specificity of child exceptions, you should place the `except` blocks for child exceptions before those for parent exceptions:
```python
try:
    # Some operation that raises a ChildException
    raise ChildException("This is a child exception")
except ChildException:
    print("Caught by child exception handler")
except ParentException:
    print("Caught by parent exception handler")
```

# Designing for inheritance and polymorphism

Polymorphism is Using a unified interface to operate on objects of different classes

LSP(Liskov substitution principle): "Base class should be interchangeable with any of its subclasses without altering any properties of the program"

Syntactically
- function signatures are compatible
	- arguments, returned values: The method in the subclass should have a signature with parameters and return values that are compatible with the method in parents' class
	Semantically
- the state of the object and the program remains consistent
- subclass method doesn't strengthen input conditions
- subclass method doesn't weaken output conditions
- no additional exceptions

## Violating LSP

→ Syntactic incompatibility
- `BankAccount.withdraw()` requires 1 parameter, but `CheckingAccount.withdraw()` requires 2
→ Subclass strengthening input conditions
- `BankAccount.withdraw()` accepts any amount, but `CheckingAccount.withdraw()` assumes that the amount is limited
→ Subclass weakening output conditions
- `BankAccount.withdraw()` can only leave a positive balance or cause an error, `CheckingAccount.withdraw()` can leave balance negative
→ Changing additional attributes in subclass's method
→ Throwing additional exceptions in subclass's method

Key: No LSP – No Inheritance

The classic example of a problem that violates the Liskov Substitution Principle is the [Circle-Ellipse problem](https://en.wikipedia.org/wiki/Circle%E2%80%93ellipse_problem), sometimes called the Square-Rectangle problem.

By all means, it seems like you should be able to define a class `Rectangle`, with attributes `h` and `w` (for height and width), and then define a class `Square` that inherits from the `Rectangle`. After all, a square "is-a" rectangle! Unfortunately, this intuition doesn't apply to object-oriented design. A `Square` inherited from a `Rectangle` will always have both the `h` and `w` attributes, but we can't allow them to change independently of each other.
```python
class Rectangle:
    def __init__(self, w,h):
      self.w, self.h = w,h
      
# Define set_h to set h       
    def set_h(self, h):
      self.h = h

# Define set_w to set w
    def set_w(self, w):
      self.w = w   
      
class Square(Rectangle):
    def __init__(self, w):
      self.w, self.h = w, w 
      
# Define set_h to set w and h 
    def set_h(self, h):
      self.h = h
      self.w = h
      
# Define set_w to set w and h 
    def set_w(self, w):
      self.w = w   
      self.h = w  
```
above code will be violating LSP because:
Each of the setter methods of `Square` change both `h` and `w` attributes, while setter methods of `Rectangle` change only one attribute at a time, so the `Square` objects cannot be substituted for `Rectangle` into programs that rely on one attribute staying constant.

Remember that the substitution principle requires the substitution to preserve the oversall state of the program. An example of a program that would fail when this substitution is made is a unit test for a setter functions in `Rectangle` class.

## Restricting Access

In Python, all data is public. Instead of access modifiers common in languages like Java, Python uses naming <u>conventions</u> to communicate the developer's intention to class users, shifting the responsibility of safe class use onto the class user.

- Naming conventions
- Use @property to customize access
- Overriding `__getattr__()` and`__setattr__()`

### Naming convention: internal attributes

![[oop4.png]]

### Naming convention: pseudoprivate attributes

![[oop5.png]]

- The single leading underscore is a convention for internal details of implementation.
- Double leading underscores are used for attributes that should not be inherited to aviod name clashes in child classes.
- Finally, leading _and_ trailing double underscores are reserved for built-in methods.![[oop6.png]]

Notice that you were still able to use the `_is_valid()` method as usual. The single underscore naming convention is purely a convention, and Python doesn't do anything special with such attributes and methods behind the scenes.

```python
# Add class attributes for max number of days and months
class BetterDate:
    _MAX_DAYS = 31
    _MAX_MONS = 12
    
    def __init__(self, year, month, day):
        self.year, self.month, self.day = year, month, day
        
    @classmethod
    def from_str(cls, datestr):
        year, month, day = map(int, datestr.split("-"))
        return cls(year, month, day)
    
    # Add _is_valid() checking day and month values
    def _is_valid(self):
        if self.day <= BetterDate._MAX_DAYS and self.month<=BetterDate._MAX_MONS:
            return True
        return False
    
bd1 = BetterDate(2020, 4, 30)
print(bd1._is_valid())

bd2 = BetterDate(2020, 6, 45)
print(bd2._is_valid())
```
That convention is widely followed, though, so if you see<u> an attribute name</u> with one leading underscore in someone's class - don't use it! The class developer trusts you with this responsibility.

## Restricted and read-only attributes

![[np.png]]

### @property, @attr.setter

![[oop7.png]]![[oop8.png]]

attr.setter is more like validation

![[oop9.png]]
why use @property:
- User-facing: behave like attributes
- Developer-facing: give control of access

Properties control only one specific attribute that they're attached to. There are ways to prevent creating new attributes, but doing so would go against the "we're all adults here" principle.

### Create and set properties

There are two parts to defining a property:

- first, define an "internal" attribute that will contain the data;
- then, define a `@property`-decorated method whose _name is the property name_, and that returns the internal attribute storing the data.

If you'd also like to define a custom _setter_ method, there's an additional step:

- define _another_ method whose name is exactly the property name (again), and decorate it with `@prop_name.setter` where `prop_name` is the name of the property. The method should take two arguments -- `self` (as always), and the value that's being assigned to the property.

In this exercise, you'll create a `balance` property for a `Customer` class - a better, more controlled version of the `balance` _attribute_ that you worked with before.

```python
class Customer:
    def __init__(self, name, new_bal):
        self.name = name
        if new_bal < 0:
           raise ValueError("Invalid balance!")
        self._balance = new_bal  

    # Add a decorated balance() method returning _balance        
    @property
    def balance(self):
        return self._balance # make the balance attribute read-only

    # Add a setter balance() method
    @balance.setter
    def balance(self, new_bal):
        # Validate the parameter value
        if new_bal < 0:
           raise ValueError("Invalid balance!")
        self._balance = new_bal
        print("Setter method called")

# Create a Customer        
cust = Customer("Belinda Lutz",2000)

# Assign 3000 to the balance property
cust.balance=3000

# Print the balance property
print(cust.balance)

# output
Setter method called 
3000
```
Now the user of your `Customer` class won't be able to assign arbitrary values to the customers' balance. You could also add a custom _ getter_ method (with a decorator `@balance.getter`) that returns a value and gets executed every time the attribute is accessed.

## Dependency injection

Reference:
https://medium.com/@suneandreasdybrodebel/pythonic-dependency-injection-a-practical-guide-83a1b1299280
https://realpython.com/python-super/#an-overview-of-pythons-super-function

```python
import requests
class RobotApi:
    url = 'http://robot-api.com'

    def send_command(self, command, data):
        formatted_url = f'{self.url}/{command}'
        requests.post(formatted_url, data=data)

class RobotControls:
    def __init__(self, api):
        self.api = api
    def move_west(self):
        self.api.send_command('move_west', data={'meters': 1})

    def move_east(self):
        self.api.send_command('move_east', data={'meters': 1})

    def move_north(self):
        self.api.send_command('move_north', data={'meters': 1})

    def move_south(self):
        self.api.send_command('move_south', data={'meters': 1})
```
The main disadvantage of injecting dependencies through `__init__` is that it requires us to construct an object that has a `send_command` method before we can instantiate a `RobotControls`. This may not seem like a huge problem in our example, but consider the case when we want to inject `RobotControls` in a new class, and we want to inject that class as a dependency in another class and so on and so on. Take for example our `FenceGuardingRobot` class:
```python
class FenceGuardingRobot:
    fence_length = 20
    def __init__(self, robot_controls):
        self.robot_controls = robot_controls
    def guard(self):
        for _ in range(self.fence_length):
            self.robot_controls.move_north()
        for _ in range(self.fence_length):
            self.robot_controls.move_south()
```
In order to instantiate this class, we now have to write:
`fence_guarding_robot = FenceGuardingRobot(RobotControls(RobotApi()))`
So when codes increase, it explodes
Then we have
When calling `super`, Python will compute a so-called <u>linearization</u> of the base classes of the calling class, which simply means that Python figures out in which order it should look up names in the base classes. In Python this is referred to as <u>method resolution order</u>. We can change our example to use dependency injection through `super` as follows:
```python
import requests


class RobotApi:
    url = 'http://robot-api.com'

    def send_command(self, command, data):
        formatted_url = f'{self.url}/{command}'
        requests.post(formatted_url, data=data)


class RobotControls(RobotApi):
    def move_west(self):
        super().send_command('move_west', data={'meters': 1})

    def move_east(self):
        super().send_command('move_east', data={'meters': 1})

    def move_north(self):
        super().send_command('move_north', data={'meters': 1})

    def move_south(self):
        super().send_command('move_south', data={'meters': 1})


class FenceGuardingRobot(RobotControls):
    fence_length = 20

    def guard(self):
        for _ in range(self.fence_length):
            super().move_north()
        for _ in range(self.fence_length):
            super().move_south()
help(FenceGuardingRobot)
```
output from above: (see a type’s method resolution order using the builtin `help` method:)
```

class FenceGuardingRobot(RobotControls)
 |  Method resolution order:
 |      FenceGuardingRobot
 |      RobotControls
 |      RobotApi
 |      builtins.object
 |
 |  Methods defined here:
 |
 |  guard(self)
 |
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |
 |  fence_length = 20
 |
 |  ----------------------------------------------------------------------
 |  Methods inherited from RobotControls:
 |
 |  move_east(self)
 |
 |  move_north(self)
 |
 |  move_south(self)
 |
 |  move_west(self)
 |
 |  ----------------------------------------------------------------------
 |  Methods inherited from RobotApi:
 |
 |  send_command(self, command, data)
 |
 |  ----------------------------------------------------------------------
 |  Data descriptors inherited from RobotApi:
 |
 |  __dict__
 |      dictionary for instance variables (if defined)
 |
 |  __weakref__
 |      list of weak references to the object (if defined)
 |
 |  ----------------------------------------------------------------------
 |  Data and other attributes inherited from RobotApi:
 |
 |  url = 'http://robot-api.com'
```
In the `Method resolution order` section, we can see that when looking up names using `super`, Python will look for the name in `FenceGuardingRobot` first, then `RobotControls`, then `RobotApi`, then `object`.
Now  we instantiate `FenceGuardRobot`, we only need `FenceGuardRobot()`, but we need `fence_guarding_robot = FenceGuardingRobot(RobotControls(RobotApi()))` without `super`

 If replace a dependency for `FenceGuardRobot`, for example to mock out the `RobotApi` class, all we have to do is define a new type that adds a new `send_command` method earlier in the linearization:
```python
from unittest.mock import Mock  
  
class MockRobotApi(RobotApi):  
send_command = Mock()  
  
class MockedFenceGuardingRobot(FenceGuardingRobot, MockRobotApi):  
pass

help(MockedFenceGuardingRobot)

# output
class MockedFenceGuardingRobot(FenceGuardingRobot, MockRobotApi)
 |  Method resolution order:
 |      MockedFenceGuardingRobot
 |      FenceGuardingRobot
 |      RobotControls
 |      MockRobotApi
 |      RobotApi
 |      builtins.object
...
```

The main advantage of this pattern using `super` for dependency injection over through `__init__` is that we don’t have to construct the dependency graph manually. All the wiring is handled by the semantics of `super`.

cons:
1. will become fairly unclear which names are provided by which dependencies. In our example it’s obvious because all classes have exactly one dependency, but when we have more than one dependency per class, things can become pretty oblique. For example, if `FenceGuardingRobot` had more than one dependency it wouldn’t be possible to tell which part of the class was being mocked out by `MockedFenceGuardingRobot` just by looking at the definitions.
2.  all the classes participating in this pattern must be designed for multiple inheritance. Specifically, if a class takes arguments through `__init__` it must take care to also take `*args` and `**kwargs` and call `super().__init__(*args, **kwargs)` even if that class doesn’t inherit from anything since your injected class may not be the last class in the linearization:
```python
class A:
    def __init__(self, a, *args, **kwargs):
        self.a = a
        super().__init__(*args, **kwargs)
class B:
    def __init__(self, b):
        self.b = b
        super().__init__(*args, **kwargs)
class C(A, B):
    pass
```

mutiple inheritance
![A diagrammed example of multiple inheritance](https://files.realpython.com/media/multiple_inheritance.22fc2c1ac608.png)

