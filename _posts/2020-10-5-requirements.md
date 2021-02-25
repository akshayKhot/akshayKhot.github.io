---
layout: post
title: Requirements
---

In his book, [Practice of System and Network Administration](https://www.amazon.ca/Practice-System-Network-Administration-Enterprise-ebook/dp/B01MFCSNQZ/ref=sr_1_1?dchild=1&keywords=Practice+of+System+and+Network+Administration%2C+The%3A+DevOps+and+other+Best+Practices+for+Enterprise+IT%2C+Volume+1&qid=1600958358&sr=8-1), Tom Limoncelli explains the importance of writing down the requirements for the system you are building. I think the list applies equally well to software projects. Having a list of clear requirements written down is probably one of the most important things you can do before starting a project.

Requirements are a list of what the service will be able to do. Requirements should list desired functionality, features, and capabilities. **Focus on the end goal: what the system will enable people to achieve.** The list of requirements guides all the other steps: design, engineering, implementation, testing, and so on. 

Requirements are written down. They are not simply agreed to in a verbal discussion, tracked on a dry-erase board in your office, or kept in your head. Writing them down in a shared requirements document has many benefits.

**Transparency**: Unlike your brain or the dry-erase board in your office, everyone can read the requirements document.

**Fewer gaps**: Writing down requirements reduces errors caused by a request being misheard or forgotten. People can verify that their request was recorded properly.

**Fewer misunderstandings**: Two people often think they have a verbal agreement when they do not. Seeing the decision in writing verifies that everyone agrees to the same thing.

**Buy-in and approval**: Written requirements provide the ability to get buy-in and management approval in an accountable way. People know what they agree to. People can’t claim they didn’t sign off on the requirements if they’ve literally signed their name on a printout. They may claim they didn’t understand the document or that circumstances and budgets have changed, but at least you have a baseline agreement.

**Fixed scope**: A formal requirements document provides a mechanism for handling additional feature requests that arrive after the agreement has been reached, preventing feature-creep. New requirements need to be formally agreed to, documented as a scope change, and subjected to buy-in and management approval before they can be added to the scope.

**Accountability**: Accountability is a two-way street. Customers can point to the document when a requirement you’ve agreed to turns out to be missing or incomplete. Documentation of requirements also helps delineate features versus bugs. A bug is a requirement that is incorrectly implemented. A feature request is a new requirement that wasn’t previously agreed to. While a bug should be fixed, a feature request requires approval, resource allocation, and possibly budget approval.

A requirements document does not need to be hundreds of pages long. A bullet list may be sufficient for small projects. The essence of business writing is brevity. A short, concise document is easier to read and understand.

Define terminology early in the document. **Ontology** is the system of terms and definitions that define the system and its parts. Often during a heated debate, one realizes that everyone uses the same words but mean different things. Getting agreement to the ontology that will be used is very important.

The requirements should focus on the list of features, stated from the perspective of what the customer should be able to accomplish using business terms, not technical terms. Record the “what,” not the “how.”

This also means not proscribing particular technology. For example, when an email system is being designed, users might request that it be compatible with the IMAP protocol (RFC3501). They should, instead, be stating their needs at a higher level of abstraction. Ask them why they need such a specific thing. For example, maybe they need to be able to read their email from their smartphone, and they know that their phone supports IMAP. 

Conversely, specifying IMAP support may under-specify the feature. Imagine the user’s surprise when the IMAP support is available, but their particular smartphone is unable to access email. The feature is complete as specified—IMAP is supported—but the user cannot read an email. Requesting that this problem be fixed would be a feature request, not a bug. It would be rejected, much to the surprise and dismay of the customer. Technically speaking, the product works as requested.

This kind of situation makes perfect sense to a technical person but is frustrating and unreasonable to a typical user. This is one reason why users view IT departments as difficult to deal with. They’re being told they got what they asked for, but in their mind, that’s not true: They can’t read the email from their phone. Phrasing requirements at the right level of abstraction is one way that we can prevent this problem.