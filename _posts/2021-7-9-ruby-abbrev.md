---
layout: post
title: "Ruby Standard Library: Abbrev"
tags: ruby
---

This post explores the `Abbrev` module that ships with the Ruby standard library. We take a look at what this module does and how it works. Then we take a look behind the hood and see how it's implemented. 

**What is Abbrev?**

This module helps you find out all the possible abbreviations for one or more strings so that there are no duplicate abbreviations. 

Input: A set of words, such as `[ruby, rust]`

Output: A hash consisting of unambiguous abbreviations for the above string.  

```ruby
irb(main):001:0> require 'abbrev'
=> true
irb(main):002:0> Abbrev.abbrev(['ruby', 'rust'])
=> {"ruby"=>"ruby", "rub"=>"ruby", "rust"=>"rust", "rus"=>"rust"}
```

Note the resulting hash omitted `ru` as a key as it would be confusing to find which word it refers to, `ruby` or `rust`.

It also works as an array extension, i.e. it adds an `abbrev` method to the `Array` class. This lets you call the `abbrev` method directly on an array. 

```ruby
irb(main):003:0> %w(ruby rust).abbrev
=> {"ruby"=>"ruby", "rub"=>"ruby", "rust"=>"rust", "rus"=>"rust"}
```

**When do I use it?**

Let's say your program has a set of commands. But you also want to allow the users of your program to type as few keys as possible when entering the commands. For example, to execute a `generate` command, the users could type `gen` or even `g`, and your program should work as expected. 

However, let's say you have a `generic` command, then you shouldn't allow the users to type `gen`, as that would be ambiguous. In this case, use the `Abbrev` module to get the non-conflicting abbreviations for your commands. 

Here is a code example from the book **Programming Ruby** that demonstrates this feature. 

```ruby
require 'abbrev'

COMMANDS = %w{ sample send start status stp }.abbrev

while line = gets
  line = line.chomp

  case COMMANDS[line]
  when "sample" then
    puts "Executing sample command"
  when "send" then
    puts "Executing send command"
  when "start" then
    puts "Executing start command"
  when "status" then
    puts "Executing status command"
  when "stp" then
    puts "Executing stp command"
  else
    STDERR.puts "Unknown command: #{line}"
  end
end

# Output
sa
Executing sample command
st
Unknown command: st
sta
Unknown command: sta
star
Executing start command
```

**How does it work?**

Here is a simple version of the code implemented in the standard library, in the `lib/abbrev.rb` directory. It ignores the optional pattern parameter, which can be a string or a regex. It includes only strings that match the pattern or start with the string. 

```ruby
module Abbr

  def Abbr.abbr(words)
    table = {}
    seen = Hash.new(0)

    words.each do |word|
      next if word.empty?
      word.size.downto(1) do |len|
        abbrev = word[0...len]

        case seen[abbrev] += 1
        when 1
          table[abbrev] = word
        when 2  # found duplicate abbreviation
          table.delete(abbrev)
        else  # no need to go further
          break
        end
      end
    end

    words.each do |word|
      table[word] = word
    end

    table
  end
end
```

Hope this helps. 