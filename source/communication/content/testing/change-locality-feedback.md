<!--bl
(filemeta
    (title "Change Locality Feedback"))
/bl-->

As code changes, we run our tests in order to receive information about any changes which are unexpected.  This real-time feedback is what makes tests living documentation. The aspect of change communication is especially useful when we get information about where the change occurred.

We will refer to the identification and communication about where a change exists as _change locality._ When a test provides accurate insight into the change locality, it becomes easier to identify and debug in the production code.  This kind of speed to debugging is critical to improving speed and accuracy of software development.

Of course no test can provide perfect, accurate change locality feedback. This means there will always be a tradeoff between accurate change locality feedback and integration level of the test in question.  I propose there is an inverse relation between integration and change locality feedback which can be stated as the following:

_The greater the number of code integration points exercised under a single test, the less a developer can know about the locality of a single change._

It is reasonable to want tests which verify code integration. Integration and end-to-end tests verify an application runs as expected using live integration points, data, system IO, and so on.  What this law tells us, however, integration tests are not sufficient for building satisfactory living documentation.

In fact, no single level of test abstraction will serve all needs for all test communication. It is neccessary to choose and support a number of different types of tests at varying granularities.  For the purpose of testing and feedback, a type system can be viewed as a form of ultra-granular test.

When we look at tests we will dive into the various levels of granularity and what valuable feedback each provides.  We will also explore different kinds of testing and how those types of tests can create a rich tapestry of documentation and just-in-time feedback.