---
layout: post
title: Array Shortcuts in Ruby
tags: ruby
---

If you want to create an array of strings or symbols, Ruby provides a couple ofx handy shortcuts. 

`%w`:  word array generator. 

```bash
irb(main):001:0> %w(ruby java python)
=> ["ruby", "java", "python"]
```

`%i`: symbol array generator

```bash
irb(main):004:0> %i(ruby java perl)
=> [:ruby, :java, :perl]
```

Both these methods also support square  `[]` and curly bracktets `{}` along with the round `()` ones. 

In addition, Ruby provides other similar methods to deal with various things. 

| Shortcut | Used For                         |
| -------- | -------------------------------- |
| %r       | regular expression               |
| %q       | multi-line, single-quoted string |
| %Q       | multi-line, double-quoted string |
| %x       | shell command                    |
| %s       | turns `sym` into `:sym`          |
| %        | regular string                   |

