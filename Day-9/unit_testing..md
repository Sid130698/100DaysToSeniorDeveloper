### What are unit tests, and why are they important?

*Unit tests are automated tests written to verify the functionality of individual units of code, such as methods or classes. They are important because they help ensure that each part of the program works correctly, detect bugs early, and facilitate code refactoring with confidence.*

### Can you explain the key principles of unit testing?

*The key principles of unit testing include:

* Isolation: Tests should be independent of other tests.
* Repeatability: Tests should produce the same results every time they run.
* Self-Validation: Tests should automatically determine if they passed or failed.
* Timeliness: Tests should be written early in the development process.*

### What is the JUnit framework, and how does it support unit testing in Java?

*JUnit is a popular open-source framework for writing and running tests in Java. It supports unit testing by providing annotations to define test methods, assertions to check expected outcomes, and test runners to execute tests and report results.*

### Can you provide an example of a simple JUnit test case?

*Sure, here’s an example:

<pre><div class="dark bg-gray-950 rounded-md border-[0.5px] border-token-border-medium"><div class="flex items-center relative text-token-text-secondary bg-token-main-surface-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md"><span>java</span><div class="flex items-center"><span class="" data-state="closed"><button class="flex gap-1 items-center"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24" class="icon-sm"><path fill="currentColor" fill-rule="evenodd" d="M7 5a3 3 0 0 1 3-3h9a3 3 0 0 1 3 3v9a3 3 0 0 1-3 3h-2v2a3 3 0 0 1-3 3H5a3 3 0 0 1-3-3v-9a3 3 0 0 1 3-3h2zm2 2h5a3 3 0 0 1 3 3v5h2a1 1 0 0 0 1-1V5a1 1 0 0 0-1-1h-9a1 1 0 0 0-1 1zM5 9a1 1 0 0 0-1 1v9a1 1 0 0 0 1 1h9a1 1 0 0 0 1-1v-9a1 1 0 0 0-1-1z" clip-rule="evenodd"></path></svg>Copy code</button></span></div></div><div class="overflow-y-auto p-4 text-left undefined" dir="ltr"><code class="!whitespace-pre hljs language-java">import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class CalculatorTest {
    @Test
    public void testAdd() {
        Calculator calc = new Calculator();
        int result = calc.add(2, 3);
        assertEquals(5, result);
    }
}
</code></div></div></pre>

### What are some common annotations used in JUnit?

*Common JUnit annotations include:

* @Test: Indicates a test method.
* @Before: Runs before each test method.
* @After: Runs after each test method.
* @BeforeClass: Runs once before any of the test methods in the class.
* @AfterClass: Runs once after all the test methods in the class.*

### How do you verify the behavior of a method using assertions in JUnit?

*Assertions in JUnit are used to check the expected outcome of a test. For example, `assertEquals(expected, actual)` verifies that the actual result matches the expected result. Other assertions include `assertTrue(condition)`, `assertFalse(condition)`, and `assertNotNull(object)`.*

### What is the difference between a unit test and an integration test?

*A unit test verifies the functionality of a single unit of code in isolation, while an integration test verifies the interaction between multiple units of code, such as different classes or modules. Integration tests typically involve more complex setups and dependencies.*

### Can you explain the purpose of the @Before and @After annotations in JUnit?

*@Before and @After annotations are used to define methods that run before and after each test method, respectively. These methods are typically used to set up and tear down test environments, ensuring each test runs in a clean state.*

### How can you mock dependencies in unit tests?

*Mocking dependencies involves creating mock objects that simulate the behavior of real objects. This is useful when the actual objects are complex or have side effects. Frameworks like Mockito are commonly used for mocking in Java.*

### What are some best practices for writing effective unit tests?

*Best practices for writing unit tests include:

* Writing clear and descriptive test names.
* Keeping tests independent and isolated.
* Testing both positive and negative scenarios.
* Ensuring tests run quickly.
* Regularly running tests and maintaining them as the code evolves.*
