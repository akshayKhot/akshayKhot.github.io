---
layout: post
title: Difference Between nil, empty, and blank
---

In ruby, you can use the `nil?` method on an instance to check if it's `nil`. However, ruby also provides `empty?` and there's a `blank?` method in Rails. For a new ruby programmer, it can get quite confusing. This post tries to explain which method to use when.

`nil?`
   
   As expected, you can use `nil?` to check if an object is nil. 
   
```ruby
irb(main):001:0> nilObject = nil
=> nil
irb(main):002:0> nilObject.nil?
=> true
irb(main):003:0> data = Hash.new
=> {}
irb(main):004:0> data.nil?
=> false
```
   
`empty?`

   You can use this method on strings, arrays, and hashes. It returns true in the following cases:

   1. String doesn't have any characters, i.e. `str.length == 0`
   2. Array doesn't contain any elements, i.e. `arr.length == 0`
   3. Hash doesn't have any key-value pairs, i.e. `hash.length == 0`

   It's important to note that an object can be empty and not `nil`. For example:

```ruby
irb(main):005:1* names = []
=> []
irb(main):006:0> names.nil?
=> false
irb(main):007:0> names.empty?
=> true
```

   If you try to call `.empty?` on a `nil` object, ruby throws `NoMethodError`. 

```ruby
irb(main):012:0> nilObject.empty?
Traceback (most recent call last):
        4: from /usr/local/opt/ruby/bin/irb:23:in `<main>'
        3: from /usr/local/opt/ruby/bin/irb:23:in `load'
        2: from /usr/local/Cellar/ruby/3.0.0_1/lib/ruby/gems/3.0.0/gems/irb-1.3.0/exe/irb:11:in `<top (required)>'
        1: from (irb):12:in `<main>'
NoMethodError (undefined method `empty?' for nil:NilClass)
```
   
`blank?`

   This is a nice syntactic sugar implemented in Rails. An object is blank if it's nil, false, empty. For example, `nil`,`false`, `''`, `[]`, `{}`are all blank. 

   You can think of `blank?` as a shorthand for the following code.

```ruby
!val || val.empty?
```

   In addition, `.blank?` returns true if a string contains only whitespace characters. 

```ruby
"  ".blank? # true
```

   Rails also provides `present?`, which is the opposite of `blank?` checks if the value is not `blank`. 

Hope that simplifies things a little. 