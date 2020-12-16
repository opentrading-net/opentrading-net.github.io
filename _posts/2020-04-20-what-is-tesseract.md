---
layout: post
title:  "What is Tesseract?"
categories: Tesseract
tags: RAD 
comments: true
author: David Regan
---

Tesseract is a radical approach to building business applications. It's a platform to support modular applications where: the focus is on business logic and models; short cutting the development lifecycle; and avoiding technology being more of a hindrance than a help.

<!--more-->

The idea for Tesseract came out of experiences building a global metals, coal & concentrates solution for a mining comglomerate. After 15+ years of experience of configuring, extending and integrating CTRM solutions our team had an epiphany with [Aspect] that we could finally give the Business exactly what they wanted for each of their business units (or at least pretty close).

## Aspect

Aspect is a basic CTRM that has some innovative features; in particular: a in-memory model; real time risk and a built-in scripting language designed primarily for reporting and interface definitions. In the early days the scripting features were basic (e.g. no functions!) but even in its limited form it allowed for the data model to be extended. Over time, as the programme of work progressed, we worked with the vendor to improve the scripting features and effectively built a custom CTRM on top of the out-of-the-box product.

## Tesseract

Tesseract takes the concept of a scriptable, extensible data model and builds a system based on this idea - from the ground up. It uses modern, off-the-shelf technolgies (e.g. [C#], [Roslyn], [.NET Core], [SQL Server], [Azure], [REST]) to build a light weight application landscape that allows technical BAs and developers to quickly build useful, performant applications.

## Why the name?

> In geometry, the tesseract is the four-dimensional analogue of the cube; the tesseract is to the cube as the cube is to the square. Just as the surface of the cube consists of six square faces, the hypersurface of the tesseract consists of eight cubical cells. The tesseract is one of the six convex regular 4-polytopes.
> -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/Tesseract)</cite>

In the same way as a cube can be unfolded as a net of six squares in two dimensions, a hyper cube can be unfolded from four dimensional space into a net of eight cubes in three dimensional space. You can't visualise this, of course, but this figure from Wikipedia tries hard to convey the idea...

{% include figure.html image="/assets/images/Net_of_tesseract.gif" caption="https://commons.wikimedia.org/wiki/File:Net_of_tesseract.gif" %}

Those eight cubes can be seen directly if you draw a tesseract as a graph of 16 vertices and 32 edges - one is highlighted in purple here:

{% include figure.html image="/assets/images/330px-Orthogonal_Tesseract_Gif-1.gif" caption="Animation showing each individual cube within the B4 Coxeter plane projection of the tesseract" %}

So, why the name ... it's an attempt to convery that the multiple dimensions of our Tesseract product that come together to build something greater than it's parts - and like the Tesseract it's a bit hard to get your head around!

## Zen and the Art of Application Development

Building good applications is hard. So many IT projects produce mediocre results for a variety of organisational and technology reasons. Often projects get distracted from solving the business problems by a host of technology issues; and yet a lot of business applications don't need a complicated approach they just need people who understand the business domain and to be able to model the domain in as data and processes. To do this we need an application development framework that allows this focus. That's what Tesseract does.

Here's some of the dimensions that make this possible:

1. It has an extensible type model
    - Types are the building blocks of systems and if the types mirror the business domain then any technically minded analyst or commerically minded developer can model the business
    - Types define the data model and the operations on the data that support the business processes
    - Each business has its own way of working and expecting a vendor or consultancy to come up with type models that meet all the business requirements is expecting too much. Careful design can give a robust model for a given business domain but there will always be extensions or variations that a business will need to add
2. Consistently generated User Interface
    - User interfaces for most business applications do not need to be overly complicated. Often the users of the our systems are experts and they will value efficiency and consistency over snazzy or flashy interactions
    - The artifacts that make up a graphical user interface (GUI), such as menus, forms, grids, etc., should be intuitive to use
    - For most business applications we don't need bespoke user interface design; instead we need a framework for attractive but consistent presentation of information and interactions with a user
    - Tesseract generates its interface from type declarations. I.e. an analyst or developer can declare the data items on a form or view and the actions available to a user and the form or view will be presented - and the set of user interactions will be consistent across the system
3. A modular approach to application development is needed. We should be able to mix and match different modules and extend them to build our application
    - An application should not be a closed system that only does whatever its original designers conceived it for; it should be an adaptable system that grows with the business develops
    - An application that supports invoicing and settlement should allow for a new module that supports sales tax determination. The original designer should not have needed to have foreseen this requirement for it to be possible to add it at a later date
4. No impedence mis-match in the data model
   - Coding business logic in modern languages that provide language-integrated queries on a data model closely aligned with the business domain are easy to maintain and develop
   - There should be no disconnect between the persisted form of the data and the query form. The traditional way to build applications is to have a business logic model and convert this representation to and from the persisted relational form. This means the business logic in the application is often divorced from the reporting or integration solutions. This is not ideal - there should be one model and one way to access it and manipulate it
5. Sessions - source control for business data  
    - Most enterprise applications require robust auditing of data changes and Tesseract's object store keeps track of all data item changes and allows a users to view the state of the system at any point in time using a **session** concept
    - Development and deployment of applications require complex DevOps. Tesseract's **session** allows for development and data changes to be made in a live environment in an isolated session. This allows for much more flexible approaches for Dev and Test - something that traditional data intensive systems struggle with
    - In the commodities trading domain we have strict requirements for end-of-day/month Risk and Finance snapshots. Most systems struggle with the edge cases around managing these scenarios but Tesseract's **sessions** concept provides robust and flexible ways to manage these critical business processes.
6. Integration as a declaration 
    - Integration with a system should not be an afterthought. In modern architectures, hosts of collaborating microservices are often co-ordinated via pub/sub message buses
    - Tesseract automatically creates Open API specified REST services for all views declared on its data models - it's merely permissions that control access to these services
    - The lightweight nature of Tesseract's architecture and it's microservice APIs mean that coherent domains of services can be spun up into the larger enterprise architecure easily and seemlessly
7. Lightweight landscape 
    - Tesseract is a web application with a persistent SQL Server back-end. It is trivial to spin up multiple instances of the application and it's flexibility and strong integration capabilities give flexibility for all sorts of architectures. 
    - Most organiations have realised the value of cloud hosting and Tesseract is designed to be hosted in the cloud but it is environment agnostic. This means it can be hosted on Azure, AWS or on-premise
8. DevOps support
    - [Continuous Integration and Continuous Deployment] has been one of the most valuable contributions to software quality in the past few decades. Modern development teams are now well practiced at CI/CD processes for their releases and any application framework **must** work well seemlessly with these approaches
    - Tesseract has [REST] APIs for DEVOps and PowerShell cmdlets to access these APIs. Both can be integrated into a DevOps deployment pipeline

So that's Tesseract...each component of the system is interesting and useful but together the the different dimensions mean a truly, radical approach to application development.


[.NET Core]: https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet
[Aspect]: https://aspectenterprise.com/
[Roslyn]: https://docs.microsoft.com/en-gb/dotnet/csharp/roslyn-sdk/
[Azure]: http://foo
[SQL Server]: http://foo
[C#]: https://docs.microsoft.com/en-us/dotnet/csharp/
[Continuous Integration and Continuous Deployment]: https://en.wikipedia.org/wiki/CI/CD
[REST]: https://en.wikipedia.org/wiki/Representational_state_transfer