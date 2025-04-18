Testing:

Last year, at a software conference session Q&A, someone else asked a really good question.

"How do you start testing when you have none?"

[Video link](https://mediaspace.esri.com/media/t/1_274g6nh3/325483122)

Jump to about 59 minutes in that video to hear when it is asked and for the response.

I was in the audience there and I really liked this question.  I have dealt with this situation before.  Working in a legacy code base with only manual testing, then adding the first few automated unit and integration tests.

TODO add modified testing pyramid and london/detroit testing schools pictures.

Here are my steps for success:

1. Figure out what is preventing testing.
    * Social
        * Management feature crush preventing taking time to add more tests
        * Schedule crush
        * Developer experience level
    * Code
        * Complexity
        * Legacy
        * Untestable patterns
        * Existing issues
    * Test Infrastructure
        * Makefiles
        * Run scripts
        * Unit test main function
    * Tests
        * Test framework complexity
        * Lack of experience
        * Unique syntax
2. Choose a unit testing framework
    * Unit testing frameworks make testing easier
    * Ask the other developers what ones they have used before
    * Find a survey where developers tell what framework they use
        * [Jetbrains Developer Ecosystem 2023 is excellent for this](https://www.jetbrains.com/lp/devecosystem-2023/)
        * [c++ section](https://www.jetbrains.com/lp/devecosystem-2023/cpp/#cpp_unittesting_two_years)
    * Do not home make your own testing framework.  If you were not able to get testing beforehand, what makes you think you can maintain a custom testing framework?
    * Just pick a framework.  My recommendation is to pick the most popular one
3. Start with a simple unit test
    * Test a simple function or class
        * Setters and Getters
        * Simple function with well defined inputs and outputs
    * Follow simple Assemble, Act, Assert
    * Find a guide for your testing framework
        * Coworker, course, blog, Youtube/conference talk?
4. Wire up test infrastructure
    * Makefiles
    * unit test main functionality
    * Run scripts
    * Code coverage
    * Share initial tests with your coworkers
5. Test the most difficult code you have
    * This code is likely tightly coupled with other code in your project
    * Draw out what the code does on a whiteboard
    * Identify seams/interfaces where you call that code and isolate it
    * Use dependency injection to insert mock objects for dependencies
    * Share these tests with your coworkers
    * If you fail, test something of moderate difficulty and try again
6. Address the social issues
    * Management time pressure / Customer Schedule / New feature
        * Coding without tests introduces risks
        * Testing will prevent regressions with the existing code
    * Developers that do not know better
        * Fresh from college or converts from other industries or engineering backgrounds that do not know how 
        * Help show them how to test their code
    * Developers that should know better
        * Have been developing since before surge in testing popularity
        * Test the code once when they write it and the tests do not persist in the code
        * Write code too tricky to be tested
        * Show these developers the worth of testing, force them to test their code.
        * Some developers may need a direct order to write tests
7. Enable testing everywhere
    * Add first simple test cases for every class
    * Peer program with coworkers to add tests for their issues
    * Cherry pick new hires first issues to be testable

* Testing side benefits and options
    * Accurate SLOC/Coverage
    * Feedback from customers/manual testing to automated testing
    * Test Driven Development (TDD)
    * Bisect when problem was introduced
    * Performance Profiling
    * Dynamic Analysis
        * Code sanitizers
            * Undefined behavior
            * Address violations
            * Memory leaks
            * Thread safety
        * Valgrind
    * Fuzz testing
    * Mutation testing
* Lessons learned
    * Set up Continuous integration / Continuous Deployment
    * If you make changes to test case infrastructure, change a test cases to intentionally fail and verify that the build still fails
        * Common example is once you have enough tests that an early failure scrolls off your terminal, so you add a pipe to tee command so that the logs get saved off, but the pipe quietly ignores the return value from the tests failing.  So the failure does not propagate properly.  Then later on a real failure starts occurring and you do not know about it.
        * If you already have tests and are reading this for pure curiousity, go invert a test assertion so the test case fails, then see if the failure propagates properly to stop the build.
    * Isolate test cases properly
        * Write scripts to run each test case individually
        * Write scripts to find test case interdependencies
            * Find a test shuffle seed which induces failures reliably, then bisect to find which other cases induce the failure
    * Have contractors deliver their test cases
    * Brag about testing improvements
        * Why do you think I am writing this