---
layout: post
title: Why We Avoid Testing
tags: programming
---


The role of software testing is to provide information about the quality of a product. In his book [Perfect Software and Other Illusions About Testing](https://www.amazon.ca/Perfect-Software-Other-Illusions-Testing-ebook/dp/B004J4VVE2/ref=sr_1_1?crid=3OAVAP1F1UEBH&dchild=1&keywords=perfect+software+and+other+illusions+about+testing&qid=1593398593&sprefix=perfect+softwar%2Caps%2C213&sr=8-1), Gerald Weinberg, who is one of my favourite writers, lists a few reasons why developers, testers, and managers avoid testing the product that they are ultimately responsible for. 

The list is hilarious, and the book provides real-world examples from the author's many years of consulting experience. After a couple of years of working professionally as a software developer, I can definitely resonate with them. Here are some of the reasons we don't test our software:

**We have so many bugs, our bug database doesn't work efficiently.**

- The development team who called in the consultant to make their bug database perform faster, because it was crushing under thousands of bugs and devs were producing bugs faster than they were fixing them. 
- Wrong priorities. Focus on reducing bugs, not managing your bug database more efficiently. 
- Allowing the list of pending bugs/feature requests to grow beyond human comprehension will only cause morale to suffer and fall further behind. 

**We didn't find many bugs,** 

- though we didn't really look/I'm testing the wrong application and don't know it.
- Looking at the wrong components, or testing things that don't matter in the bigger picture. 
- Wasting time on unnecessary testing, ignoring the major parts. 

**We found so many bugs, there couldn't be any more.**

- Thinking that more bugs found = less bugs remaining. Wrong. 

**Not having the specifications for the product.** 

- A common myth of Agile is that we don't need no specification. We will just build and iterate by getting user feedback. That's a fallacy. 
- As Joel [says](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/), you need to have a spec to build good software. 

**It's not in my component, so I don't record it.**

- The tester who keeps on ignoring bugs in the product because it is not related to the feature/task that he/she is testing right now, or not in his domain. 

**We don't test the worst components because it takes too long.**

- Not testing an important functionality because it takes too long to set up the test case. So we will just ignore it. 

**Our tests proved the program was correct.**

- The test manager, when asked why he allowed a buggy release, replied, "because our tests proved that it was correct". No amount of testing will ever "prove" a program is correct. Correct is not even a definable term. 
- Using fake testing models, such as over-reliance on automated testing will give you false confidence, in turn missing important bugs that would've been caught by a competent human tester. 

**We ran so many test cases that we couldn't look at them all.**

- The team that thought that the software was ready to ship because "we've run six-hundred-thousand" test cases and nothing crashed the system. 
- Thinking that anything doesn't crash must be okay. 

**If our software works okay for three users, obviously it will work okay for a 100.**

- Ignoring effects of scale on performance. 

**We don't want our testers to know we're ignoring their information.**

- The dev team that didn't include QA in the important meetings, because "they just delay shipping software". 

**I don't report bugs, so the developer won't be angry with me.**

- The QA who doesn't report bugs because "the dev will get angry because it makes him look bad"
- Blaming people for reporting the bugs in the product only motivates them to hide bugs, which is not useful to anyone. 

**We don't need to test that, because the developer is really good.**

- We don't know the first thing about real humans. The fallacy of perfect software.