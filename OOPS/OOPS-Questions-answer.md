## What is Object Oriented Programming (OOPs)?
Object Oriented Programming is a programming paradigm where the complete software operates as a bunch of objects talking to each other. An object is a collection of data and the methods which operate on that data.

## Why OOPs?
The main advantage of OOP is better manageable code that covers the following:

* The overall understanding of the software is increased as the distance between the language spoken by developers and that spoken by users.
* Object orientation eases maintenance by the use of encapsulation.  One can easily change the underlying representation by keeping the methods the same.
* The OOPs paradigm is mainly useful for relatively big software.
* OOPs provides enhanced code reusability.The code is easier to maintain and update.

## Q. What is a Class?
A class is a building block of Object-Oriented Programs. It is a user-defined data type that contains the data members and member functions that operate on the data members. It is like a blueprint or template of objects having common properties and methods.

## Q. What is an Object?
An object is an instance of a class. Data members and methods of a class cannot be used directly. We need to create an object (or instance) of the class to use them. In simple terms, they are the actual world entities that have a state and behaviour.

## Q. What are the four pillars of OOP?

The four pillars of OOP are:

* Encapsulation – Wrapping data and methods that operate on that data into a single unit (class).

* Abstraction – Hiding complex implementation details and showing only the necessary features.

* Inheritance – Allowing a class to inherit fields and methods from another class.

* Polymorphism – Having many forms; the same method can behave differently based on the object calling it.

## Q. What is Encapsulation?
Encapsulation is the binding of data and methods that manipulate them into a single unit such that the sensitive data is hidden from the users
It is implemented as the processes mentioned below:

## Q. What is Abstraction?
Abstraction is similar to data encapsulation and is very important in OOP. It means showing only the necessary information and hiding the other irrelevant information from the user. Abstraction is implemented using classes and interfaces.

**Data hiding:** A language feature to restrict access to members of an object. For example, private and protected members in C++.<br>
**Bundling of data and methods together:** Data and methods that operate on that data are bundled together. For example, the data members and member methods that operate on them are wrapped into a single unit known as a class.

## Q. What is Inheritance? What is its purpose?
The idea of inheritance is simple, a class is derived from another class and uses data and implementation of that other class. The class which is derived is called child or derived or subclass and the class from which the child class is derived is called parent or base or superclass.<br>
The main purpose of Inheritance is to increase code reusability. It is also used to achieve Runtime Polymorphism.

## Q. What is the difference between the IS-A relationship and HAS-A?
IS-A represents Inheritance and HAS-A represents composition.

## Q. What is Polymorphism? and types of Polymorphism?
The word "Polymorphism" means having many forms. It is the property of some code to behave differently for different contexts. For example, we can define multiple functions having the same name but different working depending on the context.

Polymorphism can be classified into two types based on the time when the call to the object or function is resolved. They are as follows:

* Compile Time Polymorphism
* Runtime Polymorphism

A) Compile-Time Polymorphism
Compile time polymorphism, also known as static polymorphism or early binding is the type of polymorphism where the binding of the call to its code is done at the compile time. Method overloading or operator overloading are examples of compile-time polymorphism.

B) Runtime Polymorphism
Also known as dynamic polymorphism or late binding, runtime polymorphism is the type of polymorphism where the actual implementation of the function is determined during the runtime or execution. Function overriding is an example of this method.

## Q. What is the difference between overloading and overriding?

Overloading – Same method name but different parameter list (compile-time polymorphism). A compile-time polymorphism feature called overloading allows an entity to have numerous implementations of the same name. Method overloading and operator overloading are two examples.

Overriding – Same method name and parameters but redefined in a derived class using the override keyword (runtime polymorphism).**Overriding** is a form of runtime polymorphism where an entity with the same name but a different implementation is executed. It is implemented with the help of virtual functions.
```
// Overloading<br>
public void Print(string msg) { }<br>
public void Print(string msg, int count) { }<br>

// Overriding<br>
public class BaseClass {<br>
      public virtual void Display() => Console.WriteLine("Base Display");<br>
}

public class DerivedClass : BaseClass {<br>
      public override void Display() => Console.WriteLine("Derived Display");<br>
}
```

## Q. What is the difference between Overloading, hiding, shadowing and Overriding in OOP?

## Q What is Composition?
Composition is an OOP principle where a class contains objects of other classes as part of its state, instead of inheriting from them.

```
class Engine
{
    public void Start()
    {
        Console.WriteLine("Engine started.");
    }
}

class Car
{
    private Engine engine; // Car *has an* Engine

    public Car()
    {
        engine = new Engine(); // Creating an Engine object
    }

    public void Start()
    {
        engine.Start(); // Using Engine’s functionality
        Console.WriteLine("Car is running.");
    }
}
```
## Q What is the difference between Inheritance and Composition?
| Aspect                          | Composition                           | Inheritance                       |
| ------------------------------- | ------------------------------------- | --------------------------------- |
| Relationship                    | “Has-a”                               | “Is-a”                            |
| Flexibility                     | ✅ High — can change components easily | ❌ Low — tightly coupled hierarchy |
| Code reuse                      | ✅ By using other objects              | ✅ By inheriting from base class   |
| Example                         | `Car` has an `Engine`                 | `Car` is a `Vehicle`              |
| Can change behavior at runtime? | ✅ Yes (replace composed objects)      | ❌ No (fixed at compile time)      |


