<!--bl
(filemeta
    (title "Getting Feedback from Tests"))
/bl-->

During any automated test run, there is an expectation that the tests will expose unexpected behavior in the code.  This kind of information can be viewed as test feedback.  Test feedback comes in a couple of different flavors which we can call _change identification_ and _change proximity_.

Change identification feedback is, essentially, what happens when a test fails.  When a test fails, output is logged and, typically, the name or description of the test is linked to the identified failure.  Change proximity feedback is the output from the test which provides the information we need to start using our deductive skills.

<!--bl
(subsection-minor "./source/communication/content/testing/change-identification-feedback.md")
/bl-->