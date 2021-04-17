---
layout: post
title: "How to Setup an Aurelia + TypeScript Single Page App on ASP.NET"
---

This article is for .NET developers who want to build a responsive and fast single-page application using the Aurelia framework. It explains how to set up a simple ASP.NET MVC project, add support for an Aurelia app, and use Webpack to watch, compile and bundle the TypeScript files into a single JavaScript file. 

Combined together, these tools provide a delightful development experience. If you are unfamiliar with them, I encourage you to check out the [sandbox project](https://github.com/akshayKhot/Sandbox#getting-started) I created on GitHub. In less than five minutes, you will have a complete dev environment to play with. 

Before we begin, here is a refresher on the tools and frameworks we will be working with. 

**[ASP.NET](https://dotnet.microsoft.com/apps/aspnet)** 

A free, cross-platform, and open-source framework that lets you build web applications and APIs with .NET and C#. This will be the back-end application for our project, responding to requests from the Aurelia client. 

**[Aurelia](https://aurelia.io/)**

An open-source, opinionated JavaScript framework. It is designed to easily build powerful web, mobile, or desktop applications. Aurelia uses open web standards. [Read](https://docs.aurelia.io/) the documentation to learn more about Aurelia. 

**[Typescript](https://www.typescriptlang.org/)**

An open-source programming language developed by Anders Hejlsberg (creator of C#) at Microsoft. It acts as a superset of JavaScript and adds typing support to the language. It also provides extensive tooling for the JavaScript ecosystem. 

**[Webpack](https://webpack.js.org/)** 

A module bundler, which is a fancy term for a program that compiles multiple JavaScript modules into a single file. It can also convert TypeScript code into JavaScript, watch for changes and re-run the tasks. For a good introduction, check out this [Webpack tutorial](https://flaviocopes.com/webpack/) by Flavio Copes. 

---

**Table of Contents**:

1. [Install Dotnet](#install-dotnet)
2. [Create an ASP.NET Project](#create-an-aspnet-project)
3. [Create an Aurelia App](#create-an-aurelia-app)
4. [Add Aurelia to ASP.NET](#add-aurelia-to-aspnet)
5. [Run the App](#run-the-app)

### Install Dotnet

First, [download the dotnet framework](https://dotnet.microsoft.com/download). You can check if it's installed properly by typing `dotnet` in your terminal window. It should give you the following output. 

```bash
➜  ~ dotnet

Usage: dotnet [options]
Usage: dotnet [path-to-application]

Options:
  -h|--help         Display help.
  --info            Display .NET Core information.
  --list-sdks       Display the installed SDKs.
  --list-runtimes   Display the installed runtimes.

path-to-application:
  The path to an application .dll file to execute.
```

### Create an ASP.NET Project

Next, create an MVC application using the generator provided by dotnet. Generators are tools that let you quickly set up a complete application using a single command. For an MVC application, run the following command. 

```bash
➜  dotnet dotnet new mvc --name Sandbox
The template "ASP.NET Core Web App (Model-View-Controller)" was created successfully.
...	

Restore succeeded.
```

If you don't provide the `--name` flag, `dotnet` command creates the MVC project in the same directory you are running the command from. 

Now that `dotnet` has created an ASP.NET MVC project for us, switch to the directory and open the project in [VS Code](#). 

```bash
➜  cd Sandbox
➜  Sandbox code .
```

Once the project opens in VS Code, you should see the following structure. 

<a target="_blank" href="{{ site.photos }}/aspnet_vs_code.jpg">
  <img src="{{ site.photos }}/aspnet_vs_code.jpg" alt="VS Code">
</a>

To run, type `dotnet run` command from the `Sandbox` directory. 

```bash
➜  Sandbox dotnet run
Building...
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: http://localhost:5000
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: /Users/akshay/Dev/dotnet/Sandbox
```

To see the running app, navigate to [https://localhost:5001](#). You will be greeted with the ASP.NET home page.

<a target="_blank" href="{{ site.photos }}/aspnet_home.jpg">
  <img src="{{ site.photos }}/aspnet_home.jpg" alt="Home Page">
</a>

Congratulations, you have successfully set up an ASP.NET web application. 

### Create an Aurelia App

First, install node from the [node.js](https://nodejs.org/en/download/) website. Then, from the Sandbox directory, run the `npx makes aurelia` command which will guide you through setting up a new Aurelia application. 

```bash
➜  Sandbox git:(master) npx makes aurelia

...

✔ Please name this new project: › app
✔ Would you like to use the default setup or customize your choices? › Default TypeScript Aurelia 2 App
✔ Do you want to install npm dependencies now? › No

...
```

Now your folder structure should look like this:

<a target="_blank" href="{{ site.photos }}/aspnet_aurelia.jpg">
  <img src="{{ site.photos }}/aspnet_aurelia.jpg" alt="Aurelia">
</a>

### Add Aurelia to ASP.NET

Update the `output.path` property in the `app/webpack.config.js` file with the following code. 

``` javascript
output: {
    // put the generated output in the `wwwrooot\lib` directory
    path: path.resolve(__dirname, '..', 'wwwroot', 'lib'),
    // ...
},
```

Add the following `script` tag to the `Views/Shared/_Layout.cshtml` file. 

```html
<script src="~/lib/entry.bundle.js"></script>
```

Replace the entire content of the `Views/Home/index.cshtml` file with: 

```html
<my-app></my-app>
```

### Run the App

First, install the required npm packages by switching to the `app` directory and running the `npm install` command. 

```bash
➜  Sandbox cd app
➜  app npm install
```

Once npm installs the packages, you can launch your app using  `npx webpack -w` command from the `app` directory. This command tells webpack to compile the Aurelia source code that includes the HTML, TypeScript (compiled to JavaScript), and CSS files and put it under `lib` directory. The `-w` flag tells Webpack to watch for changes in the source. 

```bash
➜  app npx webpack -w
...
...
webpack 5.31.0 compiled successfully in 5677 ms
```

Finally, start your ASP.NET server with the `dotnet run` command from the Sandbox directory. You should run this command in a different terminal window. 

```bash
➜  Sandbox dotnet run
Building...
```

<a target="_blank" href="{{ site.photos }}/aspnet_app.jpg">
  <img src="{{ site.photos }}/aspnet_app.jpg" alt="App">
</a>

To verify if Webpack is watching for code changes, make a simple modification in the `app/src/my-app.ts` file and reload the browser. 

Of course, both the ASP.NET and Aurelia apps contain a lot of boilerplate code. If you are like me, and like to start each new project from a clean slate, I have set up a polished application that lets you do just that. Just download/clone the [Sandbox](https://github.com/akshayKhot/Sandbox) project from GitHub and follow the instructions to set up a clean sandbox. 
