---
layout: post
category: thoughts
title: Research vs. production coding

---

I spent years as an academic research fellow, and part of my job involved producing code as well as papers. I thought I was a pretty decent developer. Then I moved into the tech startup space (at Signal) and worked closely with some seriously good software enegineers, who were kind enough to help me learn alongside them. 

In a commercial environment, "test driven development" (TDT) means writing the tests first, then writing the actual code until all the tests pass. This works fine but only if you know the end result you're heading towards. If you have a full spec of the component you're developing, and you just need to churn out code till you get there, this is fine.

But "research coding" tends to be exploratory, so you don't know what the result should be until you've get there. The goal you're heading towards is much more high-level and ill-defined. 

One aspct of a lot of data science is to explore data, to explore methods and algorithms until you've learned what is possible -- and to then turn that into high quality production-ready code. So one hybrid approach that I've found useful sometimes is to do the exploratory research coding, then write a formal set of unit tests, and then refactor the code so that it a) still passes the tests and b) meets other criteria (e.g. performance, readability, colloquialisms). This is better than never writing those tests!

But sometimes, it's worth going further: instead of refactoring the inevitably messy exploratory code, it can be better to start with a blank page. The outcome of the exploration is <i>not</i> a first draft of your code, but rather the learnings about what is possible and practical. So do the exploration, then write a spec (even if only to clarify your thoughts), and then switch to TDT mode.

