---
layout: post
title: 20 C# Namespaces You Use 80% Time
tags: dotnet c-sharp
---

.NET contains a lot of namespaces and many more, if you include the third-party libraries. However, there are a few that you will use over and over. Here are the twenty that will get you through 80% of the common, recurring programming problems. 

**System**

Contains the most fundamental types. These include commonly used classes, structures, enums, events, interfaces, etc. 

**System.Text**

Contains classes that represent ASCII and Unicode character encodings. Classes for converting blocks of characters to and from blocks of bytes. 

**System.Text.RegularExpressions**

Provides regular expression functionality. 

**System.Linq**

Provides classes and interfaces that support queries that use Language-Integrated Query (LINQ).

**System.XML.Linq**

Contains the classes for LINQ to XML. LINQ to XML is an in-memory XML programming interface that enables you to modify XML documents efficiently and easily.

**System.XML**

Provides support for processing XML.

**System.XML.Serialization**

Contains classes that are used to serialize objects into XML format documents or streams.

**System.Text.Json**

Provides high-performance, low-allocating, and standards-compliant capabilities to process JavaScript Object Notation (JSON), which includes serializing objects to JSON text and deserializing JSON text to objects, with UTF-8 support built-in. 

**System.Diagnostics**

Provides classes that allow you to interact with system processes, event logs, and performance counters.

**System.Threading**

Provides classes and interfaces that enable multithreaded programming. In addition to classes for synchronizing thread activities and access to data ([Mutex](https://docs.microsoft.com/en-us/dotnet/api/system.threading.mutex?view=net-5.0), [Monitor](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor?view=net-5.0), [Interlocked](https://docs.microsoft.com/en-us/dotnet/api/system.threading.interlocked?view=net-5.0), [AutoResetEvent](https://docs.microsoft.com/en-us/dotnet/api/system.threading.autoresetevent?view=net-5.0), and so on), this namespace includes a [ThreadPool](https://docs.microsoft.com/en-us/dotnet/api/system.threading.threadpool?view=net-5.0) class that allows you to use a pool of system-supplied threads, and a [Timer](https://docs.microsoft.com/en-us/dotnet/api/system.threading.timer?view=net-5.0) class that executes callback methods on thread pool threads.

**System.Threading.Tasks**

Provides types that simplify the work of writing concurrent and asynchronous code. The main types are [Task](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task?view=net-5.0) which represents an asynchronous operation that can be waited on and cancelled, and [Task](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task-1?view=net-5.0), which is a task that can return a value. The [TaskFactory](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.taskfactory?view=net-5.0) class provides static methods for creating and starting tasks, and the [TaskScheduler](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.taskscheduler?view=net-5.0) class provides the default thread scheduling infrastructure.

**System.IO**

Contains types that allow reading and writing to files and data streams, and types that provide basic file and directory support.

**System.Net**

Provides a simple programming interface for many of the protocols used on networks today.

**System.Net.Http**

Provides a programming interface for modern HTTP applications.

**System.Net.Mail**

Contains classes used to send electronic mail to a Simple Mail Transfer Protocol (SMTP) server for delivery.

**System.Net.Sockets**

Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to tightly control access to the network.

**System.Reflection**

Contains types that retrieve information about assemblies, modules, members, parameters, and other entities in managed code by examining their metadata.

**System.Security**

Provides the underlying structure of the common language runtime security system, including base classes for permissions.

**System.Security.Cryptography**

Provides cryptographic services, including secure encoding and decoding of data, as well as many other operations, such as hashing, random number generation, and message authentication. 

**System.Dynamic**

Provides the support for dynamic programming. 