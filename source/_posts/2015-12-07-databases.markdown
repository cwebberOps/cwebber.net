---
layout: post
title: "Databases, Pipelines, and Failures"
date: 2015-12-07 06:18:02 -0800
comments: true
categories: wordpress, dr
---
One of the more interesting things that comes up for me when building new pipelines is around handling the moving of already running services and how things play out when disaster recovery is in play. The hardest part has been framing the question. What are we trying to achieve and how does that affect the other things we are trying to achive? My starting point has been around this:

- What is the "right" behavior in normal operations?
- What is the "right" behavior in disaster recovery or new pipeline build out?

All of this really gets interesting when discussing a service that is heavily database dependent, like Wordpress. In an ideal world, each deploy into acceptance, union, and rehearsal would restore either a replica of exactly what is in delivered/production right now or what was there fairly recently (think last night's backup). This is actually super easy to achive. Assuming that the data we need is accessible, we can build that into the pipeline.

Except, what happens when the production system isn't there for reference? When acceptance goes to be deployed before we get to delivered how do we get valid data in the database? I really see two options:

- Fail the pipeline and force manual intervention.
- Initialize the database with an empty set of data.

When we deploy most applications, at this point, the second option is quite normal. When you are building out for the first time it makes a tremendous amount of sense. Really, this question probably doesn't even cross your mind because there is no production data to start with. On the flip side, when you look at Wordpress and many enterprise applications, much of the config of the application is actually stored in the database. Not to mention, when moving an already existing application, your concerns are usually a bit different than when you are building a new application.

The benefit of forcing the fail is that it ensures that you don't accidentally deploy without a working application. Whether it be settings or content, Wordpress without a restore of the data isn't very useful if it has been used much already. The problem is that, this is hugely disruptive. The first time you spin the pipeline all the way through, you end up needing to fix four database installs (acceptance, union, rehearsal, delivered).

The place I have landed is asking a few more questions:

- What is the overall importance of this application?
- Does this fit into the dependency chain in a way that it is going to block other applications if it doesn't deploy?
- What impact does this have on the system as a whole?
- Rephrasing the above question, if we have bad data, are other systems going to do the wrong thing?
- If other systems do the wrong thing, what could the impact be?

The place that this brings me to is really around the nature of the service and the larger implications. Today I am moving around a Wordpress instance. That instance happens to support the blog and our events page. By it being up with wrong data durring a disaster recovery situation, it really isn't going to hurt anything. It is important, but to have a few pages 404 for a day or two is not the end of the world. Turning that around, it is in the dependency chain for the main website. Which means, in order for us to get the site deployed the app needs to work. There is much more stress created if we cant deploy www because of a missing wordpress backup.

The hypothetical enterprise system also helps justify this position. If instead of a Wordpress instance we were talking about an internal payroll system, it may actually make a ton of sense to fail the pipeline each time. We really do want to ensure that data is correct because other systems do act on it. In a time of crisis you dont want your benefits system to send all of your employees notification that they are now eligible for COBRA and that their health coverage ends in a few days.
