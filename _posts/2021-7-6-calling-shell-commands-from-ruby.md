---
layout: post
title: Calling Shell Commands From Ruby
tags: ruby
---

Frequently we want to run shell commands or interact with the operating system from the programming language. Here're a few different ways to run shell commands from Ruby. Which one do you prefer?

`command` (backticks)

```ruby
irb(main):001:0> puts `ls`
cookbook
design_patterns
features
files
main.rb
projects
test
tests
```

`%x(cmd)`

```ruby
irb(main):004:0> %x(echo 'hi')
=> "hi\n"
```

`Kernel#system`

   This command executes the given command in a sub-shell, returning `true` for successful commands; `false` otherwise. 

```ruby
irb(main):006:0> system('ls')
cookbook	features	main.rb		test
design_patterns	files		projects	tests
```

`Kernel#exec`

   This command replaces the current process by running the provided shell command. It doesn't return, instead replacing the current process. 

```ruby
irb(main):007:0> exec('ls')
cookbook	features	main.rb		test
design_patterns	files		projects	tests
➜
```
Note the arrow at the end of the following example, the current `irb` session was terminated after executing the command. 