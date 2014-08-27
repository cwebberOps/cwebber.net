---
layout: post
title: "Bootstrapping Windows with Chef"
date: 2014-08-25 08:36:55 -0700
comments: true
categories: chef, windows, ec2
---
As part of my work on the community cookbooks I am finding more and more need to test things against Windows. While I am excited for the work that [@afiune](https://twitter.com/afiune) has been doing to make [Test Kitchen](http://kitchen.ci) work with Windows, I really want any testing I do on the community cookbooks to be easily reproducible by the community. From there I set out to learn how to do a basic bootstrap and apply a cookbook.