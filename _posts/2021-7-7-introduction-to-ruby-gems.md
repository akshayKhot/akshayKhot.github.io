---
layout: post
title: An Introduction to Ruby Gems
tags: ruby
img: rubygems_server.png
---

This is the first post in a series of posts on ruby gems. It explains what  ruby gems are and various commands you can use the interact with gems. 

**What is a ruby gem?**

A gem is a software package containing ruby application or library. Gems give you a structured and reliable way to install, use, package, and distribute ruby code. You can use gems written by other ruby programmers in your own applications and write and publish your own gems that others can use. 

RubyGems is a package manager for ruby, providing a standard format for distributing ruby gems. It's a piece of software that hosts the gems on its server. You can use the `gem` command that ships with ruby to use RubyGems. 

**Searching for Gems**

When you are a new ruby programmer, you won't be writing your own gems. Instead, you will use the gems developed by others. Here are a few different ways to check what gems are available for you to use. 

1. The `search` command lets you find gems from the command line. 

   ```bash
   ➜  ~ gem search sequel
   
   *** REMOTE GEMS ***
   
   abbish_sequel_plugins (0.0.6)
   active_scaffold-sequel (0.8.0)
   acts_as_api_sequel (0.0.1)
   annotate-sequel (1.1.1)
   aquel-sequel (0.0.1)
   async-sequel (0.1.0)
   bumbleworks-sequel (0.0.4)
   [...]
   ```

   As you can see, gem returns many entries, all containing the phrase `sequel` when you only provide the name. You can use regular expressions to be more precise. 

   ```bash
   ➜  ~ gem search ^sequel$
   
   *** REMOTE GEMS ***
   
   sequel (5.46.0)
   ```
   
2. Use the search feature on the [RubyGems](https://rubygems.org/) website. For example, [this search for the sequel gem](https://rubygems.org/search?query=sequel).

**Installing the Gems**

Once you find a gem that suits your needs, the next step is to install it so you can use it in your application. The `install` command lets you install the gem along with its documentation. 

```bash
➜  ~ gem install sequel
Fetching sequel-5.46.0.gem
Successfully installed sequel-5.46.0
Parsing documentation for sequel-5.46.0
Installing ri documentation for sequel-5.46.0
Done installing documentation for sequel after 5 seconds
1 gem installed
```

**List Installed Gems**

To see a list of all the available gems, use the `list` command.

```bash
➜  ~ gem list

*** LOCAL GEMS ***

abbrev (default: 0.1.0)
actioncable (6.1.4)
actionmailbox (6.1.4)
actionmailer (6.1.4)
actionpack (6.1.4)
actiontext (6.1.4)
[...]
```

**Uninstalling a Gem**

If you installed a gem by mistake or no longer need it, you can uninstall it using the `uninstall` command. 

```bash
➜  ~ gem uninstall drip
Successfully uninstalled drip-0.1.1
```

**Read the Gem Documentation**

To understand how a gem works, you can read the documentation that comes with the gem. To see the documentation for a gem, use the `server` command, which spins up a server. You can then go to the URL provided to read the documentation of the gem. 

<a target="_blank" href="{{ site.images }}/{{ page.img }}">
  <img src="{{ site.images }}/{{ page.img }}" alt="RubyGems Server">
</a>  

This was the introduction to gems in ruby. In the next post, we will learn how to create your own gems. 

