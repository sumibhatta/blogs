---
layout: post
title: Starting with C#?
subtitle:
cover-img: /assets/img/dotnet.jpg
thumbnail-img: /assets/img/hello_world.jpeg
share-img: /assets/img/hello_world_jpeg
tags: [c#, csharp,.net ]
comments: true
---

### What's Inside 
- **_[What is C#](#what-is-c))_** 
- **_[C# development Stack](#c-development-stack))_** 
- **_[First C# Program](#first-c-program))_** 
- **_[Breaking Everything Apart](#breaking-everything-apart))_** 


### What is C#?   
C# is a general-purpose, object-oriented, high level programming language. The C# programs may contain one or several files with **.cs** extension. These files are compiled by C# compiler **(csc)** to executable code as a result assembly is created. 

### C# development Stack

- Microsoft .NET
- C# specific tools like compiler , linker etc.
- IDE (I am using rider)


### First C# Program
{% highlight csharp linenos %}
namespace ConsoleApp1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("C# is awesome?");
        }
    }
}
{% endhighlight %}   

### Breaking Everything Apart

{: .box-note}
Console.WriteLine("C# is awesome?");

WriteLine is a static method defined in class called Console. 

{: .box-note}
static void Main(string[] args)

C# cannot execute without entry point. Main method is place where our program begins automatically.

{: .box-note}
class Program

Like other methods, Main method also cannot stand on it's own, that's why it is wrapped with ``class Program``.

{: .box-note}
namespace ConsoleApp1

Namespaces exist in C# to avoid **name clashes** in large projects with many classes. So, classes are wrapped within namespace. It is considered bad to have class without a namespace. And for the classes without namespaces, C# assigns anonymous namespace.



#### Next Topic: [Primitive Types and Variables](https://sumibhatta.com.np/blogs/2022-05-16-primitive-types-csharp/)