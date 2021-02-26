---
layout: post
title: Configuration Management
tags: devops
---

One thing I am learning as a developer working on enterprise software is the importance of a configuration management system. When you have a software system installed on-premises for each customer that is configured and customized separately, managing configuration becomes a challenge. You can't just use environment variables or simple files to store config. You need to have a good strategy to deal with the configuration.  

When code relies on values that may change after the application has gone live, keep those values external to the app. When your application will run in different environments and potentially for different customers, keep the environment- and customer-specific values outside the app. 

Common things you will probably want to put in configuration data include: 

- Credentials for external services (database, third-party APIs, and so on)
- Logging levels and destinations
- Port, IP address, machine, and cluster names the app uses
- Environment-specific validation parameters
- Externally set parameters, such as tax rates
- Site-specific formatting details
- License keys

Basically, look for anything that you know will have to change that you can express outside your main body of code and slap it into some configuration bucket. In this way, you’re parameterizing your application; the code adapts to the places it runs. 

> Parameterize Your App Using External Configuration.


If the configuration is simple, you can store it in JSON or XML files. For more complicated ones, you might need an application that stores the config in the database. When your application starts, it reads this configuration as a data structure in memory and uses it throughout its life. If you change the configuration, the application needs to restart to fetch the new values. This is how we manage configuration at CityView.

Though this is a common approach to managing configuration, the pragmatic programmers recommend against it. Instead, their suggestion is to wrap the configuration information behind a thin API. This decouples your code from the details of the representation of the configuration.

**Configuration-as-a-Service**

The config is still external to the application in this approach, but instead of storing it in a file or database, it's stored behind a service API. This has the following benefits:

- Changing configuration doesn't require the application to restart. Then next API call will fetch the latest configuration value. 
- Multiple applications can share configuration with correct authentication and authorization. 

The first benefit is important. Modern applications are expected to be up and running all the time. You shouldn't have to stop and start the whole app to change a single config value. Using config-as-a-service, the application always fetches the latest value from the configuration dynamically. When config changes, there's no need to rebuild the code. 

However, I am not totally sold on this benefit. If I expose my configuration as a service behind an API, my application becomes chatty, making many HTTP calls with the API, which would have been available in-memory if they were loaded as a data structure when the application started. An HTTP call is always going to be slower than an in-memory call. 

You have to use your best judgement and choose the strategy that suits the users' needs and application and what's important to you. If the config is changing all the time and you don't want to restart the app each time, use config-as-a-service. If the config is done initially and changes rarely, use a static configuration that gets loaded when the application boots up.