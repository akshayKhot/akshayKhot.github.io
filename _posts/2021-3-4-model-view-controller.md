---
layout: post
title: The MVC Pattern, Explained
tags: programming aspnet-core
---

Now that you have an ASP.NET application up and running, the next step is to understand the MVC pattern, which stands for Model-View-Controller, and forms the core of the ASP.NET MVC framework. 

**What's MVC?**

MVC is an architectural pattern that splits the application into three parts: model, view, and controller. It was first introduced in the SmallTalk programming language in the '70s. An easy way to understand MVC: **the model is the data, the view is the user interface, and the controller is the glue between the two**.

**Model** 

This represents the C# classes that hold the data that your application needs and the business logic that operates on that data. Model classes are stored under the 'Models' directory. 

For example, a model class representing a blog post might look like this:

```c#
// Models/Post.cs

namespace app.Models
{
    public class Post
    {
        public int ID { get; set; }

        public string Title { get; set; }

        public string Body { get; set; }
    }
}
```

**View**

Represents the HTML that's sent to the user and displayed in the browser. One important thing to remember is that this HTML is not static or hard-coded. It's generated dynamically by the controller using a model's data. In ASP.NET, the views are stored in a .cshtml file and are found under the 'Views' directory. 

To continue our example of a blog post, a view to render a post might be:

```html
// Views/Post.cshtml

<div class="post">
    <div class="title">
        <a href="/posts/@post.ID">@post.Title</a>
    </div>

    <div class=body>
        @Html.Raw(post.Body)
    </div>
</div>
```

**Controller**

These are C# classes that form the glue between a model and a view. They handle the HTTP request from the browser, then retrieve the model data and pass it to the view to dynamically render a response. The controller classes are stored under the 'Controllers' directory. 

A PostController that builds the view for the post by fetching the Post model will be:

```c#
// Controllers/PostController

namespace app.Controllers
{
    public class PostsController : BaseController
    {
        public IActionResult Post(int id)
        {
            // Get the post from the database
            Post post = _service.Get(id);

            // Render the post.cshtml view, by providing the post model
            return View(post);
        }
    }
}
```

In an MVC application, each component has its role well specified. For example, model classes only hold the data and the business logic. They don't deal with HTTP requests. Views only display information. The controllers handle and respond to user input and decide which model to pass to which view.

This is known as separation of responsibility, making an application easy to develop and maintain over time as it grows in complexity.

A good guideline to keep in mind when building your MVC code is this quote from the [C2 wiki](https://wiki.c2.com/?ModelViewController): 

> **We need SMART Models, THIN Controllers, and DUMB Views**