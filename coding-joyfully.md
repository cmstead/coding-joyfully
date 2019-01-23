
# Coding Joyfully #
#### The Art of Mindful Software Development ####

## Table Of Contents ##

- [Section 1: Introduction](#user-content-introduction)
- [Chapter 1: Communication](#user-content-communication)

## Introduction ##

At the point in my career where I began work on this book, I have been writing software for more than 20 years. In the time since I started my software journey, lots of technical books have been written about the concepts of clean code, refactoring, patterns, pragmatic practices, and so on. As can happen with any career, I have experienced my share of ups and downs.  I have enjoyed jobs only to have my experience sour.  I've worked in languages and then found myself driven away from the community for one reason or another.

Through all of this experience, I have considered myself a passionate programmer. I enjoy solving problems and I often go on a search for new things people might need to make their job easier. This particular search led me down the path of creating open source tools.

Many software developers I have met started their journey because they played video games and wanted to create them.  This couldn't have been further from my story.  In high school I was a passionate musician.  I played multiple instruments -- some with more skill than others -- and I wanted to share my love of music with the world. I was fortunate that the, now long defunct, Geocities was there for just such a budding enthusiast such as myself.

Since I never had the desire to write video games, my desire to write software was always centered around creating something useful, or at the very least, better than what I already had. This ultimately paved the way to creating tools I could share with the community.  I found the tools I created to be most interesting to others when I was scratching an itch I already had.

At this point, I center much of my open source development effort around creating tools which make software creation more joyful. Although the notion of joyful creation had resonance for me, other people didn't seem to quite understand what I valued and why it brought me joy.

Through trial and error, I discovered that what seemed to bring me the most joy while creating anything, software related or not, was the mindfulness that arose through a sense of understanding what I am doing and where my work is leading me.

This book aims to explore the way I approach what I consider "mindful software development" and how what the facets are which make mindful software development possible.

It is worth emphasizing now, this book is not intended to argue that my approach is the "one true way," or any such silliness.  Instead I hope you come away with a sense of how each of the ideas I present works toward making software development a mindful, joyful experience.


### Language In Example Code ###

The language I work in most often is Javascript.  I am using this language in the example code throughout the book, not because I believe it is inherently better than any other language, but because it is the language I write most fluently.  Aside from my personal fluency in a language, it is common for people who write in a variety of different tech stacks to encounter, and have to write, Javascript.

I believe the ideas presented throughout this book will be applicable to most languages programmers are working in today.  Some of the tooling may be better or worse for a given language, but what better reason for you to take up the mantle and make the coding experience more joyful for the people in your community?
    
    

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

    
    

    