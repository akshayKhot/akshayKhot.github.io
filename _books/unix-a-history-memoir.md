---
layout: post
title: "Unix: A History and a Memoir"
date: 2021-7-6
img: unix_memoir.jpg
---

I am not even halfway reading this book from Brian Kernighan, but couldn't wait to share my notes. Bell Labs, where Unix began, was a remarkable institution that produced many good ideas and capitalized on them. 

<div class="book">
<a target="_blank" href="{{ site.bookshelf }}/{{ page.img }}">
  <img src="{{ site.bookshelf }}/{{ page.img }}" alt="{{page.title}}">
</a>
</div>

The Unix story certainly offers many insights into how to design and build software, and how to use computers effectively, which the book tries to highlight along the way. As a simple but characteristic example, the Unix philosophy of software tools made it possible to combine existing programs to accomplish a wide variety of tasks without having to write new software.

It's a programming instance of an old strategy: divide and conquer. By breaking bigger tasks into smaller ones, each one becomes more manageable, and the pieces can be combined in unexpected ways.

He (Hamming) felt that programming should be taught as writing was taught. There should be a notion of style that separated poor code from good code, and programmers should be taught how to write well and appreciate good style. 

I (Kernighan) was a department head for over 15 years, was probably at best an average manager, and was definitely happy to step down. Others successfully resisted promotion for long periods; Dennis Ritchie became a department head well after I did, and Ken Thompson never did. 
Programming is the process of creating the sequences of operations that perform some desired task, using some programming language. Compilers translate from higher-level languages (closer to human language) ultimately to the individual instructions of a specific kind of computer. 

Finally, an operating system is just a big and complicated program built from the same instructions as ordinary programs like Word or a browser. Its task is to control all the other programs that are trying to run and to manage interactions with the rest of the computer. 

### Multics

**CTSS** was the most innovative OP of the time, allowing users to type on terminals connected to a big IBM machine (7094), instead of punch cards. It was more pleasant and productive than batch processing.

It was such a productive programming environment that MIT researchers decided to create an even better version called **Multics,** which stood for Multiplexed Information and Computing Service.

Multics was complicated, and needed new software and hardware than IBM 7094, so MIT enlisted GE (for hardware) and Bell Labs (for software).

Because it was so ambitious, Multics soon ran into problems. It was a victim of the **second system effect**. It was over-engineered, and was described as "an attempt to climb too many trees at once." Coordinating two companies and a university spread across the country was difficult. 

> Second system effect: After a success, it's tempting to try to creates a new system that fixes all the remaining problems with the original while adding everybody's favorite new features. The result is often a system that's too complicated, a consequence of taking on too many different things at the same time. 

Bell Labs worked on Multics from 1966 through 1969. By 1968, it realized that it was not going to achieve its goal of providing computing services at a reasonable cost. It was too expensive. Bell Labs dropped out of the project in April 1969 (MIT and GE worked on it and Multics was eventually completed and used until 2000, though not widely).

 Multics was the source of many good ideas, but its biggest contribution was its influence on a tiny operating systen called Unix. 

### Unix

Unix was created in part as a reaction to the complexity of Multics. When Bell Labs pulled out of Multics, Ken Thompson and Dennis Ritchie who were working on it had to find something else to do. They spent time exploring ideas and doing paper designs. 

Around this time, Ken found DEC PDP-7, which was a dated computer with 16K bytes of memory. 

> “At some point I realized that I was three weeks from an operating system.” - Ken Thompson

He needed to write three programs, one per week.

1. An editor, so he could create code
2. An assembler, to turn the code into machine language that could run on the PDP-7
3. A kernel - an operating system

Right at that time, Ken’s wife went on a three-week vacation to take their one-year-old son to visit Ken’s parents in California, and Ken had three weeks to work undisturbed.

As he said during a 2019 interview, 

> One week, one week, one week, and we had Unix

The first version of a recognizable Unix system was running in mid to late 1969. 

> In retrospect, I think that Bell Labs did a good job with space. Private offices, though they cost more than open areas, give people peace and quiet, a place to focus without constant noise in the background, storage for books and papers, and a door to close for intense thought or private conversations. By now, I've spent enough time in open-plan work areas to know that, for me at least, they are utterly destructive of concentration. The Bell Labs mixture of one’s own private office and a shared space for the community worked very well.  

### Unix Features

It may be hard for today's readers to appreciate just how much of a simplification all Unix was. It hid all the irrelevant nonsense that earlier operating systems enforced on their users. 

**File system**

- A Unix file is simply a sequence of bytes. 
- Any structure or organization of the contents is determined only by the programs that process it. 
- Files are organized in directories, which contain file information e.g. name, access, size, date & time of creation/modification, etc. 
- Any directory can contain subdirectories so the file system is hierarchical. 

**System calls**

- Provide a way to access the services that an OS provides, such as starting/stopping programs, reading/writing files, accessing storage/network. 
- The Unix File system interface is very simple, with only five system calls to open or create a file, read or write its bytes, and close it. 

---

**Ken Thompson**
- Born in 1943 
- Went to UCB to study electrical engineering 
- Electronics was his hobby for 10 years before college
- Arrived at Bell Labs in 1966 and started work on Multics
- Interest in games, especially Chess; and flying 
- Retired from Bell Labs in 2000
- Moved to Google in 2006
- Created Go programming language with Rob Pike and Robert Griesemer

Quotes:

> I consumed computers, I loved them. At that time, there was no computer science curriculum at Berkeley; it was being invented.  

> I was just going to stay in the university because... I owned it. My fingers were in absolutely everything. The main monster computer at university shut down at midnight and I’d come in with my key and I’d open it up and it would be my personal computer until 8 AM.

**Dennis Ritchie**

- Born in 1941
- Went to Harvard for undergrad in physics and grad in applied Maths.
- ACM Turing Award in 1983 for C and Unix
- Retired officially in 2007 but continued to come down to Bell Labs every day until his death in October 2011.

> Dennis was modest and generous, always giving credit to others while downplaying his own contributions. 

Dennis was a superb technical writer, with a spare elegant style, deft turns of phrase, and often with flashes of dry wit that accurately reflected his personality. He and I wrote The C Programming Language together; it was published in 1978, with a second edition in 1988, and has since been translated into more than two dozen languages. Dennis’s original C reference manual formed the basis of the ANSI/ISO standard for C that was first produced in 1988, and was a major part of the book. Without doubt, some of the success of C and Unix can be attributed to Dennis’s writing. 