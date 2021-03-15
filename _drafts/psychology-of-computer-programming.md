---
layout: post
title: The Psychology of Computer Programming
---

This book has only one major purpose—to trigger the beginning of a new field of study: computer programming as a human activity, or, in short, the psychology of computer programming.

The material which follows is food for thought, not a substitute for it.

### Reading Programs

Programming is, among other things, a kind of writing. One way to learn writing is to write, but in all other forms of writing, one also reads. We read examples—both good and bad—to facilitate learning. But how many programmers learn to write programs by reading programs?

A young novelist of our time was recently asked who were his favorite authors. He responded simply that he never read novels, as his ideas were so new and superior to anyone else's that reading would only be a waste of his time. As you might expect, his work did not support his thesis. Perhaps the same could be said for some of our radical young programmers. Perhaps there is something to be gained from reading other people's programs—if only the amusement engendered by their bad examples. Perhaps if we want to understand how programmers program —to lift the veil of the programming mystique—we could fruitfully begin by seeing what is to be learned from the reading of programs.

Warning: Reading code won't help if the reader has no sense of what's good and what's bad. 

**An approach to read programs**

Unlike novels, the best way to read them is not always from beginning to end. They are not even like mysteries, where we can turn to the penultimate page for the best part. Instead, as we look at each piece of code, we ask ourselves the question, **"Why is this piece here?"**

**Few reasons why code exists**

When we do read code, we find that some of it gets written because of machine limitations, some because of language limitations, some because of programmer limitations, some because of historical accidents, and some because of specifications—both essential and inessential. 

For whatever reason a particular piece of code gets inserted into the final product, there are psychological aspects to that reason—which leads us to believe that studying programming as human behavior will bear numerous and not always expected fruits.

1. Machine Limitations

   One of the reasons which account for pieces of code is that the machine on which the program is to be run is limited in some way relative to the ideal machine for the problem.

   When the programmer includes something that is intended to overcome some limitation of the machine, he rarely marks it explicitly as such. Although this omission adds to the intrigue of reading programs, it does penalize the program when, for example, it is transferred to another machine. 

   The programmer may not even be aware that some of his coding is intended to compensate for a limitation of the machine, in which case he could hardly be expected to mark it.

2. Language Limitations

   One of the consequences of moving up above machine language is that certain facilities of the hardware may be lost to the user.

   We may not feel these limitations until they have been lifted from us, just as we often do not know we are sick until we suddenly feel better. Therefore, it is reasonable to expect that future languages will make us feel those limitations of our current languages that are not detectable today.

3. Programmer Limitations
   
   More directly psychological is the question of how much coding is done because the programmer did not have full mastery of his computer, his language, or himself.
   
   There are, of course, programmer limitations other than merely not knowing the full power of the language—vocabulary limitations, we might say. For instance, the programmer may be unaware of certain algorithms, or he may be unable to grasp a sufficiently large portion of the problem at one time to see that certain duplications may be avoided.
   
4. Historical Traces

   We often find material in programs that might be accounted for under one of the above categories but is really present because of the history of the development of the program.

   Things being what they are in the programming business, it is unlikely that anyone is going to delve into a working program and modify it just because the they found a better, alternative way that makes the existing code obsolete. 

5. Specifications

   In almost every program, there is some code which actually does the work that was specified.

   in most cases, we do not know what we want to do until we have taken a flying leap at programming it. 

   Specifications evolve together with programs and programmers. Writing a program is a process of learning—both for the programmer and the person who commissions the program. 

   Moreover, this learning takes place in the context of a particular machine, a particular programming language, a particular programmer or programming team in a particular working environment, and a particular set of historical events that determine not just the form of the code but also what the code does!

> The most important reason for studying the process by which programs are written by people is not to make the programs more efficient, more compact, cheaper, or more easily understood. Instead, the most important gain is the prospect of **getting from our programs what we really want**—rather than just whatever we can manage to produce in our fumbling, bumbling way.

**Homework**

- If you are a programmer, when was the last time you read somebody else's program? When was the last time somebody else read one of your programs and discussed it with you?
- If you are a first-line manager, are you capable of reading the programs written by your programmers? Do you read them? 
- If you are a higher-level manager, are your first-line managers capable of reading programs written by their programmers? Are you sure?
- Review some code from a library or from your colleagues, or even from your own program. Try to analyze it into pieces of code that are there for reasons mentioned above. **What did you learn?**

### What Makes a Good Program?

It's very difficult to say that one program is better than another, or one programmer is better than another. Not at least, in the sense that we can study the program out of the context in hwich it was developed and in which it will be used nad declare it to have a goodness of 83.72 percent. 

More often, then, we will be doing evaluation of programs not with respect to one another but with respect to a situation—a total situation —in which they are developed. Looking honestly at the situation, we are never looking for the best program, seldom looking for a good one, but always looking for one that meets the requirements.

**Specifications**

The most important criteria when evaluating a program is that it has to be correct. It should give the correct outputs for each possible input. If a program doesn't work, measures of efficiency, of adaptability, or of cost of production have no meaning. 

> Any program that works is better than any program that doesn't.

There is a difference between a program written for one user and a piece of 'software'. When there are multiple users, there are multiple specifications. When there are multiple specifications, there are multiple definitions of when hte program is working. 

**Schedule**

One of the recurring problems in programming is meeting schedules, and a program that is late is often worthless. The average programming manager would prefer that a project be estimated at twelve months and take twelve than that the same project be estimated at six months and take nine. 

**Adaptability**

