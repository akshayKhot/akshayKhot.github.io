---
layout: post
title: Programming by Coincidence
tags: programming cityview
---

I spent many hours this week banging my head to parse a simple XML document. It was a real struggle to get anything done. According to pragmatic programmers, I was [programming by coincidence](https://pragprog.com/the-pragmatic-programmer/extracts/coincidence), without any clear plan, just hoping to get the code working somehow and failing.

> The weary soldier advances cautiously out of the brush. There’s a clearing ahead: are there any land mines, or is it safe to cross? There aren’t any indications that it’s a minefield—no signs, barbed wire, or craters. The soldier pokes the ground ahead of him with his bayonet and winces, expecting an explosion. There isn’t one. So he proceeds painstakingly through the field for a while, prodding and poking as he goes. Eventually, convinced that the field is safe, he straightens up and marches proudly forward, only to be blown to pieces.
>
> The soldier’s initial probes for mines revealed nothing, but this was merely lucky. He was led to a false conclusion—with disastrous results.
>
> As developers, we also work in minefields. There are hundreds of traps just waiting to catch us each day. Remembering the soldier’s tale, we should be wary of drawing false conclusions. We should avoid programming by coincidence—relying on luck and accidental successes—in favor of programming deliberately.


Yes, I was that soldier. Finally, after confronting my ignorance and admitting my complete lack of understanding of how XML works, I decided to do a deep dive into this topic. As always, I found a few good courses on PluralSight and started with [Linq to XML](https://app.pluralsight.com/library/courses/linq-fundamentals-csharp-6/table-of-contents) by K Scott Allen. The course taught me everything I needed to know about XML and much more in just under 30 minutes.

It was mindblowing. At work this morning, I was able to crank out beautiful C# code using Linq to get it done exactly what I wanted with the XML. Linq-to-XML is like a genie. You wish for what you want to do with the XML, and it does it for you. All I needed to do was understand a few basic concepts and classes in the System.XML.Linq namespace.

According to the [docs](https://docs.microsoft.com/en-us/dotnet/api/system.XML.linq?view=netframework-4.7.2),

> Linq-to-XML is an in-memory XML programming interface that enables you to modify XML documents efficiently and easily.

So true.

**Here are a few of the essential classes we need:**

1. XDocument: This represents the XML document. It derives from XContainer and hence can contain child nodes. However, it can have only one child node to follow the XML standard that there can be only one root element in an XML document.
2. XElement: Represents an XML element. It is one of the fundamental classes in Linq-to-XML. We can use this class to create/read/modify/delete the XML elements, add attributes to existing elements, and much more.
3. XAttribute: Represents an XML attribute, which is simply a name-value pair associated with an XML element.
4. XNamespace: Represents an XML namespace. The most common way to create its object is to assign a string to it.

There are additional classes in the namespace. However, these four classes were enough for all my practical purposes. Let’s see how to use them.

**Creating XML**

```c#
public static void CreateXML()
{
    var doc = new XDocument();
    XNamespace ns = "https://www.akshaykhot.com";

    var friends = new XElement(ns + "Friends");
    
    var bandya = new XElement(ns + "Friend",
        new XAttribute("Name", "Akshay Darade"),
        new XAttribute("From", "School")
        );
    var abhiyash = new XElement(ns + "Friend",
        new XAttribute("Name", "Abhiyash Jain"),
        new XAttribute("From", "College")
        );
    var kunal = new XElement(ns + "Friend",
        new XAttribute("Name", "Kunal Veera"),
        new XAttribute("From", "Building")
        );
    
    friends.Add(bandya, abhiyash, kunal);
    doc.Add(friends);
    doc.Save("friends.XML");
}
```

To generate this beautiful XML:

```xml
<?XML version="1.0" encoding="utf-8"?>
<Friends XMLns="https://www.akshaykhot.com">
  <Friend Name="Akshay Darade" From="School" />
  <Friend Name="Abhiyash Jain" From="College" />
  <Friend Name="Kunal Veera" From="Building" />
</Friends>
```

I think the C# code is as much, if not more, readable as the XML.

**Parsing XML**

```c#
public static void QueryXML()
{
    XDocument doc = XDocument.Load("friends.XML");
    XNamespace ns = "https://www.akshaykhot.com";
    
    // find all school frinds
    var schoolFriends = doc.Element(ns + "Friends")
                           .Elements(ns + "Friend")
                           .Where(friend => friend
                                            .Attribute("From")
                                            .Value.Equals("School"));

    foreach (XElement friend in schoolFriends)
    {
        Console.WriteLine(friend.Attribute("Name").Value);
    }
  
}
```

There is a gotcha in the above code, and I got burned by it. If you are not careful, and one of the friends doesn’t have an attribute **From**, it will throw the infamous object reference not set to an instance of an object exception.

To get around this, it’s better to create a common utility method, which you can use any time you want to read the elements' attributes.

```c#
private string GetAttribute(XElement element, string attributeName)
{
    string value = string.Empty;
    XAttribute attr = element.Attribute(attributeName);

    if (attr != null)
        value = attr.Value;

    return value;
}
```

The code looks cleaner and is much more concise than the traditional .net XML manipulation libraries. I replaced most of the spaghetti code that I wrote during the week with lesser and more powerful code.

It's good to learn a new skill that helps you solve the problems you are facing, and it just feels so damn good. Today was one of the happiest days at work for me than the frustrating week I had so far.

**Here are some of the lessons learned:**

1. Always be aware of what you are doing.
2. Don’t code blindfolded.
3. Have a plan before you start programming.
4. If you don’t know why your code works, you won’t understand why it fails, which it will.