---
layout: post
title: Protect Your Users
tags: thoughts cityview
---

As software developers, we have more power than we realize. Our programs directly affect people and influence their behaviour. It's a good idea to take a break from coding from time to time and ask yourself this question.

**Would I use this product myself?**

Or, its corollaries:

- Do I want my personal and sensitive info shared? 
- Do I want my data to be given to big tech companies, sold to the highest bidders? 
- Would I be happy to be driven by this autonomous vehicle? 
- Am I comfortable doing this? 

If the answer is no, take action. Make changes in the software to protect your users.

At CityView, I am building an application that allows city inspectors to conduct virtual video inspections with the contractors without driving all the way to the location. From his home or office, the inspector can talk face-to-face with the contractor, just using the browser, without having to install Skype, Zoom, or WhatsApp. It's a handy application, and I am really having so much fun programming it, using [WebRTC](https://www.w3.org/TR/webrtc/) and Twilio Programmable Video.

The latest feature I implemented allows the inspector to record the entire virtual meeting by clicking a button. The easier way to implement this recording feature would have been to use a third-party library, or use a video framework from a big Silicon Valley company, record the video, and store the video on the cloud, which is just [someone else's computer](https://blog.codinghorror.com/the-cloud-is-just-someone-elses-computer/). I would have finished in a couple of hours, and life would have been great.

Except, when it came time to test the feature, I was hesitant. I faced the phone camera away from me, outside the window, to not record myself or my personal space. I didn't even turn on the webcam on my desktop. I didn't want my video to get uploaded to the cloud, no matter how safe and password protected it was.

This brings us back to the question in the beginning. **If I am not willing to use this feature, how can I expect the poor inspectors and contractors to use it,** record their homes and offices, and trust that the app is not selling the recording to the highest advertisers online or storing it in an insecure way, vulnerable to hacking, or exposing their private lives to the world?

Once that realization set in, and I got over the shame caused by the question, I redesigned the complete recordings architecture and re-implemented the entire workflow. Now, the entire recording is captured and stored on the inspector's computer, safe on the city's servers. Their IT staff knows which physical machine it's on and delete it permanently if not needed. It's not getting uploaded to a cloud server farm somewhere far away or sitting on a cheap laptop waiting to get hacked, but it's on **their** machine, in their hands, and they take responsibility for it. The contractors can ask the city to delete the recording if it contains any sensitive information, knowing that it will be done according to the data privacy act.

Implementing the second design was much harder than the first one. I had to think hard about it, use the native APIs provided by the browsers, worry about synchronizing the audio and video streams of multiple users simultaneously, and store them on the inspector's machine. The design became more complex, and the code size increased by a factor of five. However, the assurance I had when testing the video was priceless. I didn't hesitate while recording, knowing that the video will be stored safely on my computer, and I can delete it whenever I want.

As software developers, we are literally building the future. Each line of code we write can have a massive impact, both for good and bad. Given that responsibility, we should think about the long-term effects of the code we are writing and take responsibility and ownership.