---
layout: post
title: "I am not a coder"
date: 2014-09-26 08:52:12 -0700
comments: true
categories: 
---
The last week at PuppetConf was an absolute blast. It was great to catch up with all the amazing folks doing amazing work. But, there was one thing that bothered me quite a bit. In many different contexts I heard people more or less say, "I can't write Ruby, I'm not a coder." Or, just as bad, "I use Puppet because I am not a coder."

These sentiments bother me in so many ways that I could probably sit and rant for half the day. But really, after thinking about it quite a bit, there are a few key reasons why this idea just doesn't sit well with me. I really think that if you are someone that says something similar to the above, you should rethink things.

## The Technical

### Puppet is why I know Ruby

I feel like an old man in saying this, but back in my day, we didn't have this fancy facter.d stuff. We had to write our custom facts using Ruby and we liked it. Ok, so maybe the liking it part is a bit of a stretch, but I definitely liked the results. When I wrote those facts, I didn't have any clue what a method was or how objects worked, I just knew that when I pasted the right things in and tweaked them a bit, I was able to get information I needed, and that was awesome.

### I don't actually know Ruby

So, anyone that actually thinks I know Ruby, probably has never actually looked at my code. While I am not scared to fire up irb or pry and copy pasta some code in to solve problems, the idea of a large scale Rails or Sinatra App does not sit well with me. I am absolutely a coder, but I am by no means much more than a Junior Ruby Developer when it comes time to my Ruby skills. Like most good SysAdmins, I just happen to be good at Google.

### Have I ever mentioned how much I dislike CPAN?

Whenever I went to go do anything in Perl, I found myself reaching for a module from CPAN. The CPAN topic is probably worth its own discussion, and, to be fair, has probably gotten a bit better since the last time I tackled this. But, as a result of the pain of CPAN and the nature of the environment I was working in at the time, installing new Perl modules wasn't an option and even if it was, it wasn't really feasible. 

Enter Ruby. As a result of running Puppet everywhere, I had Ruby everywhere for free. Combine that with the fact that the Ruby Standard Library is kinda awesome, you get the ability to do some phenomenal things. Since most of my job involved ALL of the systems, I needed to be able to write scripts that would work everywhere in our infrastructure. With the power of Ruby's Standard Library and the fact that the code was actually readable, even a week later in most cases, it made a great way to do systems stuff, everywhere.

### Level up your Puppet game

The real power in Puppet can be found in writing custom functions and custom types and providers. It is the custom functions that let you actually move some of the crazy that usually gets done inside of templates, thus hidden from plain view, and move it back into the manifest where it can be seen in context with all the other things going on in the manifest. The custom types and providers give you the benefit of being able to manage ALL THE THINGS in Puppet. Do you want to manage DNS about systems inside of Puppet? How about adding systems to that new fancy monitoring SaaS? All of that gets done in custom types and providers.

## The Squishy Stuff

### You are already a coder

Are you writing Puppet Code? Are you using ERB? If so, you are already a coder. You are already dealing with making decisions about the APIs you present or don't present. You are dealing with control structures and code organization. You are a coder.

### Code is eating the world

So I am not going to actually dig into this except to say, code is becoming an integral part of our lives as Operations and Systems Administration Professionals. Whether it be with Chef, Puppet, Ansible or the next thing, being a coder is going to be at the center of the jobs that we do.
