---
title: "What Are My Tests Telling Me?"
date: 2018-02-01T01:14:36-03:00
draft: true
description: "Unit Tests Aren't Just About Red, Green, Refactor"
---

<!--
I have made two kinds of edits in this post:
1. I reworded some sentences where the intent was clear. Because git diffs work weird with prose, the original text is in a HTML comment before the changed section.
1. I also added comments before sections where the intent was not clear, or the argument not strong.
-->

<!-- EDIT: Working with developers who are new to testing can lead to a lot of confusion as to what is the purpose of testing. For many, the argument is that it is just as easy to manually test the code than it is to write out a bunch of unit tests. -->
Developers new to automated tests are often confused to their purpose. 
Many argue that performing manual tests is easier than writing out automated ones. <!-- /EDIT -->
<!-- You're making the assertion that automated testing saves money without giving justification. Either elaborate here, or provide forshadowing to the section where you back this up. --> Yes, but why would I pay a developer to manually test an entire application when I could pay someone pennies on the dollar and outsource it? 
The many arguments against testing fall apart quickly but can be a difficult battle to change the culture of these developers.

Over the years of watching people learn to test, it became clear that developers would follow these phases in their learning pattern.

### Flat Out Refusal

This phase comes in a lot of forms, we could be staring at the 25 year vet who has gotten by all these years and doesn't believe they can improve their process or skills. We could also be looking at the university student who is moving to fast to really appreciate the need to test. There are a lot of developers in between who could benefit from testing but they just don't know why.

This is the toughest phase to move from. What I find with these developers is that people have just not taken the time to really teach them "why" we test. That 25 year vet has never written more than a few handful of tests (if any) in their career and are set in their ways. They don't want to learn new things. 

<!-- I might add an argument: because new developers are often just trying to get something working, they don't value tests because `robust` and `stable` stable are after thoughts to "Does it even run?"  --> <!-- There's just some tense issues in this paragraph -->
The university student is usually all over the place. They're learning so many basic things that they do not learn what they need to about tests. And if they do, they are in information overload and miss the "why" entirely. 

This is the longest phase in the development of a tester. How do you break the old habits or get them to slow down enough to appreciate it. For many of us we woke up one day and realized there has to be a better way. We take the time to embrace testing and its benefits. 

This developer may have heard about TDD and Red, Green, Refactor and believe this is the only benefit. 

### Try Some Testing

A developer wants to learn testing or mandated by their company to start. They fire up a JUnit or Jasmine guide and start looking at writing unit tests. At this point they haven't considered the quality of their code and get overwhelmed with testing their code. It may take the developer a day to write a single test. There is nothing wrong with this first experimental stage and I fully support it. Helping a fellow developer out of this stage is very rewarding. This step is your gateway "drug" into accepting testing. If working with a developer and I can get them to embrace writing tests, this is the phase where eyes get big and people start to see some benefits.

A developer may fail at this phase 2-3 times in their career before they can move on. Building up the confidence, appreciation and skill set for testing may take a few shots to get it right. The important thing for anyone reading this and wanting to learn, don't be discouraged if you have been in this phase multiple times. Many have been there before you. Hold your head up and keep pushing.

### Over Testing

So you have mastered JUnit and started playing with Mockito (insert your testing framework of choice). Testing has become easier for you and you can write very intricate tests. You are starting to realize you can stand-up your applications with a lot more confidence. At this point you are testing everything: Your Code, The Browser, that 3rd party rest api, the database. You have no limits because testing is becoming fun and showing some benefits.

In this phase you start to notice code quality standards are changing a bit but you don't know why. You may have even explored the [dependency inversion principle](http://blog.thecodewhisperer.com/permalink/consequences-of-dependency-inversion-principle) at this point. This is great, you are starting to realize your tests are telling you things, even though you don't know the what or why.

To get developers out of this phase, they have to realize a lot of their tests are very large and hard to maintain. There are no limits on what you test and some direction and review needs to be given to bring the developer back down to reality.

### The "Aha" Tester

And we finally get to the phase which is the point of this article. The "aha" tester has developed a lot of unit tests at this point and learns a lot about their tests. They see patterns emerging in how they write tests, they create patterns of their own and the intent of their tests are finally revealed. In my years of experience I have left a few code bases in a mess as I got to this point in testing an application.

