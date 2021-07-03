---
layout: post
title: How to Write a Switch Statement in Ruby
tags: ruby
---

Ruby doesn't have a switch statement, unlike other programming languages. Instead, there's the `case` expression, which is much versatile and powerful than a `switch`.  

A `case` expression in ruby consists of three parts. 

1. `case`: The variable we are going to match. 
2. `when`: A condition to match.
3. `else`: The default choice. 

```ruby
size = 10

case size
when 0
  puts "Small size"
when 10
  puts "Medium size"
when 20
  puts "Large size"
else
  puts "Invalid size"
end
```

Because `case` is a statement, you can assign its value to a variable. 

```ruby
size = 10

message = case size
          when 0
            "Small size"
          when 10
            "Medium size"
          when 20
            "Large size"
          else
            "Invalid size"
          end

puts message  # Medium size
```

It's also possible to match ruby symbols in a `case` statement. 

```ruby
size = :small

message = case size
          when :small
            "Small size"
          when :medium
            "Medium size"
          when :large
            "Large size"
          else
            "Invalid size"
          end

puts message  # Small size
```

In a `case` expression, ruby compares the value in the `when` clause with the value in the `case` clause using the `===` operator. The order of comparison is important. In the above example, ruby compares `:small === size`, not `size === :small`. 

You might wonder what difference the order would make, but this allows ruby to do pretty sophisticated comparisons using Ranges, classes, regular expressions, etc. Let's consider an example that illustrates this. 

Ruby defines the `===` operator such that it returns `true` when you use it with a class as the first operand and the instance as the second operand. That is, `String === ""` returns true, however `"" === String` returns false. This allows us to use a `case` statement to figure out the type of a variable, as follows:

```ruby
obj = 10

case obj
when String
  puts "It's a string"
when Fixnum
  puts "It's a number"
else
  puts "It's neither a string nor a number"
end

# It's a number
```

You can also match multiple values separated by a comma in a single `when`. In a `case` statement, a comma `,` is equivalent to `||` in an `if` statement. 

```ruby
val = 3

case val
when 1, 4, 9
  puts "It's a square"
when 2, 3, 5, 6, 7, 8
  puts "Not a square"
end

# Not a square
```

Here's a pretty sophisticated [example](http://ruby-doc.com/docs/ProgrammingRuby/html/tut_expressions.html#S5) from Dave Thomas's classic book "Programming Ruby" that shows the power of ruby's `case` expression. 

```ruby
case inputLine

when "debug"
  dumpDebugInfo
  dumpSymbols

when /p\s+(\w+)/
  dumpVariable($1)

when "quit", "exit"
  exit

else
  print "Illegal command: #{inputLine}"
end
```

An important difference with the `switch` statement in other languages is that `case` doesn't have a fall-through, so you don't need to use a `break` statement after the end of each block. 