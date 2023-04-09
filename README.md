## C# Coding Guidelines

### Revision History

| Date | Version | Description |
| --- | --- | --- |
| 2/2/2021 | 1.0 | Initial Version |
| 5/30/2022 | 2.0 | DI |
| 1/23/2023 | 3.0 | Notion |

### Table of Contents
- [C# Coding Guidelines](#c--coding-guidelines)
  * [Revision History](#revision-history)
  * [Table of Contents](#table-of-contents)
  * [Introduction](#introduction)
  * [Coding Standards](#coding-standards)
    + [Naming Conventions](#naming-conventions)
    + [Pascal Case](#pascal-case)
    + [Variables and Parameters](#variables-and-parameters)
    + [Hungarian notation](#hungarian-notation)
    + [Caps](#caps)
    + [Meaningful names](#meaningful-names)
    + [Abbreviations](#abbreviations)
    + [Underscores](#underscores)
    + [Type names](#type-names)
    + [Interfaces](#interfaces)
    + [File Names](#file-names)
    + [Namespaces](#namespaces)
    + [Alignment and indentation](#alignment-and-indentation)
    + [Object Declarations](#object-declarations)
    + [Enums](#enums)
    + [Events](#events)
    + [Exceptions](#exceptions)
  * [Meaningful Error Messages](#meaningful-error-messages)
  * [Reasonably Sized Functions and Methods](#reasonably-sized-functions-and-methods)
  * [Comments](#comments)
  * [Automated Testing](#automated-testing)
  * [Global Variables](#global-variables)
  * [Exception Handling](#exception-handling)
  * [Single Return Statements](#single-return-statements)
  * [**SOLID Principles**](#--solid-principles--)
- [Project Basic Structure](#project-basic-structure)
- [Dependency Injection](#dependency-injection)
- [ORMs and Databases](#orms-and-databases)
  * [Entity Framework](#entity-framework)
    + [EF Identity Models](#ef-identity-models)
    + [Keys of Type Guid](#keys-of-type-guid)
    + [Auto-Generated Keys](#auto-generated-keys)
    + [Circular Cascade Delete Rules](#circular-cascade-delete-rules)
  * [SQL](#sql)
    + [SQL Stored Procedures and Entity Framework](#sql-stored-procedures-and-entity-framework)
  * [Data Access through Repositories](#data-access-through-repositories)
  * [Cancellation Tokens](#cancellation-tokens)
  * [API REST Controllers](#api-rest-controllers)
    + [XML Comments and Decorators](#xml-comments-and-decorators)
  * [Repositories in API Controllers](#repositories-in-api-controllers)
  * [Visual Studio Scaffolding](#visual-studio-scaffolding)

### Introduction

Alset is a software development company specializing in delivering custom software solutions and providing consultancy on good product development processes, from the initial steps to ready-to-market launches. We also offer staff augmentation or recruitment services to help businesses reach their return on investment faster.

Well-written software offers many advantages. It will contain fewer bugs and run more efficiently than poorly written programs. Since the software has a life cycle and much revolves around maintenance, it will be easier for the original developer(s) and future code keepers to maintain and modify the software as needed. This will lead to increased productivity of the developer(s). The overall cost of the software is reduced when the code is developed and maintained according to software standards.

A distinction has been made between standards and guidelines. Standards are rules which programmers are expected to follow. Guidelines can be viewed as suggestions that can help programmers write better software and are optional but highly recommended. The use of standards will be enforced through software peer reviews.

It is important to note that standards are not fixed but will evolve. Developers are encouraged to provide feedback to contact@alset.com.mx.

The following document outlines best practices for C# coding. Following these guidelines will make your code more readable, maintainable, and consistent. 

### Coding Standards

#### Naming Conventions

Use consistent naming conventions throughout the codebase. This includes naming variables, functions, classes, and other entities. For C#, the standard naming convention uses PascalCase for class, method, and property names. For variables and parameters, use camelCase. 

| Object Name | Notation | Length | Plural | Prefix | Suffix | Abbreviation | Char Mask | Underscores |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Class name | PascalCase | 128 | No | No | Yes | No | \[A-z\]\[0-9\] | No |
| Constructor name | PascalCase | 128 | No | No | Yes | No | \[A-z\]\[0-9\] | No |
| Method name | PascalCase | 128 | Yes | No | No | No | \[A-z\]\[0-9\] | No |
| Method arguments | camelCase | 128 | Yes | No | No | Yes | \[A-z\]\[0-9\] | No |
| Local variables | camelCase | 50 | Yes | No | No | Yes | \[A-z\]\[0-9\] | No |
| Constants name | PascalCase | 50 | No | No | No | No | \[A-z\]\[0-9\] | No |
| Field name | camelCase | 50 | Yes | No | No | Yes | \[A-z\]\[0-9\] | Yes |
| Properties name | PascalCase | 50 | Yes | No | No | Yes | \[A-z\]\[0-9\] | No |
| Delegate name | PascalCase | 128 | No | No | Yes | Yes | \[A-z\] | No |
| Enum type name | PascalCase | 128 | Yes | No | No | No | \[A-z\] | No |

#### Pascal Case

Do use PascalCasing for **class** names and **method** names. Class names are nouns (phrases) or adjectives.

```plaintext
public class ClientActivity
{
  public void ClearStatistics()
  {
    //...
  }
  public void CalculateStatistics()
  {
    //...
  }
}
```

#### Variables and Parameters

Do use camelCasing for method arguments and local variables

```plaintext
public class UserLog
{
  public void Add(LogEvent logEvent)
  {
    int itemCount = logEvent.Items.Count;
    // ...
  }
}
```

#### Hungarian notation

Do not use Hungarian notation or any other type of identification in identifiers.

```plaintext
// Correct
int counter;
string name;    
// Avoid
int iCounter;
string strName;
```

#### Caps

Do not use Screaming Caps for constants or read-only variables.

```plaintext
// Correct
public const string ShippingType = "DropShip";
// Avoid
public const string SHIPPINGTYPE = "DropShip";
```

#### Meaningful names

Use meaningful variable names to make your code more readable and understandable. Avoid using short, cryptic variable names.

```plaintext
var seattleCustomers = from customer in customers
  where customer.City == "Seattle" 
  select customer.Name;
```

#### Abbreviations

Avoid using abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri.

```plaintext
// Correct
UserGroup userGroup;
Assignment employeeAssignment;     
// Avoid
UserGroup usrGrp;
Assignment empAssignment; 
// Exceptions
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
UriPart uriPart;
```

#### Underscores

Do not use underscores in identifiers. Exception: you can prefix private fields with an underscore

```plaintext
// Correct
public DateTime clientAppointment;
public TimeSpan timeLeft;    
// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
// Exception (Class field)
private DateTime _registrationDate;
```

#### Type names

Use predefined type names (C# aliases) like int, float, and string for local parameters and member declarations. Try to avoid using .NET Framework names like Int32 and Single. Using implicit type var is recommended.

```plaintext
// Correct
string firstName;
int lastIndex;
bool isSaved;
string commaSeparatedNames = string.Join(", ", names);
int index = int.Parse(input);
// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
String commaSeparatedNames = String.Join(", ", names);
Int32 index = Int32.Parse(input);
```

#### Interfaces

Do prefix interfaces with the letter I. Interface names are nouns (phrases) or adjectives.

```plaintext
public interface IShape
{
}
```

#### File Names

Do name source files according to their main classes. Exception: file names with partial classes reflect their source or purpose, e.g., designer, generated, etc.

```plaintext
// Located in Task.cs
public partial class Task
{
}
// Located in Task.generated.cs
public partial class Task
{
}
```

#### Namespaces

Do organize namespaces with a clearly defined structure:

```plaintext
// Examples
namespace Company.Product.Module.SubModule
{
}
namespace Product.Module.Component
{
}
namespace Product.Layer.Module.Group
{
}
```

#### Alignment and indentation

Do vertically align curly brackets and indent using tabs

```plaintext
// Correct
class Program
{
  static void Main(string[] args)
  {
    //...
  }
}
```

#### Object Declarations

Do declare all member variables at the top of a class, with fields at the very top, properties, constructors, public methods, and private methods at last.

```plaintext
// Correct
public class Account
{
  private string _bankName;
  public decimal Reserves { get; set; }
 
  // Constructor
  public Account()
  {
    // ...
  }

  public Task GetAccount()
  {
    // ...
  }

  private Task SetAccount()
  {
    // ...
  }
}
```

#### Enums

Do use singular names for enums. Exception: bit field enums.

```plaintext
// Correct
public enum Color
{
  Red,
  Green,
  Blue,
  Yellow,
  Magenta,
  Cyan
} 
// Exception
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```

Do not explicitly specify a type of an enum or values of enums (except bit fields):

```plaintext
// Don't
public enum Direction : long
{
  North = 1,
  East = 2,
  South = 3,
  West = 4
} 
// Correct
public enum Direction
{
  North,
  East,
  South,
  West
}
```

Do not use an “Enum” suffix in enum type names:

```plaintext
// Don't
public enum CoinEnum
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
} 
// Correct
public enum Coin
{
  Penny,
  Nickel,
  Dime,
  Quarter,
  Dollar
}
```

Do not use “Flag” or “Flags” suffixes in enum type names:

```plaintext
// Don't
[Flags]
public enum DockingsFlags
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
// Correct
[Flags]
public enum Dockings
{
  None = 0,
  Top = 1,
  Right = 2, 
  Bottom = 4,
  Left = 8
}
```

#### Events

Do use the suffix EventArgs at the creation of the new classes comprising the event information:

```plaintext
// Correct
public class BarcodeReadEventArgs : System.EventArgs
{
}
```

Do name event handlers (delegates used as types of events) with the “EventHandler” suffix, as shown in the following example:

```plaintext
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

DO use two parameters named sender and e in event handlers. The sender parameter represents the object that raised the event. The sender parameter is typical of a type object, even if employing a more specific type is possible.

```plaintext
public void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e)
{
  //...
}
```

#### Exceptions

Do not throw exceptions unless it is strictly necessary.

```plaintext
throw new Exception(“Error”)
```

Do use the suffix exception at the creation of the new classes comprising the exception information:

```plaintext
// Correct
public class BarcodeReadException : System.Exception
{
}
```

### Meaningful Error Messages

Error handling is an essential aspect of computer programming. This includes adding the necessary logic to test for and handle errors and making error messages meaningful.

Error messages should be meaningful. When possible, they should indicate the problem, where it occurred, and when.

### Reasonably Sized Functions and Methods

Software modules and methods should not contain a massive number of lines of code. They should be written to perform one specific task. If they become too long, the task can be broken down into subtasks that new routines or methods can handle. A reasonable number of lines of code for a routine or a method is 200. This does not include documentation, either in the function/method header or inline comments.

### Comments

Write comments for non-obvious code and all classes, properties, or methods. While the code should be self-explanatory, there may be parts that are not immediately clear. In these cases, it is important to write comments to explain what is happening. Use XML documentation to write comments that can be generated into documentation using tools like Sandcastle or DocFX. Here's an example:

```plaintext
/// <summary>
/// Adds two integers together.
/// </summary>
/// <param name="a">The first integer.</param>
/// <param name="b">The second integer.</param>
/// <returns>The sum of the two integers.</returns>
public int Add(int a, int b)
{
    return a + b;
}
```

Here's a list of recommended XML tags and what they do:

*   **\<summary>**: A brief description of the member.
*   **\<param>**: A description of a method parameter.
*   **\<returns>**: A description of the method return value.
*   **\<remarks>**: Additional information about the member.
*   **\<example>**: An example of how to use the member.
*   **\<seealso>**: A reference to another member that is related to the current member.

Read all the other types of XML documentation here: [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/xmldoc/recommended-tags)

### Automated Testing

Use automated testing to ensure code quality and prevent regressions. Use xUnit for API test. Here's an example:

```plaintext
/// <summary>
/// Class for testing the User functionality of the API.
/// </summary>
public class UsersTest : IClassFixture<WebApplicationFactory<Startup>>
{
    private readonly WebApplicationFactory<Startup> _factory;
    private readonly IConfiguration _configuration;
    private readonly IApiService _apiService;
    private readonly string _confirmUrl;

    /// <summary>
    /// Constructor for the UsersTest class.
    /// </summary>
    /// <param name="factory">The WebApplicationFactory instance to use.</param>
    public UsersTest(WebApplicationFactory<Startup> factory)
    {
        _factory = factory;
        _configuration = InitConfiguration();
        ICrypto crypto = new Crypto(_configuration);
        _apiService = new ApiService(_configuration, crypto);
        _confirmUrl = _configuration["Confirm.Url"];
    }

    private static IConfiguration InitConfiguration()
    {
        var config = new ConfigurationBuilder()
            .AddJsonFile("appsettings.json")
            .Build();
        return config;
    }

    /// <summary>
    /// Test method for creating a user via the API.
    /// </summary>
    [Fact]
    public async Task CreateUser()
    {
        //Arrange
        var client = _factory.CreateClient();
        Random randomNumber = new Random();
        var userRequest = new UserRequest

        {
            Email = $"TestUser{randomNumber.Next(1, 50)}@yopmail.com",
            Password = "Abcd1234@",
            FirstName = $"Test{randomNumber.Next(1, 50)}",
            LastName = "User",
            CallbackUrl = _confirmUrl,
        };

        //Act

        var createResponse = await _apiService.Post<UserRequest, UserResponse>("api/Users", _configuration["Site.Url"], userRequest, false, client: client);

        //Assert
        Assert.True(createResponse.Success && !string.IsNullOrEmpty(createResponse.Id));
    }
}
```

Use NUnit for .NET MAUI. Here is an example:

```plaintext
/// <summary>
/// Class for testing the mobile app.
/// </summary>
[TestFixture(Platform.Android)]
[TestFixture(Platform.iOS)]
public class Tests
{
    IApp app;
    Platform platform;

    private bool _onAndroid;
    private bool _oniOS;

    /// <summary>
    /// Constructor for the Tests class.
    /// </summary>
    /// <param name="platform">The platform to test on (iOS or Android).</param>
    public Tests(Platform platform)
    {
        this.platform = platform;
    }

    [SetUp]
    public void BeforeEachTest()
    {
        app = AppInitializer.StartApp(platform);
        _onAndroid = app.GetType() == typeof(AndroidApp);
        _oniOS = app.GetType() == typeof(iOSApp);
    }

    /// <summary>
    /// Test method for launching the app.
    /// </summary>
    [Test]
    public void AppLaunches()
    {
        app.Screenshot("Main Page");
        app.Repl();
    }

    /// <summary>
    /// Test method for logging in to the app.
    /// </summary>
    [Test]
    public void Login()
    {
        //Arrenge
        OpenLoginPage();

        //Act
        app.EnterText(e => e.Marked("Email_Entry"), email);
        app.Screenshot("Email entered");

        app.EnterText(e => e.Marked("Password_Entry"), password);
        app.Screenshot("Password entered");

        app.Tap(e => e.Marked("Login_Button"));

        var loggedInPageResults = app.WaitForElement(e => e.Marked("Home_Page"));

        app.Screenshot("User Logged in");

        //Assert
        Assert.IsTrue(loggedInPageResults.Any());
    }

    /// <summary>
    /// Opens the login page.
    /// </summary>
    public void OpenLoginPage()
    {
        var loginPageResults = app.WaitForElement(e => e.Marked("Login_Page"));
        if (!loginPageResults.Any())
            Assert.Fail("Login page not found");
    }
}
```

### Global Variables

Avoid using global variables, as they can make code difficult to understand and maintain. Instead, use local variables or pass variables as arguments to functions. Here's an example:

```plaintext
/// <summary>
/// Example class.
/// </summary>
public class ExampleClass
{
    /// <summary>
    /// Example method.
    /// </summary>
    /// <param name="exampleParameter">The example parameter.</param>
    /// <returns>The result of the example method.</returns>
    public int ExampleMethod(int exampleParameter)
    {
        int exampleVariable = 42;

        return exampleParameter + exampleVariable;
    }
}
```

### Exception Handling

Use exception handling to handle unexpected errors and exceptions in a graceful way. Use try-catch blocks to catch and handle exceptions that may occur during program execution. Here's an example:

```plaintext
/// <summary>
/// Example method.
/// </summary>
/// <param name="exampleParameter">The example parameter.</param>
public void ExampleMethod(int exampleParameter)
{
    try
    {
        // Do something that may throw an exception
    }
    catch (Exception ex)
    {
        // Handle the exception
    }
}
```

### Single Return Statements

Avoid using multiple return statements in a function. Multiple return statements in a function can make it difficult to understand the flow of execution. Instead, use a single return statement at the end of the function. Here's an example:

```plaintext
/// <summary>
/// Example method.
/// </summary>
/// <param name="exampleParameter">The example parameter.</param>
/// <returns>The result of the example method.</returns>
public bool ExampleMethod(int exampleParameter)
{
    bool result = false;

    if (exampleParameter > 0)
    {
        result = true;
    }

    return result;
}
```

### **SOLID Principles**

Follow the SOLID principles to write maintainable, scalable, and extensible code. The SOLID principles are a set of principles that promote good object-oriented design. Here's an example:

```plaintext
// Single Responsibility Principle
// A class should have only one reason to change
/// <summary>
/// Example class.
/// </summary>
public class ExampleClass
{
    /// <summary>
    /// Example method A.
    /// </summary>
    public void MethodA()
    {
        // Do something
    }

    /// <summary>
    /// Example method B.
    /// </summary>
    public void MethodB()
    {
        // Do something else
    }
}

// Open/Closed Principle
// A class should be open for extension but closed for modification
/// <summary>
/// Example class.
/// </summary>
public abstract class ExampleClass
{
    /// <summary>
    /// Example method.
    /// </summary>
    public abstract void MethodA();
}

/// <summary>
/// Example class extended.
/// </summary>
public class ExampleClassExtended : ExampleClass
{
    /// <summary>
    /// Example method.
    /// </summary>
    public override void MethodA()
    {
        // Do something
    }
}

// Liskov Substitution Principle
// Subtypes should be substitutable for their base types
/// <summary>
/// Example class.
/// </summary>
public class ExampleClass
{
    /// <summary>
    /// Example method.
    /// </summary>
    public virtual void MethodA()
    {
        // Do something
    }
}

/// <summary>
/// Example class extended.
/// </summary>
public class ExampleClassExtended : ExampleClass
{
    /// <summary>
    /// Example method.
    /// </summary>
    public override void MethodA()
    {
        // Do something else
    }
}

// Interface Segregation Principle
// Clients should not be forced to depend on methods they do not use
/// <summary>
/// Example interface.
/// </summary>
public interface IExampleInterface
{
    /// <summary>
    /// Example method A.
    /// </summary>
    void MethodA();

    /// <summary>
    /// Example method B.
    /// </summary>
    void MethodB();
}

/// <summary>
/// Example class.
/// </summary>
public class ExampleClass : IExampleInterface
{
    /// <summary>
    /// Example method A.
    /// </summary>
    public void MethodA()
    {
        // Do something
    }

    /// <summary>
    /// Example method B.
    /// </summary>
    public void MethodB()
    {
        // Do something else
    }
}

// Dependency Inversion Principle
// High-level modules should not depend on low-level modules; both should depend on abstractions
/// <summary>
/// Example interface.
/// </summary>
public interface IExampleInterface
{
    /// <summary>
    /// Example method.
    /// </summary>
    void MethodA();
}

/// <summary>
/// Example class.
/// </summary>
public class ExampleClass : IExampleInterface
{
    /// <summary>
    /// Example method.
    /// </summary>
    public void MethodA()
    {
        // Do something
    }
}

/// <summary>
/// Example class wrapper.
/// </summary>
public class ExampleClassWrapper
{
    private readonly IExampleInterface _example;

    /// <summary>
    /// Constructor for the example class wrapper.
    /// </summary>
    /// <param name="example">The example interface.</param>
    public ExampleClassWrapper(IExampleInterface example)
    {
        _example = example;
    }

    /// <summary>
    /// Example method.
    /// </summary>
    public void MethodA()
    {
        _example.MethodA();
    }
}
```

## Project Basic Structure

All .NET projects must follow the same pattern. All projects must use controllers and repositories, and all controllers must only manage sessions and permissions with no business logic code.

Repositories must implement all the business and data access logic with the terms used in this document. All repositories must be injected by DI.

Services must be used to interact with other APIs and systems, they must be injected with DI too.

## Dependency Injection

.NET supports the dependency injection (DI) software design pattern, a technique for achieving Inversion of Control (IoC) between classes and their dependencies.

There are rules for our current programming standards:

*   The context must be defined using EF in the Startup or Program file for Injection.
*   Repositories must be registered as _scoped_ objects.
*   Services must be registered as _singleton_ objects.

For more information, visit [https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-6.0#lifetime-and-registration-options](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-6.0#lifetime-and-registration-options).

## ORMs and Databases

The architect will define the best approach for accessing data in each project. There are two main approaches.

### Entity Framework

The Entity Framework with Code-First and Migrations approach will be used when working with MVPs or small projects.

Using Code First: The developer writes code to specify the model. EF generates the models and mappings at runtime based on the developer’s entity classes and additional model configuration.

Code First Migrations. The Migrations feature lets you change the data model and deploy your changes to production by updating the database schema without dropping and re-creating the database.

This approach will speed up the development time since there won’t be a need for writing SQL queries; EF will manage all of those by translating LINQ queries into SQL.

When using Entity Framework Code First with Migrations, it's important to follow some best practices to ensure that your database schema is correctly generated and updated. Here are some guidelines to follow:

#### EF Identity Models

When working with authentication and authorization in a .NET application, you may use the built-in Identity models that come with Entity Framework. These models include classes such as **IdentityUser**, **IdentityRole**, and **IdentityDbContext**. When using these models, it's important to follow some best practices to ensure that your application is secure and scalable:

*   Do not use the built-in **IdentityUser** and **IdentityRole** classes directly. Instead, create your own derived classes that add any fields or relationships you need.
*   Use a separate database schema or database for your authentication and authorization data. This can help isolate this data from your main application data and simplify database migrations.
*   Use secure password storage techniques, such as salting and hashing, to store user passwords. The built-in Identity system in Entity Framework already handles this for you, but it's important to understand the underlying security principles.

Here's an example of a custom **ApplicationUser** class that derives from **IdentityUser**:

```plaintext
public class ApplicationUser : IdentityUser
{
    // Add any additional fields or relationships here
}
```

#### Keys of Type Guid

In Entity Framework, it's recommended to use **Guid** keys instead of integer keys. This is because integer keys can cause issues with data synchronization in distributed systems, while **Guid** keys are universally unique and can help avoid these issues. Additionally, **Guid** keys are ideal for cases where you need to generate keys on the client-side before sending data to the server.

When creating entities with **Guid** keys, you can use the **\[Key\]** attribute to specify that the property should be used as the key:

```plaintext
public class ExampleEntity
{
    [Key]
    public Guid Id { get; set; }

    // Add any additional properties or relationships here
}
```

#### Auto-Generated Keys

In Entity Framework, you can use auto-generated keys by using the **DatabaseGenerated** attribute. This allows the database to automatically generate a key value when a new record is inserted into the table. When using auto-generated keys, it's important to ensure that the key is unique and that there are no collisions with existing keys.

Here's an example of an entity with an auto-generated key:

```plaintext
public class ExampleEntity
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public int Id { get; set; }

    // Add any additional properties or relationships here
}
```

#### Circular Cascade Delete Rules

When using Entity Framework, you can specify cascade delete rules for relationships between entities. This means that when an entity is deleted, any related entities will also be deleted. However, it's important to avoid circular dependencies when using cascade delete rules. This can occur when two entities have a bidirectional relationship with cascade delete rules, leading to infinite loops when trying to delete entities.

To avoid circular dependencies, you can use Fluent API to specify the cascade delete rules instead of using the **\[ForeignKey\]** attribute. Here's an example of how to specify cascade delete rules using Fluent API:

```plaintext
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.Entity<ParentEntity>()
        .HasMany(p => p.ChildEntities)
        .WithOne(c => c.ParentEntity)
        .OnDelete(DeleteBehavior.Restrict);

    modelBuilder.Entity<ChildEntity>()
        .HasOne(c => c.ParentEntity)
        .WithMany(p => p.ChildEntities)
        .OnDelete(DeleteBehavior.Cascade);
}
```

In the example above, the **ParentEntity** has a one-to-many relationship with **ChildEntity**, with the **ChildEntity** having a reference back to the **ParentEntity**. The **ParentEntity** has a cascade delete rule, but the **ChildEntity** does not. Instead, the **ChildEntity** has a restrict delete rule, meaning it cannot be deleted if it has any related **ParentEntity** records.

### SQL

In projects with data and complex queries where the information is essential for the proper functioning of the application, the SQL approach will be used.

There will be a SQL project inside the repos of the application where all the schema changes will be made.

For data changes, there will be a need for a shared folder in SharePoint to save the SQL queries for data loading or transformations if needed for a release.

#### SQL Stored Procedures and Entity Framework

SQL Stored Procedures can be used to improve the performance and security of database operations in a .NET application. By encapsulating complex SQL queries or data manipulation logic in a stored procedure, you can simplify your code and reduce the risk of SQL injection attacks.

Entity Framework Code First with Migrations provides an easy way to create and manage stored procedures. Here's how to create a migration to create a stored procedure inside the database and how to call it from the repository:

1.  Create a new migration using the **Add-Migration** command in the Package Manager Console:

```plaintext
Add-Migration MyStoredProcedure
```

1.  In the Up method of the migration, use the Sql method to create the stored procedure:

```plaintext
public partial class MyStoredProcedure : Migration
{
    protected override void Up(MigrationBuilder migrationBuilder)
    {
        migrationBuilder.Sql(@"
            CREATE PROCEDURE [dbo].[MyStoredProcedure]
            AS
            BEGIN
                -- SQL query or data manipulation logic here
            END
        ");
    }

    protected override void Down(MigrationBuilder migrationBuilder)
    {
        migrationBuilder.Sql("DROP PROCEDURE [dbo].[MyStoredProcedure]");
    }
}
```

1.  After running the migration to create the stored procedure in the database, you can call it from your repository using the SqlQuery method:

```plaintext
public async Task<MyEntity> GetMyEntityWithStoredProcedure(int id)
{
    var parameters = new object[] { id };
    var result = await _dbContext.Set<MyEntity>()
        .FromSql("EXEC [dbo].[MyStoredProcedure] @id={0}", parameters)
        .FirstOrDefaultAsync();

    return result;
}
```

In the example above, the FromSql method executes the stored procedure and returns the results as a MyEntity object. The @id parameter is passed to the stored procedure as a parameter.

Using stored procedures in your .NET application can improve performance and security while simplifying your code. By using Entity Framework Code First with Migrations, you can easily create and manage stored procedures, making it easy to incorporate them into your application.

### Data Access through Repositories

When working with Entity Framework, it's recommended to use the Repository pattern to access data. This pattern allows you to abstract away the details of the data access layer and provides a clear separation of concerns. Additionally, using interfaces for your repositories can simplify dependency injection and make your code more testable.

Here's an example of a repository interface for an **ExampleEntity**:

```plaintext
public interface IExampleRepository
{
    IEnumerable<ExampleEntity> GetAll();
    ExampleEntity GetById(int id);
    void Add(ExampleEntity entity);
    void Update(ExampleEntity entity);
    void Delete(ExampleEntity entity);
}
```

By using this interface, you can create an implementation that uses Entity Framework to access data:

```plaintext
public class ExampleRepository : IExampleRepository
{
    private readonly DbContext _dbContext;

    public ExampleRepository(DbContext dbContext)
    {
        _dbContext = dbContext;
    }

    public async Task<IEnumerable<ExampleEntity>> GetAllAsync(CancellationToken cancellationToken = default)
    {
        return await _dbContext.Set<ExampleEntity>().ToListAsync(cancellationToken);
    }

    public async Task<ExampleEntity> GetByIdAsync(int id, CancellationToken cancellationToken = default)
    {
        return await _dbContext.Set<ExampleEntity>().FindAsync(new object[] { id }, cancellationToken);
    }

    public async Task AddAsync(ExampleEntity entity, CancellationToken cancellationToken = default)
    {
        await _dbContext.Set<ExampleEntity>().AddAsync(entity, cancellationToken);
        await _dbContext.SaveChangesAsync(cancellationToken);
    }

    public async Task UpdateAsync(ExampleEntity entity, CancellationToken cancellationToken = default)
    {
        _dbContext.Entry(entity).State = EntityState.Modified;
        await _dbContext.SaveChangesAsync(cancellationToken);
    }

    public async Task DeleteAsync(ExampleEntity entity, CancellationToken cancellationToken = default)
    {
        _dbContext.Set<ExampleEntity>().Remove(entity);
        await _dbContext.SaveChangesAsync(cancellationToken);
    }
}
```

### Cancellation Tokens

When working with long-running operations, including cancellation tokens as parameters for all methods is important. A cancellation token can be used to cancel the operation if it takes too long or if the user wants to stop it. This can be especially important when working with large datasets or when making calls to external services. You can make your code more responsive and user-friendly by including cancellation tokens as parameters.

### API REST Controllers

When working with API REST Controllers in a .NET application, it's important to follow some best practices to ensure that your API is well-documented and easy to use. Here are some guidelines to follow:

#### XML Comments and Decorators

When creating API endpoints in .NET, it's important to include XML comments and decorators to provide clear and concise documentation for the endpoint. XML comments can describe the endpoint's purpose, provide sample requests and responses, and include any other relevant information. Decorators can be used to specify the HTTP method, response codes, and other metadata that can be used by tools like Swagger to generate documentation automatically.

Here's an example of an API endpoint that includes XML comments and decorators:

```plaintext
/// <summary>
/// Creates a new example entity.
/// </summary>
/// <remarks>
/// Sample request:
/// 
///     POST /api/ExampleEntity
///     {
///     }
/// 
/// </remarks>
/// <param name="request">The example entity to create.</param>
/// <param name="cancellationToken">The cancellation token.</param>
/// <returns>The newly created example entity.</returns>
/// <response code="200">Returns the newly created example entity.</response>
/// <response code="400">Returns if any of the information is missing.</response>
[HttpPost]
[AllowAnonymous]
[Produces("application/json")]
[ProducesResponseType(StatusCodes.Status200OK)]
[ProducesResponseType(StatusCodes.Status400BadRequest)]
public async Task<ActionResult<ExampleEntityResponse>> Post([FromForm] ExampleEntity request, CancellationToken cancellationToken)
{
    if (ModelState.IsValid)
    {
        var response = await _repository.AddAsync(request, cancellationToken);
        return Ok(response);
    }
    return BadRequest(ModelState.ToResponse());
}
```

In the example above, the XML comments provide information about the purpose of the endpoint, sample requests and responses, and the parameters that are expected. The decorators specify the HTTP method, response codes, and other metadata that can be used by tools like Swagger to generate documentation automatically.

By following these guidelines, you can create API endpoints that are well-documented and easy to use, making it easier for other developers to integrate with your application.

### Repositories in API Controllers

When working with API Controllers, using the Repository pattern to access data is recommended, similar to the Entity Framework example in the previous section. This pattern allows you to abstract away the details of the data access layer and provides a clear separation of concerns. Additionally, using interfaces for your repositories can simplify dependency injection and make your code more testable.

### Visual Studio Scaffolding

Visual Studio includes a powerful feature called scaffolding that can quickly generate code for common tasks. One common use case for scaffolding is to generate API Controllers for a .NET application. Scaffolding can save a lot of time and effort when creating new endpoints, and can help ensure that your code is consistent and follows best practices.

Here's how to use scaffolding to generate a new API Controller:

1.  In Visual Studio, right-click on the project in the Solution Explorer and select "Add" > "New Scaffolded Item."
2.  In the "Add Scaffold" dialog, select "API Controller with actions, using Entity Framework" and click "Add."
3.  In the "Add Controller" dialog, select the Entity Framework data context you want to use and the entity you want to generate a controller for.
4.  Click "Add" to generate the new API Controller.

The scaffolding process will generate a new API Controller that includes all actions. The controller will require adding a repository interface, XML comments, and any necessary model classes.
