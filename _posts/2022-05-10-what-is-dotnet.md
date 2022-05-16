---
layout: post
title: What is .NET?
subtitle: (.NET Framework, .NET Core,.NET 5)?
cover-img: /assets/img/dotnet.jpg
thumbnail-img: /assets/img/netthumb.jpg
share-img: /assets/img/netthumb.jpg
tags: [.net, .netframework, .netcore,.net5, .net6 ]
comments: true
---

### What's inside...
- **_[What is dotnet?](#what-is-net)_**  
- **_[Different types of dotnet (.NET Framework, .NET Core, .NET 5)](#different-types-of-nets)_**    
- **_[Some Terms](#some-keywords)_**   
- **_[Similarities and Differences](#similarities-and-differences-between-different-runtimes)_**  
- **_[What to use?](#what-to-use)_**  

### What is .NET?   
These days application developed in .NET runs everywhere . From Cloud and Web, Linux, Windows, macOS, mobile devices and iot devices too. .NET is a little of catch-all term. Some people mean it as a framework or the entire ecosystem(from compiler to runtimes to application people write). Moreover it could also have other meaning. To understand it we have to learn more about it.

### Different Types of .NETs
 
**.NET Framework** is the oldest of all .NET runtimes. It is a SDK(Software Development Kit) with all accompanying classes and APIs. Since all the API were tied to Windows OS, MS no longer recommends it.   


**.NET Core** is a cross platform runtime, which works on Linux, Windows and MacOS. Latest .NET Core Version is .NET Core 3.0 and there won't be technically new versions of .NET Core.

**.NET 5** and **.NET 6** are the newest .NET runtimes. Technically it is versions of .NET Core but much more.

**[Mono](https://www.mono-project.com/)** is a software platform designed to allow developers to easily create cross platform applications part of the .NET Foundation. Sponsored by Microsoft, Mono is an open source implementation of Microsoft's .NET Framework based on the ECMA standards for C# and the Common Language Runtime.

**.NET Standard** is an API specification rather than a SDK. i.e it is a blueprint of what API needs to be present for something to call itself compatible with .NET Standard. We can say that it specifies what BCL must be implemented for a given version.

**ASP.NET** is an active server pages bought to .NET.

**ASP.NET Core** is a way to create webapp with .NET Core.

### Some Keywords

**[CLR](http://vb.net-informations.com/framework/common_language_runtime.htm)** 
CLR is the heart of .NET Platform, an interface between OS and applications written in .net. It is an environment that controls the execution of mananged code and ensures the execution of .NET programs on different hardware platforms and OS.

It is an abstract computing machine. Similar to physical computers, it supports a set of instructions, registers, memory access and I/O operation.


**BCL** Base Class Library is a set of classes provided bt .NET to build applications. It is essentially a collection of multiple libraries that provides various features such as Collections, XML, I/0, data type definitions for multiple programming languages.

**JIT** Just in Time Compiler converts IL( Intermediate Language) to native code on demand.

**IL:** After compiling source code turns into IL. It is bundled into assembly known as IL(Intermediate Language). CLR then runs assembly.

### Similarities and Differences between different runtimes

**Similarities**
- Have Runtime to interact with Host OS
- Use BCL to write applications
- Code Compiled into IL

**Differences**
- Less base class library in .NET Core than in .Net Framework

### What to Use?

.NET 5 and above:
- Unites all .NET implementations
- Has One Common Language Library
- One Set of Base Class Libraries

It is recommended to use .Net 5 or anything new. It's not that .net framework won't work, it is still supported but new technologies will be built upon newer versions so, preferably it is good to use .NET 5 or newer versions.