At this point in your development, tests are coming fast and written much better. code quality is improving. You are delivering faster and producing much fewer defects. You realize you don't have to test if something is written to the dom, that test is the job of the browser. The [Test Pyramid](https://martinfowler.com/bliki/TestPyramid.html) is emerging and you have other types of testing setup for your application. Change is now less risky in your system and your business team is starting to buy into the $$ value that testing provides.

Everyone works at their own speed. So you may have gotten here in 6 months, or 25 years. The important part is that you are realizing that tests are much more than pass fail. Congratulations you are officially a tester.

## So What Were My Tests Telling Me All These Years?

Whither you are reading this because you are new to testing, learning about TDD, or a seasoned veteran you will know that testing is there to make sure your system is working. You want to reduce the risk of change, and unit tests are a great way to accomplish this. Let's look at other ways that unit tests help us get software to market in a safe and timely fashion.

1. Tests Are Documentation
  
    Your business team is maintaining a costly set of use cases or writing requirements in Jira. Your developers are keeping a wiki page page going with a list of contracts between systems. Your tester have a large regression test suite mapped out. But what if all that was unnecessary. With properly laid out and named unit tests the team will realize that the other efforts are duplication and can be retired. As a developer if I continue to evolve and maintain my tests they act as the business requirements, use cases and contracts. 

    A well named test can provide a lot of information without the reader needing to know any of the implementation details of the test or code. The standard in naming over the years has evolved into something like `UnitOfWork_StateUnderTest_ExpectedBehavior` or `Given_When_Then`, which to the reader should be a clear requirement on how the system should behave.

2. Tests Reflect The Quality Of Your Code
  
    Was your unit test hard to write? Were you able to get a unit test written at all? If this is the case, there is a good chance your code has some smell to it. If you are practicing test driven development you know that this is a point of feedback from your code. As your tests get more complex you know there is a problem in your design. 

    In my own experience when I find a test that is large or hard to maintain the typical pattern I see emerging is that the code is [tightly coupled](https://en.wikipedia.org/wiki/Coupling_(computer_programming)) or violates the [single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). Being able to write clean, decoupled code takes time. Let your test dictate your refactoring efforts. Start small and pick quick wins before diving head first into complicated refactors.

    This is the tip of the iceberg when it comes to code quality. Unit tests offer so many details about the quality of your code that it will require an article on its own. 

3. Tests Tell Us What We Missed
  
    A new ticket comes in and you have a new production defect. Oh No!!! Panic, clearly this isn't your fault. Let's take the time to run a git blame and figure out who's problem this is!!! Ok now breath, it is time for you to take ownership. How are you going to tackle this problem? Given that we already learned that tests are documentation, we can safely assume that we missed something in our documentation. 

    One of the most important things taught to me over the years is that a defect is just a test you have not written yet. Look through your "documentation" find the test that is missing and write it. Now you have a failing test that you can use to know when the bug is fixed.

4. Tests Act As An Organization Tool
  
    Do you find yourself trying to do too many things at once? Are you all over the place trying to implement everything at once? Use unit tests as a way to organize your thoughts. Write out a test list for yourself on paper or jump ahead and write out a list of test names in your editor. Take the time to organize your thoughts before you jump into the code. One big folly I see happening is trying to implement too many tests at once. Slow down and stay organized. Use your tests as a tool to stop getting ahead of yourself.

    Another good use as an organizational tool is understanding where you left off. It is Friday before a long weekend and you are already checked out and not wanting to think anymore. The weekend is going to be crazy and you know Monday morning you will forget where you left off. Take the time and write yourself one more unit test. This unit test will fail, but its name will tell you where you left off. Now Monday won't be so bad. 

5. Tests Keep You From Over-coding

    "Just in Case" code is a real problem. Developers add code in just in case a scenario may happen without understanding the requirements or data. Extra code be a major problem as it adds extra complexity and testing scenarios into the code. By writing good tests it forces the developers to understand the system. You eventually will question every test you write to know if it is really needed.


Now that you know some of the other reasons developers write tests you can have a better appreciation of the "why" in your argument for testing. The learning path through the phases should be accelerated as you appreciate more about what your tests are telling you. As a developer I had to learn these lessons to really understand why I was testing and helped me appreciate TDD more. My tests were no longer about pass/fail. They were my contract with the business team to make sure that what I was delivering was high quality. 

Each of these topics can spawn much larger discussions. I have a series of articles which will do a deep dive into a lot of these areas. But those stories are for another day. 

Thanks for reading,
{{< signature >}}
