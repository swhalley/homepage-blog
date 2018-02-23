---
title: "Writing Effective Unit Tests"
date: 2018-01-01
draft: true
description: "Tips to writing better unit tests"
---

Do you find yourself writing large unit tests? Or you dread making changes to your system because a failing test may take you longer to fix than the code itself? You aren't alone. There are lots of people out there who are maintaining code bases who face these problems every day. There is a good chance that while you are reading this that I am cursing at my screen (in passion not anger) because of a bad test. How do we begin to write and fix bad tests? The [Boy Scout Rule](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule) is a great place to start. Leave your tests cleaner than you found them and the world will be a better place.

Here are my tips for writing better tests.

## Quality over Quantity
I would rather see you write 5 really good tests than 100 bad tests. Focus on the quality of the tests you are writing. Make sure they add value. Skip testing the code that is too simple to fail (Looking at you getters and setters) and spend some time really testing the code that matters. 

If you work on an application that requires X% of code coverage in your tests, then you are probably staring at a lie. Code coverage in tests does not tell you how effective your tests are, it simply tells you that a line of code was covered in the test. If you have a low threshold (70-90%) There are many scenarios you can miss by doing this. And what is that 10% that is missing? Is it ia getter/setter? or is it prime business logic? Be careful in what you test and don't rely on code coverage tools to tell you that you did a good job. On the flip side, I do believe code coverage isn't all evil. For those new to testing it is a good way to force themselves to test more than they normally would. Put you out of your comfort zone and test more. This is one of the few good benefits I see. 

## Create a Test List
Keep yourself organized by taking some time to create a test list. Know ahead of time what you want to test. The test list should be something that you can quickly change and append to. I find synching to Pen and Paper will help you. I keep notebooks and index cards handy for testing. Create quick notes and reminders while you go. As I am writing a test I may think of another scenario I forgot to test. Dont stop working on your existing test, instead quickly add a note to come back to later. Stay focused and organized on the test you are writing and trust the test list you create. 

Test lists dont have to be fancy, a simple "parameters in" and "expected outcome" can be enough to get your through a lot of tests.
Example
```
Pretend Doctor Test List

cough, running nose = cold
fever, fatigue = flu
headache, chronic fatigue = has kids 
```

## Name Things Well
  * Spend some time and give your tests a good name. A good solid name helps you understand what is being tested and the gaps in your test coverage
  * Name Format - [UnitOfWork_StateUnderTest_ExpectedBehavior]

### Structure Tests
  * Setup
  * Act
  * Assert

### Write Assert First and work Backwards
  * Doing this you will write less code to setup tests, be to the point, and wont get lost as often in your tests
  * This, along with Test Lists may be the single most important ways to improve the efficiency of your unit tests

### Fail your test before passing
  * You want to see your test fail before passing. Make sure it can fail
  * flip the assert() to see it fail

### Don't Test too Much
  * Make sure you pick the proper scope for your test
  * If the test is too big, this indicates you are either 
     * Testing too much
     * you have a code smell

### Humble Object
  * If a class is too hard to test, there is a change you can refactor out a humble object which may simplify your tests
  * Humble Objects are mostly identified on the ends of your application. Dom, Services, Entry points to your appication are normally the hardest to test
  * Create an abstraction on the hard parts to test. These new abstractions are your Humble Objects

### Refactor Tests
  * Because a unit test is working, does not mean it isn't fragile or hard to maintain. Take time to refactor the test after you are done to ensure it is easy to read, well structured and easy to maintain.
  * Boyscout Rule
  
### Don't use try/catch in tests
   * Frameworks will fail your test if an exception is thrown. Utilize this
   * try/catch with a print statement consumes the error, hiding and possibly never testing your asserts
   * see "Fail your test before passing"
  
### Don't violate Law of Demeter
   * http://wiki.c2.com/?LawOfDemeter
   * If your unit tests have to reach through objects to talk to other objects you are not writing unit tests. Test the simplist thing possible. 
   * When mocking and stubbing, do this one level away. don't reach through to other objects to try and mock/stub. these tests are expensive to maintain. I want to stub my dependency not my dependencies dependency. 
