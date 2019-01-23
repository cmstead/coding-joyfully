<!--bl
(filemeta
    (title "Tests as Documentation"))
/bl-->

It is common to consider tests, primarily, as a way to ensure production code behaves the way it is supposed to.  Though this kind of feedback is important as code changes, tests in a static system also provide vital communication.

Any test suite communicates information about how the underlying system currently works and which way is best to interact with it. If the tests are built around a public API, they can provide vital information to the people who will consume the API.  Likewise, if the tests are around some internal unit of functionality, anyone new to the system can use tests to better understand how the internals work.

Any test which provides useful communication needs to be constructed in a way that it can be interpreted by others who encounter it.  This means the more meaninful each line of code is, the more useful the document becomes.

It is vital to look at tests, first, as a document.  Much like any other executable code, the code we write is not the program the computer executes.  Even interpreted code goes through a transformation, so code really is, almost exclusively, the domain of people.

<!--bl
(build-message "Communication > Testing: Tests as documentation is the current section underway")
/bl-->