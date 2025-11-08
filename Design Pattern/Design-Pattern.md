# Archituctural Pattern, Archituctural Style, Design Principle and Design Patterns


## Q. What is difference between archituctural pattern and archituctural style?

## Q. What is difference between Design Principle and Design patterns?

## Q. What are SOLID Principles? How they different from Design Patterns?

## Q. What is Single Responsibility Principle?

## Q. What is Open-closed Principle?

## Q. What is Liskov Substitution Principle?

## Q. What is Interface Segregation Principle?

## Q. What is Dependency Inversion Principle?

## Q. What is DRY principle?

## Q. What is KISS principle?

## Q. What are Design Patterns and what problem they solve?
Design patterns are solutions to software design problems you find again and again in real-world application development. Patterns are about reusable designs and interactions of objects.

The 23 Gang of Four (GoF) patterns are generally considered the foundation for all other patterns. They are categorized in three groups: Creational, Structural, and Behavioral

## Q. What are the types of Design Patterns?
They are categorized in three groups: Creational, Structural, and Behavioral

## Q. What are Creational Design Patterns?
**Creational Patterns:**: Creational Design Patterns focus on the process of object creation in software development. These patterns make sure that we create things in a way that's not only easy but also flexible, so we can change them later if we need too. They hide the complicated details of how we put pieces together.

- **Abstract Factory**	Creates an instance of several families of classes
- **Builder**	Separates object construction from its representation
- **Factory Method**	Creates an instance of several derived classes
- **Prototype**	A fully initialized instance to be copied or cloned
- **Singleton**	A class of which only a single instance can exist  
## Q. What are Structural Design Patterns?
**Structural Patterns**: A Structural Design pattern is like a recipe for putting together different objects and classes to build a bigger structure. It's a bit like following a blueprint to construct a house. These patterns teach us how to combine the unique parts of a system in a way that's easy to change or expand without affecting the entire system.

- **Adapter**	Match interfaces of different classes
- **Bridge**	Separates an object’s interface from its implementation
- **Composite**	A tree structure of simple and composite objects
- **Decorator**	Add responsibilities to objects dynamically
- **Facade**	A single class that represents an entire subsystem
- **Flyweight**	A fine-grained instance used for efficient sharing
- **Proxy**	An object representing another object

## Q. What are Behavioral Design Patterns?
**Behavioral Patterns**: These patterns help solve common problems in how pieces of code share tasks, hide whay they do, and stay organized. When developers use these patterns, it's like building a puzzle where the pieces fit together easily, making the software more organized, easy to change, and less likely to break when we need to add or change things. So it's like having a guide to make sure all the parts of your software work together smoothly.

- **Chain of Resp.**	A way of passing a request between a chain of objects
- **Command**	Encapsulate a command request as an object
- **Interpreter**	A way to include language elements in a program
- **Iterator**	Sequentially access the elements of a collection
- **Mediator**	Defines simplified communication between classes
- **Memento**	Capture and restore an object's internal state
- **Observer**	A way of notifying change to a number of classes
- **State**	Alter an object's behavior when its state changes
- **Strategy**	Encapsulates an algorithm inside a class
- **Template Method**	Defer the exact steps of an algorithm to a subclass
- **Visitor**	Defines a new operation to a class without change
- 
## Q. What is Singleton Design Pattern?

## Q. How to make singleton pattern thread safe?

## Q. What is Factory pattern? Why to use factory pattern? How to implement Factory method pattern?
The Factory Method design pattern defines an interface for creating an object, but let subclasses decide which class to instantiate. This pattern lets a class defer instantiation to subclasses. 
The classes and objects participating in this pattern include:

- Product  (Page)
   - defines the interface of objects the factory method creates
- ConcreteProduct  (SkillsPage, EducationPage, ExperiencePage)
   - implements the Product interface
- Creator  (Document)
   - declares the factory method, which returns an object of type Product. Creator may also define a default implementation of the factory method that returns a default ConcreteProduct object.
   - may call the factory method to create a Product object.
- oncreteCreator  (Report, Resume)
   - overrides the factory method to return an instance of a ConcreteProduct.
```
namespace Factory.NetOptimized;

using static System.Console;

/// <summary>
/// Factory Design Pattern
/// </summary>
public class Program
{
    public static void Main()
    {
        // Document constructors call Factory Method
        List<Document> documents = [new Resume(), new Report()];

        // Display document pages
        foreach (var document in documents)
        {
            document.CreatePages();  // Factory method

            WriteLine($"{document} --");
            foreach (var page in document.Pages) WriteLine($" {page}");
            WriteLine();
        }

        // Wait for user
        ReadKey();
    }
}

/// <summary>
/// The 'Product' abstract class
/// </summary>
public abstract class Page
{
    // Override. Display class name
    public override string ToString() => GetType().Name;
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class SkillsPage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class EducationPage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class ExperiencePage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class IntroductionPage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>    
public class ResultsPage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class ConclusionPage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class SummaryPage : Page
{
}

/// <summary>
/// A 'ConcreteProduct' class
/// </summary>
public class BibliographyPage : Page
{
}

/// <summary>
/// The 'Creator' abstract class
/// </summary>
public abstract class Document
{
    // Gets list of document pages
    public List<Page> Pages { get; protected set; } = null!;

    // Factory Method
    public abstract void CreatePages();

    // Override
    public override string ToString() => GetType().Name;
}

/// <summary>
/// A 'ConcreteCreator' class
/// </summary>
public class Resume : Document
{
    // Factory Method implementation
    public override void CreatePages()
    {
        Pages =
        [
            new SkillsPage(),
            new EducationPage(),
            new ExperiencePage()
        ];
    }
}

/// <summary>
/// A 'ConcreteCreator' class
/// </summary>
public class Report : Document
{
    // Factory Method implementation
    public override void CreatePages()
    {
        Pages =
        [
            new IntroductionPage(),
            new ResultsPage(),
            new ConclusionPage(),
            new SummaryPage(),
            new BibliographyPage()
        ];
    }
}

```


## Q. What is Abstract Factory pattern?


## Q. What is the Observer pattern, and how does C# implement it?
The Observer pattern defines a one-to-many relationship: a subject maintains a list of observers and notifies them when its state changes. In .NET, this is commonly implemented using delegates and the event keyword. Clients subscribe to an event (backed by a delegate) on the subject. When the subject changes, it invokes the delegate, calling all registered handlers. An event is essentially an automatic notification that some action has occurred, built on delegates. Thus C#’s event construct encapsulates the Observer pattern.
