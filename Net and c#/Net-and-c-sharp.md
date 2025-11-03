## Q. What is .NET, and how does it work?
.NET is a cross-platform framework developed by Microsoft for building web, desktop, mobile, and cloud applications. It supports multiple programming languages, including C#, F#, and VB.NET, and provides a managed runtime environment for executing applications.

Instead of compiling code directly into machine instructions, .NET applications first compile into Common Intermediate Language (CIL). The Common Language Runtime (CLR) then translates CIL into machine code at runtime, allowing cross-platform execution.

Key components of .NET include:

- CLR (Common Language Runtime) – Executes .NET applications and manages memory, security, and performance
- Base Class Library (BCL) – A collection of reusable libraries for file handling, collections, and more
- JIT (Just-In-Time) Compiler – Converts CIL into optimized machine code at runtime

## Q. What is the CLR, and why is it important?
The Common Language Runtime (CLR) is the execution environment for .NET applications. It provides automatic memory management, security, and performance optimizations, making applications more reliable and efficient.

How it works:
- Code written in C# or another .NET language compiles into Common Intermediate Language (CIL)
- The Just-In-Time (JIT) compiler translates CIL into machine code at runtime
- The Garbage Collector (GC) automatically manages memory by reclaiming unused objects

The CLR enforces security policies and prevents unauthorized memory access

## Q. What is CIL (Common Intermediate Language)?
When you compile C# code, it doesn’t turn into machine code directly. Instead, it compiles into Common Intermediate Language (CIL), which is then executed by the CLR.

CIL enables:
- **Cross-platform compatibility** – Code written in any .NET language can run on different operating systems via the CLR

- **Language interoperability** – Since all .NET languages compile to CIL, C#, F#, and VB.NET can interact seamlessly

## Q. What is garbage collection in .NET, and how does it work?
Managing memory efficiently is one of the biggest challenges in programming.

In languages like C++, developers must manually allocate and free memory, which can lead to memory leaks, security issues, and crashes if done incorrectly. .NET solves this problem with garbage collection (GC), which automatically frees memory used by objects that are no longer needed.

This makes applications more reliable and easier to manage, but it also means developers need to understand how garbage collection works to avoid performance issues.

## Q.How garbage collection works
The Common Language Runtime (CLR) includes a Garbage Collector (GC) that runs automatically when needed. It follows a three-step process:

*Marking* – The GC scans memory to identify which objects are still in use

*Sweeping* – It removes objects that are no longer needed, freeing up memory

*Compacting* – It reorganizes memory to prevent fragmentation and improve efficiency

This process happens without developer intervention, which reduces the chances of memory leaks but also means developers don’t have direct control over when garbage collection occurs.

## Q. Does garbage collection affect performance?
Yes, while garbage collection helps prevent memory issues, it can temporarily pause execution when it runs. If too many objects are created and discarded frequently, GC cycles can slow down application performance.

To optimize memory usage and reduce the impact of GC:

Avoid unnecessary object creation—Reusing objects can reduce memory allocations

Use structs instead of classes for lightweight data types, since structs are stored on the stack instead of the heap

Minimize large object allocations, as large objects trigger special GC behavior

In performance-critical applications, .NET provides tools like
`
GC.Collect()
Span<T>
Memory<T>
`


## Q. What is the difference between value types and reference types in C#?

Value types store data directly on the stack (e.g., int, float, bool, struct).

Reference types store a reference to the data on the heap (e.g., class, string, array).

## Q. What is a delegate in C#?

A delegate is a type-safe function pointer . A delegate in C# is a type that represents a reference to a method. It allows methods to be passed as arguments, making it a key feature for event handling, callbacks, and functional programming.

Think of it as a function pointer, but type-safe and object-oriented.

*How delegates work*
A delegate acts as a wrapper around a method, allowing you to store and invoke it dynamically. Instead of calling a method directly, you assign it to a delegate and call the delegate instead.

