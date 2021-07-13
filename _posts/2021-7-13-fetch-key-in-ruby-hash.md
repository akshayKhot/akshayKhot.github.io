---
layout: post
title: "Hash: fetch vs. []"
tags: ruby
---

While reading the source code for one of the Ruby standard library modules, I came across the `fetch` method on a Ruby Hash. Having used only the `[]` syntax so far, I was interested in learning why Ruby provides this alternate method that apparently does the same thing. Here's a brief explanation of the `Hash#fetch` method and when you should use it instead of the `[]`. 

From the [docs](https://ruby-doc.org/core-3.0.1/Hash.html#method-i-fetch), the `fetch` method returns the value for the given key, if found. Otherwise, it returns a `KeyError`. 

```ruby
h = {foo: 0, bar: 1, baz: 2}
=> {:foo=>0, :bar=>1, :baz=>2}
h.fetch(:bar)
=> 1
h.fetch(:temp)

Traceback (most recent call last):
        5: from /usr/local/opt/ruby/bin/irb:23:in `<main>'
        4: from /usr/local/opt/ruby/bin/irb:23:in `load'
        3: from /usr/local/Cellar/ruby/3.0.0_1/lib/ruby/gems/3.0.0/gems/irb-1.3.0/exe/irb:11:in `<top (required)>'
        2: from (irb):38:in `<main>'
        1: from (irb):38:in `fetch'
KeyError (key not found: :temp)
```

You can also specify a default value, if the key is missing. 

```ruby
h = {foo: 0, bar: 1, baz: 2}
h.fetch(:temp, 10)
=> 10
```

If `key` is not found and a block is given, yield the key to the block and return the value returned by the block. 

```ruby
h.fetch(:temp) { |key| "No Key: #{key}" }
=> "No Key: temp"
```

In contrast to the `fetch` method, the `[]` syntax will retrieve the value if the `key` exists, otherwise, it returns `nil`. These two lines of code are equivalent:

```ruby
h = { foo: 10, bar: 20 }

h.fetch(:jam, 50)
=> 50
h[:jam] || 50
=> 50
```

As Jorg Mittag said in [this](https://stackoverflow.com/a/16570069/5192528) answer on Stack Overflow, 

> With [], the creator of the hash controls what happens when a key doesn't exist, with `fecth` you do. 

Hope this was useful. 