---
title: "The 3 S's - Self Documenting Code"
date: 2018-01-01
draft: true
description: "A multi-part series looking into why testing is hard and some tips you can use to get ready to test"
---
The golden standard for me in development are the 4 Rules of Simple Design and KISS (Keep it Simple Stupid). I believe many systems are over designed and more complex than they need to be. With all of the design patterns, SOLID principles, DRY, Object Oriented programming out there, a developer can get overwhelmed. Being able to rest on some very basic principles has helped me be very efficient at what I do. I believe a few simple rules are all it takes to transform a good developer into a great developer.

The 4 rules of simple design are 
1. Passes its tests
2. Minimizes duplication
3. Maximizes clarity
4. Has fewer elements

The 3 S's for me evolved from the fact that a lot of developers fail on #1. I was taught that these tests do not have to be automated and that any test is better than no test, but if the feedback loop on 2-4 is long enough, it wont be worth the developers time to clean up and make the code better. That is why if there is not a quck feedback loop on change the remaining arguments fall apart.


For many developers the barrier to entry into testing is hard. A lot of the information out there dives right into the testing part of things and skips some of the simple rules of testing. Many of the developers I talk to seem to all have the same problems: their code is too large, expensive to change or code has dependencies that make it impossible to test. With TDD, BDD, JUnit, RSpec, Jasmine, or any other testing idea/framework the choices are not always easy and can be intimidating for a new developer looking to learn more about testing. 

The 3 part series will dive into some ideas to help you write better code without any complications. For the series we will forget tests exist. Let's focus on how we can write our code so it is easier to read, easier to write and overall less stressful to change. After this series is complete learning to test your code shouldn't be so hard because you will hopefully have already written code that is testable. In the first part of this series we will look at self documenting code.



