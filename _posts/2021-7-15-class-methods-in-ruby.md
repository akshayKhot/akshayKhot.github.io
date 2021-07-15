---
layout: post
title: Class (Static) Methods in Ruby
tags: ruby
---

As an Enterprise C# developer venturing into Ruby, one of the first questions I had was how do I create static methods on a class, as Ruby doesn't have a `static` keyword. Instead, it provides quite a few different ways to create static (class) methods. 

Let's assume you have a class `Person` as follows. 

```ruby
class Person
  
  def initialize(name)
    @name = name
  end
  
  def greet
    puts "Hello, I am #{@name}"
  end
end

akshay = Person.new("Akshay")
akshay.greet    # Hello, I am Akshay
```

Here are a few ways to add a method named `talk` on the `Person` class, instead of its instances. 

`class << self`

The syntax `class << self` opens up `self`'s class. This allows you to add methods on the class. 

```ruby
class Person
  
  class << self
    def talk
      puts "Person can talk"
    end
  end
  
  # rest of the code
end

Person.talk   # Person can talk
```

`self.method`

Instead of opening the `self` class, you can directly define the method on `self`, as follows:

```ruby
class Person
  
  def self.talk
    puts "Person can talk"
  end
  
  # rest of the code
end

Person.talk   # Person can talk
```

`Class.method`

Finally, you can simply use the class name, i.e. `Person`, and define a method on it outside the class. 

```ruby 
class Person
  
  # rest of the code
end

def Person.talk
  puts "Person can talk"
end

Person.talk   # Person can talk
```

Personally, I prefer the second one, as it keeps the static method in the context of the class, as well as makes the intent clear. 

Which one do you prefer?