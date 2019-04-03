<!--bl
(filemeta
    (title "Ideas in This Book")
)
/bl-->

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