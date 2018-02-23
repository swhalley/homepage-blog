---
title: Architecting an Application
date: 2018-01-01T00:00:00-04:00
draft: true
description: What to look out for 
---

## Overview
You are tasked with starting a new application. The quick choice is to grab the language you know best and go from there. But is your choice going to scale in the future? Are your personal preferences going to work for your organization. Understand that a lot of the choices early will make or break the application in the long run. Version 1 may make it out the door, but if Version 2 is too expensive to write, there is a little chance your organization will be happy with the bill you left on their laps. 

The following article will go over the mindset I take when starting a new application from scratch. Know that your mindset on a lot of the following items will work for small and large applications. The examples will use Java and Javascript to do comparisons, but these ideas should work for any language. 

## Know Your Customers
Who is your customer? The question of who your customer is may seem straight forward at first. What the Equifax Hack taught me is the answer isn't so simple.

In the eyes of Equifax, we are not the customer, we are the product. Yes they offer us a service to freeze credit, but that is no different than a distributed freezing an order due to a stock shortage. The product, our credit information, is the product and they will store it whither we like it or not. So we are not the customer. Their customer is is the one paying the $$ for that information. 

This model needs to be looked at for your application for various reasons. If you are writing an internal application for your company the answer may differ greatly in comparison to an external facing application.

Once you figure out who your customer is. Consider how tech savvy they are. A great application could be written on the command line very fast and cheap if your customer is able to use it. When you have to take the time to add a UI to that interface, the costs will go up. Need even more bells and whistles from the UI, you continue to add cost. The application needs to be developed to your users skillset. It is why git works best from the command line and Facebook doesn't have a command line interface (though people have).

## Know Your Developers
What skill sets are available to you? You may be a strong Java developer but if the majority of developers on your team are strong in Javascript, swallow your pride, and choose node for your team. 

Cost and time to market are very important. If you have developers spending too much time learning they are not writing code. Or struggling to write code which may end up as spaghetti later. Developers should always be tip-toeing the line between being out of their comfort zone and confused. A challenged developer will give you great results. A confused developer is going to deliver crap.

Make your decisions so the developer is always coming back for more and enjoying themselves. But not so much that they stress all day.

Another aspect of your developers you need to consider is how much protection your codebase needs. Do you have trustworthy develoeprs on your team that you never have to worry about the test coverage of their code? maybe you can skip adding any code coverage tools to the CI environment (for now anyway). Do you have code quality concerns from your team, maybe it is time to pull out [AirBnB Linter](https://github.com/airbnb/javascript) and [prettier](https://prettier.io/) to make sure the quality standards remain high.

Understand the trade-offs on when to add your quality tools. A young application may not require it for v1, but are you in a position to pay off that choices technical debt later. Way these choices in your mind. 


## Know Your Product
This one is pretty straight forward. If you do not know the vision of your product, stop trying to make architecture decisions. Stop and go understand your product.

## Picking a Languages and Frameworks

The language is an implementation detail. In the grand scheme of your choice, a strong software developer will be a bigger asset to your team than the language of choice. There is so much overlap in the technology these days that most languages are interchangable. Instead of taking a long time deciding on a language and multiple frameworks, take the time to develop your resources. Teach your developer's how to write tests, teach them the 4 Rules of Simple Design. Make developemnt easy on yourself. 

By knowing your Developers, Customers and your product 

You shouldn't need to be the smartest person in the room to understand your architecture. If you pick an architecture that takes year(s) to implement, and weeks to learn, you are causing yourself some grief. Not just for you, but your organization. Ask yourself what is the simpliest thing you can do to standup this framework. Identify your "gotchas" and edge cases and work from there.

If you are starting your application in the cloud. What is the simpliest thing you can do to get your application out there. Let's take for example a handful of rest endpoints. Where would I start?
 * Docker - I would choose this to get environments stood up quickly. The languages used inside is an implementation detail and we could flip flop between Java and node. Development could start while we pick the service that hosts the application. 
 * NodeJS w/ Express - I know my developement team knows node, so start with that. 
 * 1 Service per Container <Rule> - If we have any tech changes we have to make in the future, we can switch without impacting prior work. We didn't put all our eggs in one basket. Pivoting is easy

Now you are at a place where devleopers are developing and you are choosing your hosting provider. Since Docker is flexible and can be deployed almost anywhere you have a good start. Do you need to scale out to a larger architecture later? Docker allows for that too. If your team is segmented in the language of choice, some can work inside JAva docker containers and other nodeJS. 

## Vetting Packages and Modules
In the Java and Javascript world, packages and modules reign supreme. Any newer language is going to be dealing with some form of package manager. How do you make sure what you pick is quality and will last the test of time. These are the criteria I look at.

  * Does it work?
    * Can you tust that the framework is reliable? Sites will do a great job of promoting their product, but do they work. 
    * Check if there are Unit tests. This shows that the developer cared. Do they do a good job of testing
    * If your use case is small, write your own tests, especially if the orignal framework lacks them. 
    * Example - If your application deals with money you will most likley be looking for something that handles floating point arithmetic properly. IF the framework you choose can't properly calculate `0.1 * 0.2 = 0.02` then you need to move on. I dont know how many currency packages I have looked at that will calculate this as `0.020000000000000004`. These are the show stopper. Know the usecase why you need the package so you can test it.
  * Is it secure?
    * If the package does something that opens you up to XSS it is a no go. Package will only work if on HTTP, show stopper.
    * Know the security context for your application and don't just put in anything because it works. 
  * Is there a clean interface?
    * How easy is it to work with. Given two similar packages pick the one that is easier to use. 
  * How popular is it?
    * There are a lot of similar packages out there. Do a search on currency on the npm site and you will see how many are really out there. 
    * NPM offers stats on how often a package has been downloaded in the last day, week and month. It is important to know that the more popular a package the more support there is going to be out there for you when you need help.
  * Active Development
    * Are bugs being worked on? When was the last release. If the package is left for dead, know that you will be left to fix the packages bugs. 
    * Can you look at the open issues in Github and find they are being discussed and worke on? lots of open issues and no invlolment from the author and community is a bad sign. 
  * Documentation
    * Have you ever found a wonderful product with no documentation? The find is rare. Documentation to me isn't about how to use the package, it tells me that the author cares about their product and has put thought into it. How do you find design flows in your work? I learn from when my tests and/or documentation tell me there are problems. 

## Lead By Example
Be the first one to raise your hand to do the first POC. You have the ability to affect change and future best practices. Other developers coming in on the ground floor may not know about testing, clean code practices, docker or other choices that were made. Learning from a small application is much easier than joining a mamoth stack later on. Apply the [KISS principle](https://en.wikipedia.org/wiki/KISS_principle) to your early work and strive to show your vision and passion on the product.

## Communicate
The #1 rule in any aspect of life. If you can't communicate with your team and solicit feedback you will fail. Architecture design and decisions are not just about you. Communicate well and be awesome