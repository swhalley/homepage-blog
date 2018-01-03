---
title: "Naming Rest Services - Goldie Locks and the 3 Bears"
date: 2018-04-01T01:14:36-03:00
draft: true
---

Naming is hard. Developers tend to move fast and not spend much time on naming. I wonder how many have been taught a good naming game to help design evolve and be clean. Names should evolve and many ideas should be thrown on the table when trying to name properly. REST and other endpoints are important to get right as they are the public facing API for your data and can be expensive to change (better to alias).

To help out with naming we will look at "Goldie Locks and the 3 Bears".

If you try and develop a rest endpoint for this, most developers I know and have worked with would do something like `/goldiLocks` and move on (typo intentional). months down the road they would start to realize that the name wasn't the best, and that typo would be propogated all over the place. The story evoloved over time and now the original name is just not enough. 

Treat your naming like a story. Especially when it comes to rest. What is written on the cover of your book is the name of your service. The Author, year of publishing can be meta/header data. So then how does this title evolve. My next iteration would be `/goldieLocks/and/the/3/bears`. Great now my rest endpoint reflects the title of the book. But can we improve further? Of course we can. 
`and` is a conjunction and `the` is a definite article. If we drop any similar names from the endpoint we still tell the story without that extra noise. `/goldieLocks/3/bears/`. To avoid confusion that we have 3 goldilocks, lets flip a few things around. `/goldiLocks/bears/3`. 

Last, but not least, we have a variable number of bears. Lets pull that out in case we ever need to support multiple numbers of bears. `/goldiLocks/bears/:numberOfBears:`. 

This plays well into a major/minor scheme in the name as well. Goldilocks is our key player. The bears the supporting cast. When we are performing naming games take the time to identify your actors and what role they play. Are they a major or minor player? If you identify two major player in the name, are you doing too much in that service? should it be broken up more?.