---
toc: true
layout: post
description:
categories: [journal]
---
# Recursion vs. Iteration for 4 Year Old

Today, I had a phone interview for one of software engineering companies. I really like one of my answers to interview questions and want to introduce it here.

Question: How can you explain differences between the recursive and iterative methods to solve a problem to a 4 year old kid?

My answer was:

We have a russian doll, inside which a lot of (more than thousands!!) other dolls one-by-one and each of them has a unique name. Only one of those dolls is a boy and all the others are girls. We want to find out the name of the boy doll. How are you going to do this? 🙂

Well, I think we can do that in two different ways.

First, we can open up one doll at a time and until we see the boy. Then we can ask his name! Right? But then, we might need to ask the same question all day long and will get tired soon. 🙁

Instead, I think we can also find his name as follows. We don’t open up all the dolls and ask to each doll, but we ask only to the first doll if she has the boy doll right inside her. If she says yes, then ask her to ask his name to him and let us know. If she says, no, then ask her to ask the exactly same questions to the doll inside her, i.e.:

* if she has the boy doll inside.
* if not, ask the same questions to the doll inside.
* if yes, then ask his name and let me know.

Right?

We call the first way the iterative method, and the second way the recursive method.

Do you think a 4 year old kid can get the idea?
Or am I too demanding? 🙂