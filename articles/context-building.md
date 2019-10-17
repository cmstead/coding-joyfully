# Context-Rich Source Documents #

There are two distinct times you have the opportunity to build context around the problem you are working on, when you start a new project, and when you engage with existing code.

I've worked on several greenfield projects since my career began and the level of success I have had in each project has been directly proportional to the amount of domain context I had going into the work.  The more I understood about the domain, the better my software ended up working.

There are many techniques which can be used to gather domain context and in most of the projects I have been on, we have used none of them. This wasn't from hubris or intentional disregard. Neither I, nor my team, actually knew how to better gather context at the time.

With this lack of tooling, we all did the best we could. Some of the earliest projects I worked on, I had very few development skills either, which made the entire situation pretty bleak.  Those were dark times.

There came a point, about a decade ago, when I became aware of tools like Test Driven Development, code modularity, names, and more.

I distinctly recall one job, where I worked with a team, some of whom were bought into the idea that automated tests were worthwhile and some who fought against them until they left the company. This mixed dynamic, coupled with the fact that we were trying to do TDD on client-side code, which was still a relatively new idea, made the entire experience of getting and keeping code under test a challenge, even for the deeply TDD religious, like myself.

As I learned more about testing and the kind of context clues that could be captured in tests, I started looking for anything I could use to better maintain context in my code.

The problem, as it turns out, is that humans are particularly ill equipped to build and maintain large amounts of contextual information while writing thousands of lines of source code. The more I captured the context I cared about in code, the easier it was for me to work in the same codebase later.

## (Re)Building Context ##

Looking back over the last decade or so, I have managed to learn a thing or two about capturing and housing context in the code. The entire endeavor began with automated tests, but as I learned more about declarative code, domain specific languages, and the like, the more I wanted to use these tools to work for me.

It is worth noting, depending on your approach, capturing context in code pays out almost nothing when you first write the code. There are developers who agonize over exactly the right name, test description, or comment, and it takes them hours to get functioning code written. Other developers simply write something, then improve it later.

Originally I was more like the former, assuming I had to get it right on the first shot. Everything must be carefully thought through, designed, and crafted from the moment my fingers touched the keyboard.

Now I fancy myself more like an ice sculpter who first attacks the block of ice with a chainsaw, then refines the rough shape appropriately. Only the people I work with could confirm or deny this.

The lesson I learned from all of this is, development is more like writing a book than building heaps and gobs of logical structures. The typical process for building context-rich software goes as follows:

- Get some ideas down and just generally get things up and running
- Edit
- Edit
- Edit
- Edit.

The trick is in editing with purpose. Let's take a look at what we can do.

### Tests ###

If you are a TDD practitioner like myself, you probably have a test written which reads like the following:

"Widget x should not burst into flames when I set the threshold to 5"

With this, you probably have a whole bunch of test code that initializes the widget, gets the fire extinguisher ready, and then sets the threshold to 5.

Now, unless Widget x is the specific name of a product your company produces, we can probably work on something better there.

Next, is bursting into flames a feature? Perhaps not. So, unless this test is a corrective test to deal with a problem discovered by the Underwriters Laboratories, maybe we can say something more useful about what happens when the threshold is set.

Looking at the threshold value, is five an important value? Is it the maximum threshold value, or is it just a value selected at the time to get the widget under test? Since this is my made up scenario, I'm voting that five is arbitrary and not a specifically interesting value.

Finally, we can reorganize this entire description as a mix of event and command language. This means we can declare an event occurred and then test that the internal workings, we'll refer to this as command behavior, behaved as expected.

Since we are writing a test, it is safe to say the event is actually a fact.  Each time the test is run, the setup and execution of events will always be the same, so they are factual.

In the end, our aim is to create descriptions which match the following form:

**If event fact happened, then context-related input produces context-related output.**

So, let's take a look at what our improved test description could look like.

"If XWidge threshold was set to a safe value, increased input amplitude does not trigger a combustion warning"

Though this description is somewhat lengthy, it tells us exactly what the conditions of the test are, how our test will interact with XWidge and what the outcome is that we expect. This entire statement is now rich with context, which will lead the next developer toward asking questions about the business instead of simply thinking about the underlying implementation.