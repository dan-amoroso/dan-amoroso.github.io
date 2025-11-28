+++
date = '2025-08-14T17:33:40+07:00'
draft = true
title = 'Craft the Business Rules, Vibe Code the Ui'
+++

After shipping some code with agentic IDEs I came to the conclusion that the best way to use them, for me, is to apply my limited attention resources to the business rules and then use them as a core kernel to "vibe code" the rest.

I use "vibe code" very losely here, since I keep a tight control over the codebase. Nothing goes in that is not tightly reviewed, and the LLM is only allowed to make very small changes at a time.

That being said, I find that once the main components of an application (sometime a few classes, sometimes a few microservices) are created, the LLMs give me less of a hard time filling in the voids all the way up to the UI.

I think of it as carefully building the fundation and then letting the model do its thing - supervised and held to the "termodinamics" of tests - based on that so that a usable 'house' gets built. 
I write the backend of a serice, think about what I would like the UI to look like, and slowly spoon-feed the ideas to a model until I get a usable UI.
As a solo backend developer that dabbles in full-stack only because its the only way to get a product out to the world, this is an empowering workflow that puts me in a familiar scenario I experienced often as part of a team, working in a company.

I put a very strong separation line - both conceptual and architectural - between the code I write myself and the code that is handled by the agent. 
We don't work on the same repositories, and I consider anything vibe coded basically throwaway. Nothing important is allowed to depend on the vibe coded stuff.

Sometimes the agent takes a while to get the tests to pass, and I often spend that time thinking about whats next, writing blog posts or - more rarely - preparing the backend for whats the come.
