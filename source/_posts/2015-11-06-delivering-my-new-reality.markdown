---
layout: post
title: "Delivering My New Reality"
date: 2015-11-06 07:00:48 -0800
comments: true
categories: delivery
---
Back in late December/early January, I took on a new role as the Engineering Lead of Corporate Infrastructure and Applications at Chef. As I started to understand my new role, one of the things I set out to do was figure out what our standard stacks and deploy patterns were going to be. As fate would have it, in early March I got a ping in from one of the folks in marketing about a crazy idea they had about the ChefConf keynote.

With three and a half weeks left before ChefConf, he said, "we want to deliver the announcement about Delivery on stage at ChefConf using Delivery." Within about two weeks I had built a new pipeline, using Delivery, that would get our corporate website, [https://www.chef.io](https://www.chef.io), deployed. As an aside, the decision to move to Fastly as part of this was probably almost as important as moving to Delivery itself.

I am now a convert. The idea of managing an environment operationally, without Delivery or something very close to it, makes me shudder. It has fundamentally changed the way I think about what I do as a professional. The key distinguishing fact, for me anyway, is that we use Delivery to deliver services, not just cookbooks, not just application code, but services.

At this point, my team is already delivering lots of things with Delivery:

- [https://www.chef.io](https://www.chef.io)
- [https://learn.chef.io](https://learn.chef.io)
- [https://downloads.chef.io](https://downloads.chef.io)
- [https://happylaptop.chef.io](https://downloads.chef.io)
- [https://docs.chef.io](https://docs.chef.io)
- An internal app for proxying the Jobvite API
- Internal shared database services
- ICE ([https://github.com/Netflix/ice](https://github.com/Netflix/ice))
- Internal cookbooks for managing infrastructure, etc.
- [https://omnitruck.chef.io](https://omnitruck.chef.io)
- An internal application for managing events
- [https://e.chef.io](https://e.chef.io)

The crazy part is that there are so many reasons why I am in love with Delivery that I can't actually explain them in one post. But my plan is to start writing about each of them. The following is a list of things I plan on writing posts about:

- The standard way of shipping things: Making changes is the same, no matter what app you are in.
- The artifact is king: Shipping a promotable artifact really is a HUGE win.
- The shape of the pipeline: Where the phases and stages are makes a huge difference in how I think now.
- Yes, you really do need four separate environments.
- A down and dirty intro to build cookbooks.
- It can't be all rainbows and unicorns... A look at some of the pain points and gotchas.

I really am super excited about Delivery and not just because I work at Chef. Hopefully even if you aren't using Delivery itself, some of the things I have learned about CD will help you as well.