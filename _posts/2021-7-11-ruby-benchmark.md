---
layout: post
title: "How to Benchmark Ruby Code"
tags: ruby
---

The Benchmark module in the Ruby standard library allows you to measure the performance of your Ruby code. It provides the following methods to measure and report the time. 

`measure`

```ruby
require 'benchmark'

puts Benchmark.measure { 1_00_000 * 45 }

# 0.000009   0.000008   0.000017 (  0.000006)
```

The output indicates the user CPU time, system CPU time, total time, and the elapsed real time in seconds. 

`bm`

Use this method to compare various operations sequentially. 

```ruby
require 'benchmark'

n = 5_000_000
Benchmark.bm(5) do |x|
  x.report("for") { for i in 1..n; a = "1"; end }
  x.report("times") { n.times do   ; a = "1"; end }
  x.report("upto") { 1.upto(n) do ; a = "1"; end }
end

#            user     system      total        real
# for     0.309944   0.001038   0.310982 (  0.311954)
# times   0.323748   0.004644   0.328392 (  0.336111)
# upto    0.332247   0.001191   0.333438 (  0.335128)
```

`bmbm`

This method performs a rehearsal before the real benchmarking starts to eliminate the costs associated with the memory allocation and garbage collection. Here's an example from the 'Programming Ruby' book. I've refactored it slightly. 

```ruby
require 'Benchmark'

DICT = "/usr/share/dict/words"

def read_all
  str = File.read(DICT)
  words = str.scan(/[-\w']+/)
end

def read_lines
  words = []
  File.foreach(DICT) do |line|
    words << line.chomp
  end
end

Benchmark.bmbm(6) do |x|
  x.report("all") { read_all }
  x.report("lines") { read_lines }
end

# Rehearsal ------------------------------------------
# all      0.063806   0.005232   0.069038 (  0.069187)
# lines    0.065963   0.003346   0.069309 (  0.069376)
# --------------------------------- total: 0.138347sec
#
# user     system      total        real
# all      0.048083   0.000751   0.048834 (  0.048901)
# lines    0.075965   0.002674   0.078639 (  0.078782)
```