## Q. What different types of Inheritance are there?
Inheritance can be classified into 5 types which are as follows:<br>
Single Inheritance: Child class derived directly from the base class<br>
Multiple Inheritance: Child class derived from multiple base classes.<br>
Multilevel Inheritance: Child class derived from the class which is also derived from another base class.<br>
Hierarchical Inheritance: Multiple child classes derived from a single base class.<br>
Hybrid Inheritance: Inheritance consisting of multiple inheritance types of the above specified.<br>
C# does not support multiple inheritance.

## Q. What is the difference between abstraction and encapsulation?

Abstraction focuses on hiding complexity by exposing only the essential details.

Encapsulation focuses on protecting data by bundling it with methods and restricting access via access modifiers (private, public, etc.).

## Q.What is an interface?
A unique class type known as an interface contains methods but not their definitions. Inside an interface, only method declaration is permitted. You cannot make objects using an interface. Instead, you must put that interface into use and specify the procedures for doing so.

##  Q. What is the difference between abstract class and interface?

Abstract class: Can have abstract and non-abstract methods, fields, and constructors. Supports single inheritance.A class can implement multiple interfaces but only inherit one base class.

Interface: Defines a contract (only method/property signatures). A class can implement multiple interfaces.<br>

| Abstract Class | Interface |
| ------------ | ------------------- | 
| A class that is abstract can have both abstract and non-abstract methods.	| An interface can only have abstract methods. |<br>
| An abstract class can have final, non-final, static and non-static variables.	| The interface has only static and final variables. | 
| Abstract class doesn't support multiple inheritance	| An interface supports multiple inheritance.| 

## Q. Is it always necessary to create objects from class?
No. If the base class includes non-static methods, an object must be constructed. But no objects need to be generated if the class includes static methods. In this instance, you can use the class name to directly call those static methods.

## Q.What is the difference between a structure and a class in C++?
The structure is also a user-defined datatype in C++ similar to the class with the following differences:

The major difference between a structure and a class is that in a structure, the members are set to public by default while in a class, members are private by default.
The other difference is that we use **struct** for declaring structure and **class** for declaring a class in C#.

## Q.  What is Constructor?
A constructor is a block of code that initializes the newly created object. A constructor resembles an instance method but it’s not a method as it doesn’t have a return type. It generally is the method having the same name as the class.

## Q. What are access modifiers in OOPs?

- public – Accessible from anywhere.

- private – Accessible only within the same class.

- protected – Accessible within the same class and derived classes.

- internal – Accessible within the same assembly.

- protected internal – Accessible within the same assembly or derived class.

- private protected – Accessible within the containing class or derived class in the same assembly.

## Q. What is the virtual function and pure virtual function?
A virtual function is a function that is used to override a method of the parent class in the derived class. It is used to provide abstraction in a class.

- In C#, a virtual function is declared using the virtual keyword,
- In Java, every public, non-static, and non-final method is a virtual function.
- Python methods are always virtual.

## Q. Difference between abstract function in abstract class and virtual function in abstract class in c#
1. Abstract Function (Method)
    <br>An abstract method:
    - Has no implementation in the abstract class.
    - Must be overridden in any non-abstract derived class.
    - Can only exist inside an abstract class.
<br>
``` 
    abstract class Shape
    {
        public abstract void Draw(); // No body — must be overridden<br>
    }
    class Circle : Shape
    {
        public override void Draw()
        {
            Console.WriteLine("Drawing a circle");
        }
    }
```
2. Virtual Function (Method)
   <br>A virtual method:
   - Has a default implementation in the base class.
   - Can be overridden (but doesn’t have to be) in derived classes.
   - The class that declares it does not have to be abstract.
<br>
```
abstract class Shape
{
    public virtual void Draw()  // Has a default implementation
    {
        Console.WriteLine("Drawing a generic shape");
    }
}
```


## Q. What is the difference between Association, Aggregation, and Composition in OOP?
1. Association
A general relationship between two independent classes where one object uses or interacts with another.
- It’s a “uses-a” or “knows-a” relationship.
- There is no ownership — both can exist independently.
  
2. Aggregation (Weak Ownership)
A special form of association where one class contains another class, but the contained object can exist independently.
- It’s a “has-a” relationship (but with weak ownership).
- The child is not destroyed when the parent is destroyed.

1. Composition (Strong Ownership)
A strong form of aggregation where one class completely owns another.<br>
If the parent object is destroyed, the child object is also destroyed.
- It’s a “has-a” relationship (but with strong ownership).
- The lifetime of the part depends on the whole.

## Q. What is the difference between coupling and cohesion? 
**Coupling** is the dependency between different parts of code while **cohesion** is about the same part of code. it is good to have loos coupling and high cohesion. 