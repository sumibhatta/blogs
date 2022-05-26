---
layout: post
title: Basics in C#
subtitle:
cover-img: /assets/img/dotnet.jpg
thumbnail-img: /assets/img/hello_world.jpeg
share-img: /assets/img/hello_world_jpeg
tags: [c#, csharp,.net ]
comments: true
---

### Topics Covered:
- [Syntax](#syntax)
- [C# Grammar](#c-grammar)
- [Vocabulary](#vocabulary)
- [Methods are Verbs](#methods-are-verbs)
- [Variables, Fields and Properties](#types-variables-fields-and-properties)
- [Data Types](#data-types)
- [Identifiers](#identifiers)
- [Data Types](#data-types)
- [Classes and Methods](#classes-and-methods)

### Syntax
It is a set of rules on how to make a running program in that language. 

{% highlight csharp linenos %}
Console.WriteLine("C# is awesome");
{% endhighlight %} 


### C# Grammar
C# grammar includes: 
- Statements
- Blocks

#### Statements
Like a __Sentence__ ends with fullstop.
C# Statement ends with __semicolon__;
An Statement consists of multiple variables and expressions.
Example:
```csharp
Console.WriteLine(Environment.CurrentDirectory);
```

#### Blocks
Like a __paragraph__ starting with new line.
A block of code is indicated with __curly braces {}__
Block Starts with : deceleration followed by curly braces.

Example:
- namespaces
- classes
- loops
- methods


```csharp
using System;

class Foo
{
    void Main()
    {
        Console.WriteLine(Environment.Version);
    }
}
```
### Vocabulary
C# vocabulary consists of:
- Keywords
- Symbols
- Characters
- Types

```csharp
int implicitVariable = 1997;
var explicitVariable = 1997;
```
### Methods are Verbs
Verb are action words like eat and sleep.
In C# method is action words.

```csharp
// 3 versions of WriteLine
Console.WriteLine();
Console.WriteLine("version 1");
Console.WriteLine($"{2:D} days left");
```

### Types, Variables, Fields and Properties

#### Type

It is used to categorize things.
Every Type can be categorized as class, struct, enum, interface and delegate.
Example: Animal

#### Field
These are the properties.
Example: Head of animal

#### Variables
Noun refering to specific object.
Example: Lucy name of dog.

A variable can either be defined by specifying their type:
- Implicitly
- Explicitly


### Literals
__literal__ is a chunk of code that is literally or precisely is as it is written.
Example of String Literal: **"C# is awesome"**

### Identifiers
__Identifier__ allows us to reference to something existing in the code element.
Example: ``Console`` and ``Writeline``



### Data Types:
Set of values with similar characteristics.
Characteristics:
- Name
- Size
- Default Value

### [Types](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types):
- Integer (**sbyte**, **short**, **int**, **long** | **byte**, **ushort**, **uint**, **ulong** | **nint**, **nuint**)  
- Real floating-point (**float**, **double**)
- Real type with decimal precision (**decimal**)
- Boolean (**bool**)
- Character  (**char**)
- String (**string**)
- Object (**object**)
- Dynamic (**dynamic**)

```csharp
//numbers
int x = 100;
var y = 200.0011f;
decimal z = 300;

//Observing the size and ranges
Console.WriteLine($"int uses {sizeof(int)} bytes and can store the values from {int.MinValue:N0} to {int.MaxValue:N0}.");

//double trouble
double numOne = 1.1;
double numTwo = 2.2;

if(numOne+numTwo == 3.3)
{
    Console.WriteLine($"{numOne} + {numTwo} equals to 3.3");
}
else
{
    Console.WriteLine($"{numOne} + {numTwo} doesn't equals to 3.3");
}
//For accuracy use decimal rather than double


//bool
var whatDoYouThink = false;

//char
char letter = 'A';

//literal strings
string firstName = "firstName";
Console.WriteLine(letter);

//VERBATIM STRING
 var firstString = "\\\\server\\folder\\file.cs";
 Console.WriteLine("first verbatam string:" + firstString);
 Console.WriteLine(@"\\server\folder\file.cs");
 Console.WriteLine(@"this is a 
multiline
             string");

//Interpolated string
Console.WriteLine($"{letter} {firstName}");
```

{: .box-note}
**Digit Separators:** Underscore character _ can be used as a digit separator. As 1_00_000.



```csharp
//objects are special type of that can store any kind of data [flexible but messier code and poor performance]
object anObject = "himalaya";
// Console.WriteLine($"{anObject} has {anObject.Length} characters");
Console.WriteLine($"{anObject} has {((string)anObject).Length} characters");

//DYNAMIC TYPES - [Flexible than object but comes with the cost of performance]
//dynamic
dynamic life = "tentative";
```

### Classes and Methods
``Class`` keyword is used to define a class and ``new`` is used to instantiate it's objects.
For understanding: Class is like a person in a team. A whole work is divided for each person and they perform the specified task to complete the job.  

{% highlight csharp linenos %}
class ClassName{
    //body
}

new ClassName();
{% endhighlight %} 
 
Classes contains:
- Data 
- Methods (tasks they need to perform)

- Functions within classes is termed as methods
- Methods can have 0 - many parameters passed to it whose type must be **explicitly** defined.
- Values must be returned using ``return`` keyword.
- To be able to be accessed from other files, method must be made ``public``.
- Method are invoked/called using ``.``  


{% highlight csharp linenos %}
namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            ClassAdd twoClass = new();
            Console.WriteLine(twoClass.Add(5, 2));
        }
    }
}
class ClassAdd{
    public int Add(int x, int y)
    {
        return x + y;
    }
}
{% endhighlight %} 