```
public delegate void PrintDelegate(string message);

public class Demo {
    public static void PrintMessage(string msg) {
        Console.WriteLine(msg);
    }

    public static void Main() {
        PrintDelegate del = PrintMessage;
        del("Hello from delegate!");
    }
}
```

*Multicast delegates (calling multiple methods)*
Delegates can also store multiple method references, meaning you can assign more than one method to the same delegate. 
```
void Method1(string msg) => Console.WriteLine("Method1: " + msg);
void Method2(string msg) => Console.WriteLine("Method2: " + msg);

MessageDelegate del = Method1;
del += Method2; // Adding another method

del("Hello!");
```

**Func, Action, and Predicate Delegates**

C# also provides built-in generic delegates to make working with delegates easier:

`Func<T>`

– Returns a value. Example: 

`Func<int, int, int> add = (x, y) => x + y`


## Q. How is delegate different from an event?
An event is a language-level construct that restricts how delegates can be invoked (only the declaring class can raise the event). Events provide a publisher/subscriber pattern with controlled invocation.


## Q. What is the difference between IEnumerable, ICollection, and IList?


- IEnumerable – Supports iteration using foreach. (read-only)

- ICollection – Inherits IEnumerable, adds count and manipulation features.

- IList – Inherits ICollection, allows index-based access.

## Q. What is the difference between == and .Equals() in C#?

== checks for reference equality (by default) for reference types, and value equality for value types.

.Equals() is used for value equality and can be overridden in custom classes.

## Q. Explain boxing and unboxing in C#.

**Boxing:** Converting a value type to an object (int x = 10; object obj = x;).

**Unboxing:** Extracting the value type from an object (int y = (int)obj;).

## Q. What is the difference between IEnumerable and IQueryable?

IEnumerable: Works with in-memory collections, executes queries on the client side. It pulls all data in memory and then apply filter. 

IQueryable: Works with external data sources (like databases), executes queries on the server side (supports LINQ-to-SQL/Entity Framework). It aapply filters and pulls data only as per filter. 

For big data set IQueryable is more efficient and for small data set IEnumerable is more faster.

## Q. What is the difference between Task, Thread, and ValueTask?

- **Thread:** OS-level unit of execution. Expensive to create.

- **Task:** A higher-level abstraction over threads, supports async programming.

- **ValueTask:** A lightweight alternative to Task that avoids allocations when a result is already available

## Q. Explain Garbage Collection (GC) in .NET.
- GC automatically frees memory used by objects no longer in use.
- Works in generations (0, 1, 2, LOH) for efficiency.
- an be forced using GC.Collect(), though not recommended.
GC reclaims managed heap memory. Gen0 collects frequently; Gen2 less often for long-lived objects. The GC uses marking and compacting (for server/workstation modes) and can run in concurrent or background modes.

