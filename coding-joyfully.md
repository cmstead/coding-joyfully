
# Coding Joyfully #
#### The Art of Mindful Software Development ####

## Table Of Contents ##

- [Section 1: Introduction](#user-content-introduction)
- [Chapter 1: Communication](#user-content-communication)

## Introduction ##

Throughout the course of my career I have had many epiphanies. Typically these opportunities come on the heels of changing the way I approach a problem. The biggest challenge I had to overcome was how I could change the way I work or learn in order to trigger the next epiphany.  This book is the best distillation I could compile at this point on what triggers learning and understanding for me and others I have worked with.

One idea I have played with recently is liminal space. Without doing a deep dive, liminal space is a place between "what was" and "what is next." This liminal space, as applied to software, is a current idea on how to trigger new discoveries in thought, learning and problem solving. Effectively, if a developer is constantly pushing against the boundaries of what they know, they are more likely to uncover something they didn't know before.

All of the ideas in this book are intended to either free the developer from mental clutter, or provide ways in which to push the boundaries of their thinking in order to generate mental liminal space where seeds of discovery may be planted. With this in mind, this book will not provide a "single true way" to ascend to the the heights of the greatest programming minds. Instead consider this book as an exploration of ways to change perspective around code to facilitate learning and greater insight.


### Code Is For People ###

It is worth noting code is not actually for computers. I know there are people who aregue otherwise, however, it is relatively easy to disprove the notion that code is for computers.  If code were for computers, we would still be working directly in binary or hexadecimal.  Even assembly code is designed to be readable by people rather than computers. The structure of a modern programming language is designed around written human language, and the most popular languages currently are all centered around English.

Even when we look at a programming language as foreign as APL, it was designed, not for typing, but for writing on a chalkboard. This means APL was actually designed specifically with human ergonomics in mind first and foremost.

We can assume, then, that people are intended to both read and write software as a coded document. Write-only software is antithetical to the very nature of the human condition, which leads us to desire communication and the ability to build a mental model of the system we are trying to design and develop.

Mindful software development is founded in the notion that people will undertake software development and design framed around communication, context, and understanding. Instead of simply hacking in a solution and crossing our fingers that everything will work out okay, we will approach software considering the next person who must maintain it. I have seen too many instances of software created with the intent of being a short-term solution, become a large system which the entire business relies on in order to function day to day.  This is the case where mindfulness can be overlooked, generating a tremendous amount of cruft and design anti-structure left in the wake.
    

### The Kerney-Larsen Effect ###

**Emotion is stored in code as it is written.**

The Kerney-Larsen (abbreviated KL) effect can be observed as people work through code which was written at an earlier time, as opposed to code actively being written now. Since your emotional state is precisely what it is at the moment you are writing code, it is unlikely you can control what emotional information will be captured in the code at first writing.

Since this effect describes the past-tense capture of emotion, the goal is to understand what state the previous programmer was in when the code they wrote was created.  This understanding would, ideally, provide a sense of empathy, which makes it easier to refactor the code without assuming the prior programmer was incapable or hostile.

Refactoring within the context of the KL effect can be viewed as writing, rather than editing, which means new emotions can be captured in the code, and old, potentially negative, emotion will be removed.  This means code which was written in a state of anger, fear, anxiety or confusion, can be retooled to not only capture context, but convey a sense of calm, or even joy.

This book assumes the KL effect will impact your development experience and uses the outcome of captured emotion as a tool to help inform us on how we might move forward with better understanding and a richer context than we had going in.
    

### Ideas in This Book ###

Through the course of this book, we will explore several different ideas around building software and the kinds of work which can be done to make the coding experience mindful.  Through this mindfulness, hopefully coding will become a joyful activity which can be pursued both at work and, if you are so inclined, at home.

#### Context Building ####

Building context and understanding what the aim is of any line, object, or module is critical to building software which works and can be maintained over time. This context can either be centered around development patterns or around a business domain.

In this section we will explore how tests can be used to define and develop context. Tests are not required to be written perfectly the first time, instead they should reflect the constantly changing nature of the context from which our code is emerging.

Types can be used, not only to ensure continuity in use for behaviors, but also to provide visual context around the domain language and associated values the previous developer intended to use.  When types and evolved tests are used in concert context becomes clear quickly.

Finally, we will look at refactoring and how it can be used to capture context in our code as well as in our tests. It is quite common for automated tests to be written in the same language as our production code, which means any tools we use to manage our code will be equally useful for managing the code defining our tests.

#### Communication ####

Once we have a means to construct context within our code, we want to communicate in a rich way.  The communication which we build into our code should not only provide context around the localized development work being done, it should lead you from where you are through the code to where you want to be.

In information architecture, there is a concept called wayfinding.  Peter Morville talks about this in depth in the book "Ambient Findability."  Our code should work to emulate the kind of wayfinding and findability designers aim to produce in their work. This will help lead future developers to the information and context they are seeking.

Tests are some of the most critical communication devices we have for providing information about intent and API consumption. Through writing and refactoring tests, we will create a meta-communication layer which will inform developers about the underlying code and develop useful patterns which can help guide the development hand.

Communication is also nothing without a discussion.  As we explore communicating through code, we will start looking at how the code communicates back as well. We will explore automated tools which can help guide the creation of deeply communicative code. Through linting and the compilation step of a statically typed language, we will see how the code can communicate deep knowledge contained within.

#### Heuristics ####

#### Code Sensing ####

#### Changing Code ####
    
    

## Communication ##


### Software is for People ###

One of the most important aspects of any software project is that software is always intended for use by people.  This does not mean the general public is going to directly consume a print driver directly from a terminal session. It does mean someone, somewhere, is going to have to actually use the thing you wrote. Even more likely, the person who will end up using it is you.

In my day job, I work in application development, so everything I write either directly, or indirectly, impacts a customer somewhere in the world.  When I write tools for developers, I aim to make the development experience better for at least one person, often me.

Understanding our work impacts people means we must, at least at some level, communicate with the people who interact with what we create. We might send an error message, or we might actually create a full user experience.  Sometimes the communication is a document on the web and sometimes, as is often the case in what I write, the communication comes from a test suite.

Before launching into the nuts and bolts of mindful software development, let's explore the idea of how communication works in the code we write every day.
    

### Testing ###

There seems to be a never-ending debate about the value of automated tests, whether they provide value and when they should be written.  I will explore how to write tests which communicate later, but for the moment, let's explore the real value we gain from writing tests, communication.

An automated test suite provides two distinct kinds of value for the programmer: feedback when something breaks or changes, and information on how to consume the API under test.


#### Tests as Documentation ####

It is common to consider tests, primarily, as a way to ensure production code behaves the way it is supposed to.  Though this kind of feedback is important as code changes, tests in a static system also provide vital communication.

Any test suite communicates information about how the underlying system currently works and which way is best to interact with it. If the tests are built around a public API, they can provide vital information to the people who will consume the API.  Likewise, if the tests are around some internal unit of functionality, anyone new to the system can use tests to better understand how the internals work.

Any test which provides useful communication needs to be constructed in a way that it can be interpreted by others who encounter it.  This means the more meaninful each line of code is, the more useful the document becomes.

It is vital to look at tests, first, as a document.  Much like any other executable code, the code we write is not the program the computer executes.  Even interpreted code goes through a transformation, so code really is, almost exclusively, the domain of people.

    

#### Getting Feedback from Tests ####

During any automated test run, there is an expectation that the tests will expose unexpected behavior in the code.  This kind of information can be viewed as test feedback.  Test feedback comes in a couple of different flavors which we can call _change identification_ and _change locality_.

Change identification feedback is, essentially, what happens when a test fails.  When a test fails, output is logged and, typically, the name or description of the test is linked to the identified failure.  Change locality feedback is the output from the test which provides the information we need to start using our deductive skills.


##### Change Identification Feedback #####

In order to get the best change identification feedback possible, it is important to think of our tests as living software documentation. The way our tests stay alive is that we run them often and use the output to ensure our software continues to work as expected.  This means test names, descriptions and error messaging be as clear and domain-related as possible.

In the time I have worked as a software developer, I have written tests which had terrible descriptions and wonderful descriptions.  The way I differentiated the two is how much context I could regain later when I was working for figure out what broke and why.

It is fairly common to see tests which look like the following:

```javascript
describe('helper utility', function () {

    it('converts a string to a buffer', function () {
        const expectedResult = [ '77', '121', '32', '83', '116', '114', '105', '110', '103' ];

        const result = conversionHelper.convertValue('My String');
        const resultArray = result.reduce(function(result, charValue) {
                return result.concat([charValue.toString()]);
            }, []);

        assert.isTrue(result instanceof Buffer);
        assert.equal(JSON.stringify(result), JSON.stringify(result))
    });

});
```

This example leaves a lot of communication out in the cold.  It's not clear, without reading the every line of the test case, what call does the conversion.  Moreover, we can't clearly discern the module we want to work with by the top level description of the test. There are also deeper issues arount context and noisy code, but we will revisit those concerns in the next section.

Without going into how, I claim we can do better.  By making just a few changes, we can actually build a lot of context around change identification which will help us narrow down the culprit for any test breakages.

```javascript
describe('conversionHelper', function () {
    describe('string to hex converter - convertValue', function () {
        it('converts a string value to a buffer', function () {
            const expectedResult = [ '77', '121', '32', '83', '116', '114', '105', '110', '103' ];

            const result = conversionHelper.convertValue('My String');
            const resultArray = result.reduce(function(result, charValue) {
                    return result.concat([charValue.toString()]);
                }, []);

            assert.isTrue(result instanceof Buffer,
                'ConvertValue did not return a buffer!');
            assert.equal(JSON.stringify(result), JSON.stringify(result),
                'Converted buffer did not match expected output!')
        });
    });
});
```
    

##### Change Locality Feedback #####

As code changes, we run our tests in order to receive information about any changes which are unexpected.  This real-time feedback is what makes tests living documentation. The aspect of change communication is especially useful when we get information about where the change occurred.

We will refer to the identification and communication about where a change exists as _change locality._ When a test provides accurate insight into the change locality, it becomes easier to identify and debug in the production code.  This kind of speed to debugging is critical to improving speed and accuracy of software development.

Of course no test can provide perfect, accurate change locality feedback. This means there will always be a tradeoff between accurate change locality feedback and integration level of the test in question.  I propose there is an inverse relation between integration and change locality feedback which can be stated as the following:

_The greater the number of code integration points exercised under a single test, the less a developer can know about the locality of a single change._

It is reasonable to want tests which verify code integration. Integration and end-to-end tests verify an application runs as expected using live integration points, data, system IO, and so on.  What this law tells us, however, integration tests are not sufficient for building satisfactory living documentation.

In fact, no single level of test abstraction will serve all needs for all test communication. It is neccessary to choose and support a number of different types of tests at varying granularities.  For the purpose of testing and feedback, a type system can be viewed as a form of ultra-granular test.

When we look at tests we will dive into the various levels of granularity and what valuable feedback each provides.  We will also explore different kinds of testing and how those types of tests can create a rich tapestry of documentation and just-in-time feedback.
    
    
    

### Domain Language ###

    

### Refactoring ###

    

### Design Patterns ###

    
    

    