---
layout: post
title: Useful Rails Commands
---

As I am learning Ruby on Rails, I find myself searching for a few commands over and over. Here are some of the essential ones. 

Specify the environment and the port to run on.

```bash
bin/rails server -e production -p 4000
```

See all the available generators.

```bash
bin/rails generate
```

Generate a new controller.

```bash
bin/rails generate controller Home index
```

Generate a new model.

```bash
bin/rails generate model post title:string body:text published:boolean
```

The `console` command lets you interact with your Rails application from the command line. 

```bash
bin/rails console
```

`bin/rails dbconsole` figures out which database you're using and drops you into whichever command line interface you would use with it.

```bash
bin/rails dbconsole
```

`destroy` undoes whatever `generate` did. For example:

```bash
bin/rails generate model Oops
bin/rails destroy model Oops
```

Finally, here are some other useful commands. 

- `bin/rails middleware` lists Rack middleware stack enabled for your app.
- `bin/rails stats` is great for looking at statistics on your code, displaying things like KLOCs (thousands of lines of code) and your code to test ratio.
- `bin/rails secret` will give you a pseudo-random key to use for your session secret.
- `bin/rails time:zones:all` lists all the timezones Rails knows about.