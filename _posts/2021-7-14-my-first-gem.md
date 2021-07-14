---
layout: post
title: I Published My First Ruby Gem!
tags: ruby
---

Finally, I built my own [gem](https://rubygems.org/gems/algorithm) and published it on RubyGems. In this post, I will share everything I learned about building and sharing gems. For a brief introduction to Ruby gems, please checkout my [previous post](/introduction-to-ruby-gems/). Hope you find it useful. 

There are two ways to create your own gem:
1. Manual (the hard way)
2. Using Bundler (the easy way)

If you haven't created a gem before, I recommend creating one the hard way, i.e. creating all the files and the folder structure manually. Once you understand the role and purpose of each, and why we do it that way, start using Bundler for your future gems. We will start with the hard way first, to understand how Bundler alleviates a lot of boilerplate code for us. 

### The Hard Way

Let's say we would like to create a package to implement all the algorithms from the famous [CLRS](https://mitpress.mit.edu/books/introduction-algorithms) book, because, why not? So here's how we'd go about it. 

**Come up with a good name**

Make sure it's not already taken by doing a search on the [RubyGems.org](https://rubygems.org/) website. 

You can also use the search command from the console, as follows:

```bash
➜  clrs gem search ^clrs$

*** REMOTE GEMS ***

clrs (2.0.2)
```

I wanted to name my gem `clrs`, but I see it's already taken. So let's try `algorithm`, which is available. 

Create a directory for the gem and `cd` into it. 

```bash
➜  my-gems mkdir algorithm && cd algorithm
➜  algorithm
```

Create a file named `algorithm.gemspec` and a `lib` directory containing `algorithm.rb` file. The `lib` directory contains the source code of your gem. 

```shell
➜  algorithm tree
.
├── algorithm.gemspec
└── lib
    └── algorithm.rb

1 directory, 2 files
```

The convention dictates that the `lib` directory should contain a single Ruby file with the same name as the gem, i.e. `algorithm.rb`. 

When the code that uses the gem calls `require 'algorithm'`, the `algorithm.rb` file gets loaded and sets up the gem's code and API. 

Let's add some code to the `algorithm.rb` file. 

```ruby
# lib/algorithm.rb

class Algorithm
  
  def initialize(name)
    @name = name
  end
  
  def run
    puts "Running Algorithm: #{@name}"
  end
end
```

The other file in our directory is the `algorithm.gemspec` file. If you are a Node.js developer, this is the `package.json` file for your package. It specifies what the gem does, who created it,  version, license, and other meta-information about the gem. This is simply a Ruby file, even though the extension is different. 

```ruby
# algorithm.gemspec

Gem::Specification.new do |s|
  s.name      = "algorithm"
  s.version   = "0.0.0"
  s.summary   = "This gem provides the implementation of CLRS algorithms"
  s.authors   = ["Akshay Khot"]
  s.email     = "akshay.khot@hey.com"
  s.files     = ["lib/algorithm.rb"]
  s.homepage  = "https://akshaykhot.com/algorithm"
  s.license   = "MIT"
end
```

The `gemspec` file can also contain many other fields. To view them all, check out the [reference](https://guides.rubygems.org/specification-reference/). 

Once you have the directory structure with the `gemspec` file, run the `gem build` command to create a gem from it. This command will generate a `algorithm-0.0.0.gem` file in the directory. 

```bash
➜  algorithm gem build algorithm.gemspec
  Successfully built RubyGem
  Name: algorithm
  Version: 0.0.0
  File: algorithm-0.0.0.gem
  
➜  algorithm ls
algorithm-0.0.0.gem algorithm.gemspec   lib
```

Next, install the generated gem locally using the `gem install command` so you can test it. 

```bash
➜  algorithm gem install ./algorithm-0.0.0.gem
Successfully installed algorithm-0.0.0
Parsing documentation for algorithm-0.0.0
Installing ri documentation for algorithm-0.0.0
Done installing documentation for algorithm after 0 seconds
1 gem installed
```

Finally, launch `irb` console and run the gem. 

```shell
➜  algorithm irb
require 'algorithm'
=> true
insertion_sort = Algorithm.new("Insertion Sort")
=> #<Algorithm:0x00007fe2fe952c28 @name="Insertion Sort">
insertion_sort.run
Running Algorithm: Insertion Sort
=> nil
irb(main):004:0>
```

Next, we will share the gem to the Ruby community by publishing it on the RubyGems.org website. You need to have an account on RubyGems to publish the gems.

```bash
➜  algorithm gem push algorithm-0.0.0.gem
Enter your RubyGems.org credentials.
Don\'t have an account yet? Create one at https://rubygems.org/sign_up
   Email:   akshay.khot@hey.com
Password:

Signed in with API key: victoria-air.local-akshay-20210714133859.
Pushing gem to https://rubygems.org...
Successfully registered gem: algorithm (0.0.0)
```

And with that, `algorithm` is live, you can check it out [here](https://rubygems.org/gems/algorithm). You can also search for it using the `gem search` command. 

```bash
➜  algorithm gem search ^algorithm$

*** REMOTE GEMS ***

algorithm (0.0.0)
```

### The Easy Way

You can use [Bundler](https://bundler.io/) to create a gem with a single command. Bundler is a tool that manages dependencies between the ruby gems. It provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions needed by your project. 

First, Install bundler using the `gem install` command. 

```bash
gem install bundler

➜ bundle -v
Bundler version 2.2.19
```

Create a gem named  `algorythm` using the `bundle gem` command. 

```bash
➜  my-gems bundle gem algorythm
Creating gem 'algorythm'...
Initializing git repo in /Users/akshay/Dev/ruby/my-gems/algorythm
      create  algorythm/Gemfile
      create  algorythm/lib/algorythm.rb
      create  algorythm/lib/algorythm/version.rb
      create  algorythm/algorythm.gemspec
      create  algorythm/Rakefile
      create  algorythm/README.md
      create  algorythm/bin/console
      create  algorythm/bin/setup
      create  algorythm/.gitignore
Gem 'algorythm' was successfully created. For more information on making a RubyGem visit https://bundler.io/guides/creating_gem.html
```

Unlike the first approach, where you have to create each file manually, bundler incorporates the best practices in creating Ruby gems and generates a bunch of files for you, such as `README.md`, `Rakefile`, etc. It also initializes a git repository for you. Nice!

```bash
➜  algorythm git:(master) ✗ tree
.
├── Gemfile
├── README.md
├── Rakefile
├── algorythm.gemspec
├── bin
│   ├── console
│   └── setup
└── lib
    ├── algorythm
    │   └── version.rb
    └── algorythm.rb

3 directories, 8 files
```

So there you go. In this post, we learned how to create a new Ruby gem and publish it on RubyGems.org. 

Hope this helps!