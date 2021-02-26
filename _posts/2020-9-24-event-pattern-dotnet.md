---
layout: post
title: Event Pattern in .NET
tags: programming
---

Here is a simple example that illustrates how to use the event pattern in .NET.

First, define the structure of the data that you want to send when the event happens. 

```c#
public class ThresholdReachedEventArgs : EventArgs
{
    public int Threshold { get; set; }
    public DateTime TimeReached { get; set; }
}
```

Then, define the Publisher, i.e. the class that wants to raise an event

```c#
public class Counter
{
    // 1. Define an event
    public event EventHandler<ThresholdReachedEventArgs> ThresholdReached;

    // 2. Do something that raises the event, and pass the EventArgs custom data 
    public void DoSomething()
    {
        ThresholdReachedEventArgs e = new ThresholdReachedEventArgs
        {
            Threshold = 10,
            TimeReached = DateTime.Now
        };
        
        // 3. Raise the actual event
        ThresholdReached?.Invoke(this, e);
    }
}
```

Finally, create one or many subscribers. Classes that want to listen to an event raised by the Publisher.

```c#
class Program
{
    static void Main(string[] args)
    {
        // 1. Create an instance of the publisher, which you want to listen to
        Counter counter = new Counter();

        // 2. Attach an event handler on the publisher
        counter.ThresholdReached += OnThresholdReached;
        
        // 3. Do something that will raise the event. Now you are ready to listen to the event. 
        counter.DoSomething();
    }

    // 4. Handle the event which is raised by publisher
    static void OnThresholdReached(object sender, ThresholdReachedEventArgs e)
    {
        Console.WriteLine($"Reached Threshold {e.Threshold} at {e.TimeReached.ToString()}");
        Console.ReadLine();
    }
}
```