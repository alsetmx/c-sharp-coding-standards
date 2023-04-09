# C# Coding Guidelines

# Revision History

| Date | Version | Description |
| --- | --- | --- |
| 2/2/2021 | 1.0 | Initial Version |
| 5/30/2022 | 2.0 | DI |
| 1/23/2023 | 3.0 | Notion |
|  |  |  |
|  |  |  |
|  |  |  |

# Content

[Revision History](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Introduction](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Internal Documentation Standards](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Summary](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Returns](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Example](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Exception](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[See](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Param](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Inheritdoc](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Coding Standards](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Pascal Case](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Variables and Parameters](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Hungarian notation](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Caps](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Meaningful names](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Abbreviations](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Underscores](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Type names](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Interfaces](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[File Names](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Namespaces](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Alignment and indentation](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Object Declarations](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Enums](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Events](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Exceptions](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Meaningful Error Messages](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Reasonably Sized Functions and Methods](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Dependency Injection](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[ORMs and Databases](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[Entity Framework](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[SQL](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

[API Controller Endpoint Definition](https://www.notion.so/C-Coding-Guidelines-73dde8c2ed214a9bae423c30779cb37b)

# Introduction

ALSET is a company specializing in Information Technology (IT) with extensive experience in providing Enterprise-level IT experience for SMBs and Startups. Our product development process helps reduce risks, lower costs, and lower implementation times.

Well-written software offers many advantages. It will contain fewer bugs and run more efficiently than poorly written programs. Since the software has a life cycle and much of which revolves around maintenance, it will be easier for the original developer(s) and future keepers of the code to maintain and modify the software as needed. This will lead to increased productivity of the developer(s). The overall cost of the software is reduced when the code is developed and maintained according to software standards.

A distinction has been made between standards and guidelines. Standards are rules which programmers are expected to follow. Guidelines can be viewed as suggestions that can help programmers write better software and are optional but highly recommended. The use of standards will be enforced through software peer reviews.

It is important to note that standards are not fixed but will evolve. Developers are encouraged to provide feedback to the contact@alset.com.mx.

This document details the Software Development Standards and Guidelines for C#.

# Internal Documentation Standards

XML documentation comments are a special kind of comment added above the definition of any user-defined type or member. They are unique because the compiler can process them to generate an XML documentation file at compile time. The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.

XML documentation comments use triple forward slashes (///) and an XML formatted comment body. For example:

```csharp
/// <summary>
/// This class does something.
/// </summary>
public class SomeClass
{
}
```

Many tags can be used in the documentation, but we will enumerate those required for our standards. For more information, you can visit [https://docs.microsoft.com/en-us/dotnet/csharp/codedoc](https://docs.microsoft.com/en-us/dotnet/csharp/codedoc)

## Summary

The <summary> tag adds brief information about a type or member. I’ll demonstrate its use by adding it to the Math class definition and the first Add method. Feel free to apply it to the rest of your code.

```csharp
/// <summary>
/// This class does something.
/// </summary>
public class SomeClass
{
}
```

## Returns

The <returns> tag describes the return value of a method declaration. The following example illustrates the <returns> tag on the first Add method. You can do the same on other methods.

```csharp
/// <summary>
/// Adds two integers and returns the result.
/// </summary>
/// <returns>
/// The sum of two integers.
/// </returns>
public static int Add(int a, int b)
{
    // If any parameter is equal to the max value of an integer
    // and the other is greater than zero
    if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
        throw new System.OverflowException();

    return a + b;
}
```

## Example

You use the <example> tag to include an example in your XML documentation. This involves using the child <code> tag.

```csharp
/// <summary>
/// Adds two integers and returns the result.
/// </summary>
/// <returns>
/// The sum of two integers.
/// </returns>
/// <example>
/// <code>
/// int c = Math.Add(4, 5);
/// if (c > 10)
/// {
///     Console.WriteLine(c);
/// }
/// </code>
/// </example>
public static int Add(int a, int b)
{
    // If any parameter is equal to the max value of an integer
    // and the other is greater than zero
    if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
        throw new System.OverflowException();

    return a + b;
}
```

## Exception

The <exception> tag lets your developers know that a method can throw specific exceptions. Looking at your Math library, you can see that both Add methods throw an exception if a particular condition is met. Not so obvious, though, is that the integer Divide method throws as well if the b parameter is zero. Now add exception documentation to this method.

```csharp
/// <summary>
/// Divides a double by another and returns the result.
/// </summary>
/// <returns>
/// The division of two doubles.
/// </returns>
/// <exception cref="System.DivideByZeroException">Thrown when a division by zero occurs.</exception>
public static double Divide(double a, double b)
{
    return a / b;
}
```

## See

The <see> tag lets you create a clickable link to a documentation page for another code element. We’ll create a clickable link between the two Add methods in our following example.

```csharp
/// <summary>
/// Adds two integers and returns the result.
/// </summary>
/// <returns>
/// The sum of two integers.
/// </returns>
/// <example>
/// <code>
/// int c = Math.Add(4, 5);
/// if (c > 10)
/// {
///     Console.WriteLine(c);
/// }
/// </code>
/// </example>
/// <exception cref="System.OverflowException">Thrown when one parameter is max
/// and the other is greater than 0.</exception>
/// See <see cref="Math.Add(double, double)"/> to add doubles.
public static int Add(int a, int b)
{
    if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
        throw new System.OverflowException();

    return a + b;
}
```

## Param

You use the <param> tag to describe a method’s parameters. Here’s an example of the double Add method: The parameter the tag describes is specified in the required name attribute.

```csharp
/// <summary>
/// Adds two doubles and returns the result.
/// </summary>
/// <returns>
/// The sum of two doubles.
/// </returns>
/// <exception cref="System.OverflowException">Thrown when one parameter is max
/// and the other is greater than zero.</exception>
/// See <see cref="Math.Add(int, int)"/> to add integers.
/// <param name="a">A double precision number.</param>
/// <param name="b">A double precision number.</param>
public static double Add(double a, double b)
{
    if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
        throw new System.OverflowException();

    return a + b;
}
```

## Inheritdoc

You can use the <inheritdoc> tag to inherit XML comments from base classes, interfaces, and similar methods. This eliminates unwanted copying and pasting duplicate XML comments and automatically keeps XML comments synchronized.

```csharp
/// <summary>
/// This is the IMath interface.
/// </summary>
public interface IMath
{
}

/// <inheritdoc/>
public class Math : IMath
{
}
```

# Coding Standards

General coding standards pertain to how the developer writes code

| Object Name | Notation | Length | Plural | Prefix | Suffix | Abbreviation | Char Mask | Underscores |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Class name | PascalCase | 128 | No | No | Yes | No | [A-z][0-9] | No |
| Constructor name | PascalCase | 128 | No | No | Yes | No | [A-z][0-9] | No |
| Method name | PascalCase | 128 | Yes | No | No | No | [A-z][0-9] | No |
| Method arguments | camelCase | 128 | Yes | No | No | Yes | [A-z][0-9] | No |
| Local variables | camelCase | 50 | Yes | No | No | Yes | [A-z][0-9] | No |
| Constants name | PascalCase | 50 | No | No | No | No | [A-z][0-9] | No |
| Field name | camelCase | 50 | Yes | No | No | Yes | [A-z][0-9] | Yes |
| Properties name | PascalCase | 50 | Yes | No | No | Yes | [A-z][0-9] | No |
| Delegate name | PascalCase | 128 | No | No | Yes | Yes | [A-z] | No |
| Enum type name | PascalCase | 128 | Yes | No | No | No | [A-z] | No |

## Pascal Case

Do use PascalCasing for **class** names and **method** names. Class names are nouns (phrases) or adjectives.

```csharp
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

## Variables and Parameters

Do use camelCasing for method arguments and local variables

```csharp
public class UserLog
{
  public void Add(LogEvent logEvent)
  {
    int itemCount = logEvent.Items.Count;
    // ...
  }
}
```

## Hungarian notation

Do not use Hungarian notation or any other type of identification in identifiers.

```csharp
// Correct
int counter;
string name;    
// Avoid
int iCounter;
string strName;
```

## Caps

Do not use Screaming Caps for constants or read-only variables.

```csharp
// Correct
public const string ShippingType = "DropShip";
// Avoid
public const string SHIPPINGTYPE = "DropShip";
```

## Meaningful names

Use meaningful names for variables.

```csharp
var seattleCustomers = from customer in customers
  where customer.City == "Seattle" 
  select customer.Name;
```

## Abbreviations

Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp, Uri.

```csharp
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

## Underscores

Do not use Underscores in identifiers. Exception: you can prefix private fields with an underscore

```csharp
// Correct
public DateTime clientAppointment;
public TimeSpan timeLeft;    
// Avoid
public DateTime client_Appointment;
public TimeSpan time_Left; 
// Exception (Class field)
private DateTime _registrationDate;
```

## Type names

Use predefined type names (C# aliases) like int, float, and string for local parameters and member declarations. Try to avoid using .NET Framework names like Int32 and Single. Using implicit type var is recommended.

```csharp
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

## Interfaces

Do prefix interfaces with the letter I. Interface names are nouns (phrases) or adjectives.

```csharp
public interface IShape
{
}
```

## File Names

Do name source files according to their main classes. Exception: file names with partial classes reflect their source or purpose, e.g., designer, generated, etc.

```csharp
// Located in Task.cs
public partial class Task
{
}
// Located in Task.generated.cs
public partial class Task
{
}
```

## Namespaces

Do organize namespaces with a clearly defined structure:

```csharp
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

## Alignment and indentation

Do vertically align curly brackets and indent using tabs

```csharp
// Correct
class Program
{
  static void Main(string[] args)
  {
    //...
  }
}
```

## Object Declarations

Do declare all member variables at the top of a class, with fields at the very top, then properties, then constructors, then public methods, and private methods at last.

```csharp
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

## Enums

Do use singular names for enums. Exception: bit field enums.

```csharp
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

```csharp
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

```csharp
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

```csharp
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

## Events

Do use suffix EventArgs at the creation of the new classes comprising the event information:

```csharp
// Correct
public class BarcodeReadEventArgs : System.EventArgs
{
}
```

Do name event handlers (delegates used as types of events) with the “EventHandler” suffix, as shown in the following example:

```csharp
public delegate void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e);
```

DO use two parameters named sender and e in event handlers. The sender parameter represents the object that raised the event. The sender parameter is typical of a type object, even if it is possible to employ a more specific type.

```csharp
public void ReadBarcodeEventHandler(object sender, ReadBarcodeEventArgs e)
{
  //...
}
```

## Exceptions

Do not throw exceptions unless it is strictly necessary.

```csharp
throw new Exception(“Error”)
```

Do use suffix Exception at the creation of the new classes comprising the exception information:

```csharp
// Correct
public class BarcodeReadException : System.Exception
{
}
```

## Meaningful Error Messages

Error handling is an essential aspect of computer programming. This includes adding the necessary logic to test for and handle errors and making error messages meaningful.

Error messages should be meaningful. When possible, they should indicate the problem, where it occurred, and when.

## Reasonably Sized Functions and Methods

Software modules and methods should not contain a massive number of lines of code. They should be written to perform one specific task. If they become too long, the task can be broken down into subtasks that new routines or methods can handle. A reasonable number of lines of code for a routine or a method is 200. This does not include documentation, either in the function/method header or inline comments.

## Project Basic Structure

All .NET projects must follow the same pattern. All projects must use controllers and repositories, all controllers must only manage sessions and permissions with no business logic code. 

Repositories must implement all the business logic with the terms used in this document, all repositories must be injected by DI.

Services must be used to interact with other APIs and systems, the must be injected with DI too.

## Dependency Injection

ASP.NET Core supports the dependency injection (DI) software design pattern, a technique for achieving Inversion of Control (IoC) between classes and their dependencies.

There are rules for our current programming standards:

Using EF, the context must be defined in the Startup or Program file for Injection.

Repositories must be registered as *scoped* objects.

Services must be registered as *singleton* objects.

For more information, visit [https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-6.0#lifetime-and-registration-options](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-6.0#lifetime-and-registration-options).

## ORMs and Databases

The architect will define the best approach for accessing data in each project. There are two main approaches.

### Entity Framework

When working with MVPs or small projects, the approach will use Entity Framework with Code-First and Migrations approach.

Using Code First: The developer writes code to specify the model. EF generates the models and mappings at runtime based on the developer’s entity classes and additional model configuration.

Code First Migrations. The Migrations feature lets you change the data model and deploy your changes to production by updating the database schema without dropping and re-creating the database.

This approach will speed up the development time since there won’t be a need for writing SQL queries; EF will manage all of those by translating LINQ queries into SQL.

### SQL

In projects with data and complex queries where the information is essential for the proper functioning of the application, the SQL approach will be used.

There will be a SQL project inside the repos of the application where all the schema changes will be made.

For data changes, there will be a need for a shared folder in SharePoint to save the SQL queries for data loading or transformations if needed for a release.

## API Controller Endpoint Definition

API Projects will be documented based on the project documentation following our standards above, usually a well-documented API endpoint would look like this:

```csharp
/// <summary>
/// [Ready] Updates a user role
/// </summary>
/// <remarks>
/// Sample request:
///
///     PUT /api/Users/Role
///     {
///        userId: "2",
///        role: "user"
///     }
///
/// </remarks>
/// <param name="request">GrupMemberDto containing only userId and new role.</param>
/// <param name="cancellationToken">Cancellation Token</param>
/// <returns>Basic Response</returns>
/// <response code="200">Basic Response <c>BasicResponse</c>BasicResponse</response>
/// <response code="400">Basic Response <c>BasicResponse</c>BasicResponse</response>
/// <response code="401">Returns 401 if session is not valid anymore</response>
[HttpPut]
[Route("Role")]
[Produces("application/json")]
[ProducesResponseType(StatusCodes.Status200OK)]
[ProducesResponseType(StatusCodes.Status400BadRequest)]
[ProducesResponseType(StatusCodes.Status401Unauthorized)]
public async Task<IActionResult> UpdateUserRole([FromBody] GroupMemberDto request, CancellationToken cancellationToken)
{
    if (ModelState.IsValid)
    {
        var response = await _repository.UpdateRole(request, cancellationToken);
        return Ok(response);
    }
    return BadRequest(ModelState.ToResponse());
}
```