## Q.List all c# ..net data types and it's usage also list some advance data type
1. Value Types

    Value types hold the actual data and are stored on the stack.

    Numeric Types

    Integral types

    byte (0 to 255) – Small unsigned number.

    sbyte (-128 to 127) – Small signed number.

    short (-32,768 to 32,767) – Small signed integer.

    ushort (0 to 65,535) – Small unsigned integer.

    int (-2,147,483,648 to 2,147,483,647) – Commonly used integer.

    uint (0 to 4,294,967,295) – Unsigned integer.

    long (-9 quintillion to +9 quintillion) – Large signed integer.

    ulong (0 to 18 quintillion) – Large unsigned integer.

    nint / nuint – Platform-specific integers (introduced in C# 9).

    Floating point types

    float – 32-bit floating point, ~7 digits precision.

    double – 64-bit floating point, ~15 digits precision.

    decimal – 128-bit precise decimal (financial calculations).

    Other Built-in Value Types

    char – Represents a single Unicode character.

    bool – Represents true or false.

    struct – User-defined value type (e.g., DateTime, Point).

    enum – Represents a set of named constants.

2. Reference Types

    Reference types store the address of data on the heap.

    object – Base type for all types in C#.

    string – Immutable sequence of characters.

    dynamic – Allows runtime type checking.

    var (not a data type, but implicit typing at compile time).

3. Nullable Types

    Nullable<T> or shorthand T? – Allows value types to hold null.

    int? age = null;  
    if(age.HasValue) { Console.WriteLine(age.Value); }

4. Collections and Advanced Data Types
    Arrays

    Fixed-size collection of elements of the same type.

    int[] numbers = {1, 2, 3};

    Collections (from System.Collections.Generic)

    List<T> – Dynamic array.

    Dictionary<TKey, TValue> – Key-value pairs (hash table).

    HashSet<T> – Unique unordered collection.

    Queue<T> – FIFO collection.

    Stack<T> – LIFO collection.

    LinkedList<T> – Doubly linked list.

    Immutable Collections (System.Collections.Immutable)

    ImmutableList<T> – List that cannot be modified after creation.

    ImmutableDictionary<TKey, TValue> – Read-only key-value store.

5. Specialized / Advanced Data Types in .NET

    **Tuples**

    Store multiple values in a single object.

    ```
    var person = (Id: 1, Name: "John", Age: 30);
    Console.WriteLine(person.Name);
    ```
    **Record Types (C# 9+)**

    Immutable reference type for models and DTOs.
    ```
    public record Person(string Name, int Age);
    ```

    **Anonymous Types**

    Useful for LINQ queries.
    ```
    var emp = new { Id = 1, Name = "Alice" };
    ```
    ***Span<T> & Memory<T> (High-Performance Types)***
    - Span<T> – Works with slices of arrays and memory without allocations.
    - Memory<T> – Similar to Span<T>, but usable in async methods.
    
    **BigInteger (System.Numerics)**

    Arbitrary precision integer for very large numbers.

    **Date and Time Types**
    - DateTime – Represents date and time.
    - TimeSpan – Represents duration.
    - DateOnly (C# 10) – Date without time.
    - TimeOnly (C# 10) – Time without date.

    **Nullable Reference Types (C# 8)**

    Helps avoid null reference exceptions.
    ```
    string? name = null;
    ```

## Q. What are the main differences between .NET Framework and .NET Core / .NET 6+?
- Cross-platform: .NET Core / .NET 6+ runs on Windows, Linux, and macOS.
- Performance: .NET Core is faster and more lightweight due to modular architecture.
- Deployment: Supports self-contained deployment (no need to install runtime separately).
- Open Source: .NET Core is open-source and community-driven.
- Unified platform: Starting with .NET 5, all app types (web, mobile, desktop, IoT, etc.) use one base library.

## Q. What is Dependency Injection (DI) and how is it implemented in .NET Core?

Dependency Injection is a design pattern where an object's dependencies are provided externally.
In .NET Core, DI is built-in via the IServiceCollection in Startup.cs:
```
services.AddTransient<IUserService, UserService>();
```

You inject it in a controller:
```
public class UsersController : ControllerBase
{
    private readonly IUserService _userService;
    public UsersController(IUserService userService) => _userService = userService;
}
```

## Q. what is Generics in .NET

- Generics allow you to define type-safe classes, methods, delegates, etc. without committing to an actual data type until the class or method is instantiated.

- They improve type safety, performance, and reusability.
```
using System;

class Box<T>
{
    public T Value { get; set; }
}

class Program
{
    static void Main()
    {
        Box<int> intBox = new Box<int>();
        intBox.Value = 100; // only int allowed
        Console.WriteLine("Box<int>: " + intBox.Value);

        Box<string> strBox = new Box<string>();
        strBox.Value = "Hello Generics"; // only string allowed
        Console.WriteLine("Box<string>: " + strBox.Value);
    }
}
```

## Q. Difference between put and patch verves
**PUT**
- Definition: PUT is used to replace the entire resource with the new one.
- If the resource exists → it’s replaced.
- If it doesn’t exist → it may be created (depends on API design).
- You must send all fields, even if only one is changed.

**PATCH**
- Definition: PATCH is used for partial updates of a resource.
- Only send the fields that need to be changed.
- More efficient for large resources.

## Q. Difference between ref, out, and in parameters.

- ref passes by reference; variable must be initialized before call.
 - out passes by reference; variable need not be initialized but must be assigned in the method. 
 - in passes by readonly reference (avoids copying large structs) — cannot be modified in callee.

 ## Q. What is the difference between const, readonly, and static?

- const is compile-time constant; implicitly static; cannot change. 
- readonly is runtime constant — can be assigned in constructor. 
- static denotes a member at the type level (shared across instances).

## Q. Explain async/await and Task Parallel Library (TPL).
async/await provide an easier way to write asynchronous code. Methods return Task/Task<T> or ValueTask. await yields control back to the caller until the awaited Task completes. TPL (Task, Parallel, Task.Run) is a set of APIs for parallel and asynchronous programming.

## Q. What are extension methods? Example with LINQ.
Extension methods let you "add" methods to existing types. 
Example: 
```
public static bool IsNullOrEmpty(this string s) => string.IsNullOrEmpty(s);
``` 
LINQ methods like Select/Where are extension methods for IEnumerable<T>.

## Q.What is deferred execution in LINQ?

A: Deferred execution means a LINQ query isn't executed until it's enumerated (e.g., via ToList(), foreach, etc.). This allows query composition and efficient data retrieval.

## Q EF: Code First vs Database First vs Model First.
- Code First: you define models in code and generate DB via migrations. 
- Database First: scaffold models from an existing DB. 
- Model First: design model in designer, then generate DB and code — less common now.

## Q. Lazy, eager, and explicit loading in EF Core.
- Eager: use Include() to load related data with the main query.
- Lazy: navigation properties are loaded on access (requires enabling proxies or manual loading); can hide N+1 problems.
- Explicit: call context.Entry(entity).Collection(e => e.Children).Load() to load when needed.

## Q. What is migration in EF Core?
Migrations are a way to evolve the DB schema from code model changes—Add-Migration, Update-Database. They generate migration classes with Up()/Down().

## Q: How to handle concurrency in EF Core?
Use concurrency tokens (e.g., rowversion/timestamp) and handle DbUpdateConcurrencyException by resolving using client wins, store wins, or merge strategies.

## Q: Explain middleware in ASP.NET Core.
Middleware are components in the HTTP pipeline that inspect/modify requests and responses. Each middleware can call await next() to pass control. Examples: authentication, routing, static files.

## Q: Difference between AddTransient, AddScoped, AddSingleton.
- Transient — new instance each time requested; 
- Scoped — one instance per request scope (e.g., HTTP request); 
- Singleton — single instance for the application's lifetime.

## Q: What is Kestrel?
Kestrel is the cross-platform web server for ASP.NET Core used to host web apps. Often run behind a reverse proxy like Nginx or IIS.

## Q: What are filters in ASP.NET Core?
Filters let you run code before/after controller actions (auth, logging, exception handling, result processing). 
Types include <br>
Authorization, <br>
Resource, <br>
Action, <br>
Exception, <br>
Result filters. <br>

## Q: What is lock, Monitor, and SemaphoreSlim?
lock(obj) is syntactic sugar over Monitor.Enter/Exit for exclusive synchronization. SemaphoreSlim is a lightweight semaphore controlling concurrent access to a resource (useful to limit concurrency degree).

## Q: How to implement authentication & authorization in ASP.NET Core?
Authentication verifies identity (cookie auth, JWT, OAuth/OpenID Connect). Authorization checks permissions (policies, roles). Use middleware AddAuthentication and AddAuthorization, configure schemes, and protect endpoints with [Authorize].

## Q: What is JWT?
JSON Web Token — a compact, URL-safe token containing claims and a signature (usually signed by server or issuer). Common for stateless API authentication.

## Q: How does OAuth2/OpenID Connect work in .NET?
OAuth2 provides delegated authorization (access tokens). OpenID Connect builds on it to provide authentication (ID token). In .NET use Microsoft.Identity.Web / OpenIdConnect handlers or IdentityServer/third-party providers to implement flows (authorization code, implicit, etc.).

## Q: What is Clean Architecture?
Clean Architecture separates code into layers (Entities → Use Cases/Domain → Interfaces → Infrastructure/UI). Dependencies point inward. It keeps business logic independent from frameworks, enabling testability and maintainability.

## Q: Explain CQRS and MediatR.
CQRS (Command Query Responsibility Segregation) splits reads and writes into different models. MediatR is a library implementing the Mediator pattern to decouple request/handlers and commonly used to implement CQRS handlers.

## Q: Caching in .NET Core (MemoryCache, DistributedCache, Redis).
IMemoryCache — in-process cache (fast, not shared). IDistributedCache — abstraction for shared caches (Redis, SQL Server). Use Redis for high-scale distributed caching.

## Q. What is N+1 Problem in EF (especially with Lazy Loading)
What it is: When you query a collection of entities, and then for each entity EF lazily loads related data, it issues an additional query per entity.<br>
Example: <br>
```
var orders = context.Orders.ToList(); 
foreach (var order in orders)
{
    var customer = order.Customer; // triggers a new query for EACH order!
}
```
If there are N orders, EF will run 1 query for the orders + N queries for customers → N+1 problem.
Why it’s bad: It kills performance with many round trips to the database.
Solutions:
1. Eager loading (Include):
```
var orders = context.Orders.Include(o => o.Customer).ToList();
```
2. Explicit loading if you want controlled fetch.
3. Projection into DTOs to load only what you need.

## Q. What is the benefit of ‘using’ statement in C#?
The ‘using’ statement can be used in order to obtain a resource for processing before automatically disposing it when execution is completed.

## Q. What is serialization?
In order to transport an object through a network, we would need to convert it into a stream of bytes. This process is called Serialization. 

## Q. What is meant by Unmanaged or Managed Code?
In simple terms, managed code is code that is executed by the CLR (Common Language Runtime). This means that every application code is totally dependent on the .NET platform and is regarded as overseen in light of it. Code executed by a runtime programme that is not part of the .NET platform is considered unmanaged code. Memory, security, and other activities related to execution will be handled by the application's runtime.

## Q. What are sealed classes in C#?
When a restriction needs to be placed on the class that needs to be inherited, sealed classes are created. In order to prevent any derivation from a class, a sealed modifier is used. Compile-time error occurs when a sealed class is forcefully specified as a base class.

## Q. What are the differences between System.String and System.Text.StringBuilder classes?
System.String is absolute. When a string variable’s value is modified, a new memory is assigned to the new value. The previous memory allocation gets released. System.StringBuilder, on the other hand, is designed so it can have a mutable string in which a plethora of operations can be performed without the need for allocation of a separate memory location for the string that has been modified.

## Q.What is the difference between Dispose() and Finalize()methods?
Dispose() is used when an object is required to release any unmanaged resources in it. Finalize(), on the other hand, doesn’t assure the garbage collection of an object even though it is used for the same function.

## Q. List down the most commonly used types of exceptions in .NET
Commonly used types of exceptions in .NET are:

ArgumentException <br>
ArithmeticException <br>
DivideByZeroException <br>
OverflowException <br>
InvalidCastException <br>
InvalidOperationException <br>
NullReferenceException <br>
OutOfMemoryException <br>
StackOverflowException <br>

## Q. What is the difference between “is” and “as” operators in c#?
An “is” operator can be used to check an object’s compatibility with respect to a given type, and the result is returned as a Boolean. An “as” operator can be used for casting an object to either a type or a class.

## Q. What is an indexer in C#?
In C#, indexers are used to index instances of a class or structure. The indexed values can then be easily accessed like an array, but without explicitly specifying a type or instance member.

## Q. What are the different types of classes in C#?
1. Abstract classes: These provide a common definition for a base class that other classes can be derived from
2. Static classes: These contain static items that can only interact with other static items
3. Partial classes: These are portions of a class that a compiler can combine to form a complete class
4. Sealed classes: These cannot be inherited by any class but can be instantiated

## Q. What is the difference between fields and properties in C#?
A field is a member of a class or an object of any type that represents a location for storing a value, whereas a property is a class member that provides a mechanism to read, write, and compute the value of a private field.

## Q.What is meant by object pooling in C#?
Object pooling is a software creational design pattern that recycles objects rather than recreating them. It does that by holding selected objects in a pool ready for use when they are requested by an application. 

This process helps to improve performance by minimizing unnecessary object creation. 

## Q.How is reflection used in C#?
In C#, reflection is used to obtain metadata on types at runtime. In other words, it allows developers to retrieve data on the loaded assemblies and the types within them.

It’s implemented using a two-step process. First, you get the type object. Second, you use the type to browse members, such as methods and properties. 

## Q. What are the advantages of generics in C#?
In C#, generics allow the developer to define classes and methods which can be used with any data type. This brings several benefits:

- Saves time by reusing code
- Provides type safety without unnecessary overhead
- Removes the need for boxing and unboxing
- Generic collection types generally perform better with value types because there is no need to box the values

##. Q. What are the disadvantages of generics in C#?

There are a few limitations with generics. These include:
- They cannot be used with enumerations
- They cannot be used with lightweight dynamic methods
- The .NET framework doesn’t support context-bound generic types

## Q.What is a multicast delegate in C#?
Unlike a simple delegate, a multicast delegate in C# references multiple target methods. When a multicast delegate is used, all the functions the delegate is pointing to are invoked. They’re implemented using the MulticastDelegate class, which is derived from the system.

## Q. What is the difference between late binding and early binding in C#?
The key differences between early binding and late binding are:

- Early binding occurs at compile-time, whereas late binding occurs at runtime
- Early binding uses class information to resolve method calling, whereas late binding uses the object to resolve method calling
- Typically, the performance of late binding is slower than early binding because it occurs at runtime

## Q. What is the difference between a throw exception and a throw clause in C#?
The fundamental difference is that throw exceptions overwrite the stack trace, whereas throw clauses retain the stack information. As such, it is much harder to retrieve the original code responsible for throwing the exception with throw exceptions. 

## Q. How do you implement Dependency Injection in C#?
Dependency Injection (DI) in C# is typically implemented using constructor, method, or property injection. In ASP.NET Core, DI is natively supported by the framework. Services are registered in the Startup.cs file using methods like AddSingleton, AddScoped, or AddTransient and these services can then be injected into controllers or other classes through their constructors.

## Q. Explain the async and await keywords in C#. How do they improve performance?
async and await simplify asynchronous programming in C#. The async keyword marks a method as asynchronous, allowing it to run in the background without blocking the main thread. The await keyword pauses method execution until the awaited task completes, allowing other tasks to run concurrently. This improves performance, especially in I/O-bound operations, by preventing the main thread from being blocked during long-running tasks.

## Q. What are the benefits of using Span<T> and Memory<T> in C#?
Span<T> and Memory<T> are value types introduced to manage and manipulate contiguous memory blocks more efficiently. Span<T> operates on stack-allocated memory, offering performance benefits by avoiding heap allocations, while Memory<T> can be used on both the stack and the heap, making it more versatile. Both types are particularly useful in scenarios requiring high-performance processing of large data sets, such as parsing, slicing, or working with buffers.

## Q. What is the difference between covariance and contravariance in C# and how are they implemented?
Covariance and contravariance in C# allow for more flexible assignments of types. Covariance lets you assign a more derived type to a generic type parameter, while contravariance allows assignment in the opposite direction. Covariance is implemented using the out keyword, typically in interfaces or delegates where a generic type is only returned. Contravariance uses the in keyword, where the generic type is only consumed as a parameter. These features are essential in scenarios like LINQ, where flexible type assignments are necessary.

## Q. How does C# implement covariance and contravariance?
Covariance: Enables assignment of a more derived type to a less derived generic type. (out keyword).
```
IEnumerable<object> objects = new List<string>(); // Covariance
Action<string> action = (object obj) => {}; // Contravariance
```
Contravariance: Enables assignment of a less derived type to a more derived generic type. (in keyword).
## Q. What is a sealed class in C#?
A sealed class in C# is a class that cannot be inherited. When a class is marked as sealed, no other class can derive from it. This is useful when you want to prevent further inheritance, ensuring that the class’s behavior remains unchanged or fixed.


## Q. What is middleware in ASP.NET Core?
In ASP.NET Core, middleware is a set of components that process HTTP requests and responses as they pass through the application. Every request that enters an ASP.NET Core application goes through a middleware pipeline before reaching the final destination, such as a controller or an endpoint.

Middleware components can perform tasks like logging, authentication, authorization, exception handling, and request modification. Each component has the option to either process the request or pass it along to the next middleware in the pipeline.

## Q. What is the difference between In C#, both `Finalize` and `Dispose`
In C#, both
`Finalize`
and
`Dispose`
are used for cleaning up unmanaged resources like file handles, database connections, or network sockets. However, they work differently in terms of when and how they release resources.

`Dispose`
is part of the
`IDisposable`
interface and allows manual resource cleanup. It should be called explicitly when you are done using an object.

By calling
`Dispose()`
, developers ensure that resources are freed as soon as they are no longer needed, rather than waiting for garbage collection.

`Finalize`
, on the other hand, is called implicitly by the garbage collector before an object is destroyed. It is defined using a destructor:
```
class ResourceHandler
{
    ~ResourceHandler()
    {
        Console.WriteLine("Finalizer called by GC.");
    }
}
```
Because
`Finalize`
runs automatically, it should only be used as a backup cleanup method in case
`Dispose`
was not called. However, finalizers introduce performance overhead because the garbage collector must process them before reclaiming memory.

Objects that use
`Dispose`
should also call
`GC.SuppressFinalize(this)`
to prevent the garbage collector from running
`Finalize`
unnecessarily.


## Q. What are some best practices for working with Entity Framework Core?
Entity Framework Core (EF Core) is a powerful object-relational mapper (ORM) that simplifies database access in .NET applications. 

However, inefficient use can lead to performance bottlenecks, security risks, and maintainability issues. Following best practices ensures that applications run efficiently and scale well.

Use
By default, EF Core tracks changes to entities, which adds overhead. For read-only queries,
`AsNoTracking()`
improves performance by disabling change tracking.
```
var users = dbContext.Users.AsNoTracking().ToList();
```
This is especially useful for reporting or data retrieval scenarios where tracking changes is unnecessary.

Optimize Queries with Projection
Fetching only required fields instead of entire entities reduces data transfer and improves performance.
```
var names = dbContext.Users.Select(u => u.Name).ToList();
```
Instead of retrieving full user objects, this query loads only the
`Name`
field, reducing memory usage.

**Avoid Lazy Loading in Performance-Sensitive Applications**

Lazy loading automatically fetches related entities when accessed, but it can lead to the N+1 query problem, causing multiple small queries instead of a single optimized one.

Use eager loading (
`Include()`
) or explicit loading when needed.
```
var users = dbContext.Users.Include(u => u.Orders).ToList();
```
This fetches users and their related orders in one query rather than multiple.

**Use Transactions for Multiple Operations**

When modifying multiple records, transactions ensure data consistency and prevent partial updates.
```
using var transaction = dbContext.Database.BeginTransaction();
try
{
    dbContext.Users.Add(new User { Name = "John" });
    dbContext.SaveChanges();
    transaction.Commit();
}
catch
{
    transaction.Rollback();
}
```
Transactions help maintain data integrity in cases where multiple database operations depend on each other.

**Leverage Connection Pooling and Indexing**

Using a connection pool reduces the overhead of repeatedly opening and closing database connections. Proper indexing improves query performance by speeding up lookups.
```
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(connectionString, sqlOptions =>
        sqlOptions.EnableRetryOnFailure()));
```
Here,
`EnableRetryOnFailure()`
helps manage transient failures in cloud-based databases.


## Q. is string a by refrence or byvalue ? and why 
string is object but works as byvalue. It is immutable object, everytime you assign value , it allocates new memoery and and new isntace of object is created. MS has designed this as intention to corelate it with real world. 

