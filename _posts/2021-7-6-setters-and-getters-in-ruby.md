---
layout: post
title: Setters and Getters in Ruby
tags: ruby
---

Each class needs a two methods for its properties, one to get the value and another to set the value. Different programming languages have different mechanisms that let you accomplish this. For example, Java has set and get methods, and C# has auto-implemented properties. Let's see how you can do this in Ruby. 

Let's say you have a class named `Company` with two properties for its `name` and `founder`. You can create the class as follows.

```ruby
class Company
  def initialize(name, founder)
    @name = name
    @founder = founder
  end
end
```

If you try to access the properties directly, ruby will throw a `NoMethodError`.

```ruby
microsoft = Company.new("Microsoft", "Bill Gates")

# # undefined method `name' for #<Company:..> (NoMethodError)
puts "#{microsoft.name} - founded by #{microsoft.founder}"
```

This is because the properties `name` and `founder` are not yet visible to the code outside the class `Company`. To allow the external code to access them, you would need to write two methods for each property. 

```ruby
class Company
  def initialize(name, founder)
    @name = name
    @founder = founder
  end
  
  def name
    @name
  end
  
  def founder
    @founder
  end
end

microsoft = Company.new("Microsoft", "Bill Gates")

# Microsoft - founded by Bill Gates
puts "#{microsoft.name} - founded by #{microsoft.founder}"
```

This takes care of reading the value of the properties. What if you want to change the name of the company, or the founder? The following code doesn't work. 

```ruby
# undefined method `founder=' for #<Company:...> (NoMethodError)
microsoft.founder = "Satya Nadella"
```

Ruby is complaining that our class is missing a method named `founder=`. Let's add the missing setter methods for `name` and  `founder`. 

```ruby
class Company
  def initialize(name, founder)
    @name = name
    @founder = founder
  end
  
  def name
    @name
  end
  
  def name=(new_name)
    @name = new_name
  end
  
  def founder
    @founder
  end
  
  def founder=(new_founder)
    @founder = new_founder
  end 
end

microsoft = Company.new("Microsoft", "Bill Gates")
microsoft.founder = "Satya Nadella"

# Microsoft - founded by Satya Nadella
puts "#{microsoft.name} - founded by #{microsoft.founder}"
```

Now any external code can read and modify the properties on the `Company` class. This approach is quite similar to Java. However, it results in quite verbose code, if your class has many properties. For each property, you'll need to write two methods, one to read, another to write. 

Ruby provides an alternate syntax that lets you skip all the boilerplate code. You can get rid of all four methods from our class by simply calling `attr_accessor` method, which generates these methods for you. 

```ruby
class Company
  attr_accessor :name, :founder
  
  def initialize(name, founder)
    @name = name
    @founder = founder
  end
end

microsoft = Company.new("Microsoft", "Bill Gates")
microsoft.founder = "Satya Nadella"

# Microsoft - founded by Satya Nadella
puts "#{microsoft.name} - founded by #{microsoft.founder}"
```

If you don't want the external code to modify the value of your properties, you can use `attr_reader` method. There's also `attr_writer`, that only allows modification, but not retrieval of the value. 

``` ruby
class Company
  attr_reader :name, :founder
  
  def initialize(name, founder)
    @name = name
    @founder = founder
  end
end
```

If you are coming from a more traditional language like Java or C#, the syntax for `attr_*` methods might look strange to you. However, it's not a special syntax, but simply a method call in ruby. 

The `attr_accessor` is a method defined on the `Company` class, and you are passing the names of the properties to that method as symbols. Ruby allows you to skip the braces on a method call, which results in the above pretty-looking code. 

It's important to understand that the `class` is not a definition in ruby, unlike the classes in other languages, but an expression that evaluates. Ruby is actually running and evaluating the code in the class as it parses it from the file. It is during this evaluation when the `attr_accessor` and the other methods are called. These methods in turn modify the class by adding the getter and setter methods for the properties. 

Hope this helps. 





