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
    * Just pick a framework.
3. Start with a simple unit test
    * Test a simple function or class
        * Setters and Getters
        * Simple function with well defined inputs and outputs