---
title: "The Evolution of Architecture"
date: 2018-07-13
draft: true
description: "What we have learned from our past"
---

Architecture has evolved over the years, understanding where we have come over the years is important in understanding where we are now. Without understanding why we have gotten to micro-services, do you really know why you need to use them? Does your company even need them? Being able to associate risk and complexity in your application could make or break your project. Let's take a look at the history of architecture and try to find out where you stand.

# Spaghetti Code

This is where we all start out. We put code together, we hack around a bit and get it to work. When a second application is needed, we start from scratch or copy and paste some old code between our applications.

{{< figure src="/img/arch/spaghetti.svg" class="figures" >}}

Functions are long, there is no structure to the code. Figure out how to add features is expensive and we struggle with the high costs associated with change.

Spaghetti code is dangerous because as bugs and new features are added, if we are not careful, than issues of fragmented code bases occur. We end up with similar but very different versions of the same code.

**Pros**

- Simple

**Cons**

- Heavy Duplication
- Higher Maintenance Costs
- Hard to Read Code
- Large Codebase

# Patterns Emerge

A pattern emerging may be as simple as a model being written to describe an object or writing common code into its own function(s). It could be that the developer is introducing the MVC pattern into the application. In either case, structure and reason is starting to develop in the code.

{{< figure src="/img/arch/pattern.svg" class="figures" >}}

A lot of legacy systems exist in this model. (:wave: Mainframe developers :wave:)

With a little structure in the code, we can move the "Hard to Read Code" from a con to a pro. Code that is easier to read will help lower the maintenance costs. The cost will still be high as we deal with duplication and fragmented code.

**Pros**

- Time saved re-writing same code

**Cons**

- Heavy Duplication
- High Maintenance Costs
- Large Codebase

# External Repositories

With the emergence of external repositories (npm, maven etc) we now have the ability to store our shared code as modules in our own or external repositories. Team's making multiple applications can now share code between them and reduce the fragmentation what may existed by the old copy/paste methods.

{{< figure src="/img/arch/repository.svg" class="figures" >}}

The negative to this, is that every time a shared piece of code changes, we have to recompile all of the programs that depends on it. In your organization, this could be a substantial amount of downtime to get all of the code pushed out to your customer.

So even though external repositories have helped streamline the development process, the extra overhead to fix/deploy all of your applications may have increased.

**Pros**

- Reduced Duplication
- Reduced Maintenance Costs
- Large Codebase

**Cons**

- Compile the World

# Micro Services

Micro services are the proposed solution to fixing the downtime introduced by the previous phase. Now you are creating smaller applications. Either the application does work or controls work, but you strive for single responsibility within the service. With the cost of Network overhead being very small these days (especially in cloud solutions) asking your neighbor program to do work for you is much quicker.

By having many small services you reduce the complexity of each program which means less risk of defects, cost of change is reduced, and hopefully removes a lot of your duplication.

In the below diagram, if a change is made in the helper service, there is no need to recompile applications 1 and 2. Therefore there is no downtime for either application. The changes to the shared code is now invisible to the other applications.

{{< figure src="/img/arch/micro.svg" class="figures" >}}

Of course there is always a tradeoff. By having many small units of work, there is an extra overhead to get all the services deployed and talking to each other. There is a lot of work going on to help with the problem. Docker and Lambda have emerged to help with this problem in different ways. Each with its own set of complications.

**Pros**

- Higher Availability
- Many Smaller Codebases

**Cons**

- Complex Deployment Plans

# Conclusion

What sparked me to write this post is that I have worked with enough people to realize that what a lot of people strive for is micro services. But they fall flat on the "Patterns Emerge" step. The developer's have not taken the time to understand why micro services have evolved and why teams use them.

Without understanding why they chose micro services, they are going to add the cons from 2 different problems without moving anything into the pros column. What they end up with is many large services with a lot of duplication and complexity.
