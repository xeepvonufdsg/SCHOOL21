# UI Web testing (AQA)

In this project you will explore the most commonly used Java libraries for UI testing. You will get hands on practice with Selenide, the leading tool for automated UI web testing. Additionally, you will learn how to work with BDD tools and generate test run reports using Allure.

💡 [Press here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave feedback on this project.** It's anonymous and will help our «School 21» team improve the learning experience. We recommend completing the survey immediately after finishing the project.

## Contents

- [Chapter 1](#chapter-1)
- [1.1. General instructions](#11-general-instructions)
- [Chapter 2](#chapter-2)
  - [2.1. Introduction](#21-introduction)
- [Chapter 3](#chapter-3)
  - [3.1. Web UI testing](#31-web-ui-testing)
  - [3.2. Selenide](#32-selenide)
  - [3.3. Page Object pattern](#33-page-object-pattern)
  - [3.4. Cucumber](#34-cucumber)
  - [3.5. Allure](#35-allure)
- [Chapter 4](#chapter-4)
  - [4.1. Getting Started with the Framework](#41-getting-started-with-the-framework)
  - [Task 1. Working with Selenide](#task-1-working-with-selenide)
  - [Task 2. UI Test Configuration Specifics](#task-2-ui-test-configuration-specifics)
  - [Task 3. Transition to Cucumber](#task-3-transition-to-cucumber)
  - [Task 4. Integration with Allure](#task-4-integration-with-allure)

## Chapter 1

## 1.1. General instructions

How to learn at “School 21”:

- Here, you’ll find a unique learning experience with a lot of freedom. You’re given a task and left to find your own way to solve it, using whatever resources work best for you — whether that’s the Internet or AI tools like GigaChat. Just be mindful of information quality: verify, think critically, analyze, and compare.
- Peer-to-peer (P2P) learning is the exchange of knowledge and experience with peers, where everyone acts as both mentor and student. This approach allows you to gain a deeper understanding of the material by learning from one another.
- Feel free to ask for help: around you are peers who are also navigating this path for the first time. Share your own experience and ideas with others. Join Rocket.Chat to stay updated with the latest community announcements.
- Your learning is meaningless if you just copy someone else’s solutions. When receiving help from others, always make sure you fully understand the “why”, “how”, and “purpose” behind the solution. Don’t be afraid to make mistakes.
- Does the task seem impossible? Take a break, get some fresh air and clear your mind — this has helped many people. Maybe after that, the solution will come to you naturally.
- The learning process is just as important as the result. It’s not just about completing the task — it’s about understanding HOW to solve it.

How to work with the project:

- Before starting, clone the project from GitLab into a repository with the same name.
- All files should be created inside the *src/* folder of the cloned repository.
- After cloning the project, create a *develop* branch and do all your development there. Then, push the *develop* branch to GitLab.
- Your directory should not contain any files other than those specified in the assignments.

## Chapter 2

### 2.1. Introduction

Automation testing engineers handle diverse tasks. Once you have mastered API test automation, building automated web UI tests is the next high-demand skill.

In this project, you will learn to use the key tools that professionals use to automate web interface testing:

- Selenide — an elegant framework for browser interaction.
- Cucumber — a tool for describing tests in a language that is understandable even to non-technical specialists.
- Allure — a powerful visualization system for results (reports of automated test runs).

You will start with the basics of Selenide automation and learn how to write clean, stable code to interact with page elements.

Next, you will learn Gherkin syntax and practice writing test scenarios that are easy for anyone to understand.

Finally, you will learn to use Allure to transform dry reports into engaging visual dashboards with charts and screenshots.

If your goal is to professionally test web applications, this stack will provide you with a scalable, reliable, and industry-proven foundation.

Let's get started!

## Chapter 3

### 3.1. Web UI testing

Web interface testing verifies how smoothly and accurately users can interact with an application. Are all elements displayed correctly? Do the buttons, forms, and navigation work as intended? Does everything still function correctly if a user accesses the application from a different browser or screen resolution? In most cases, this involves end-to-end testing, also known as web scenario testing.

The classic approach begins with manual testing: a QA engineer clicks through the application, enters data, checks various scenarios, and logs any bugs found. However, as the project grows in complexity, more time is spent on repetitive checks, especially during regression testing. This is where automation comes in.

Automated web UI testing simulates user actions through code, opening pages, filling out fields, clicking buttons, and verifying that everything functions as expected.

There are, however, some challenges to consider. Factors such as page loading speed, dynamic changes in the DOM, and cross-browser compatibility can impact the stability of these tests.

To reduce risks and streamline their work, QA engineers rely on specialized tools:

- Frameworks, such as Selenide (which you will explore in this project), simplify browser and page element interactions.
- Gherkin syntax (used with Cucumber, which is also covered in this project) allows you to write test cases as clear, natural-language scenarios. While Gherkin is not yet as widespread as some other tools, its popularity is growing quickly, so mastering it can give you a real edge in the job market.
- Reporting tools (like Allure, which you will try out) transform automated test results into visual reports that highlight errors and provide detailed insights.

Automation isn’t about replacing manual testing but rather supporting it by handling repetitive tasks so engineers can focus on more complex challenges.

For this approach to succeed, it’s essential not only to know how to code, but also to choose the right tools for each project’s needs. More on that-coming up next.

### 3.2. Selenide

Selenide is a Selenium WebDriver-based framework for automating web interface testing. Its main purpose is to make writing UI tests simple, clear, and reliable.

Selenide handles routine tasks such as browser management, timeouts, and exception handling. This allows you to focus on the logic of your tests rather than technical details.

**Basic working principles**

1. **Automatic browser management**

Selenide automatically launches and closes the browser (using Chrome by default). To get started, you just need to specify your configuration in the code.

```
Configuration.browser = "firefox"; // choosing browser
Configuration.headless = true; // no-UI browser mode
```

1. **Searching elements**

The $ method is used to find page elements with CSS or XPath selectors.

1. **Automatic Waits**

```
$(By.id("login-button")).click(); // search by ID
$("input\[name='email'\]").setValue("<test@mail.com>"); // CSS selector
```

Selenide automatically waits for elements to appear, become visible, or become clickable (up to 4 seconds by default), so you don’t have to manually use `Thread.sleep()` or `WebDriverWait` in your tests.

1. **Assertions**

Built-in methods for validation:

```
$(".title").shouldHave(text("Welcome")); // text verification
$("#submit-btn").shouldBe(disabled); // element state verification
```

**Advantages of Selenide:**

- Concise syntax: Writing tests requires two to three times less code than using plain Selenium.
- Stability: Built-in waits and exception handling minimize false test failures.
- Integration: It works seamlessly with JUnit, TestNG, Cucumber, Allure, and other tools.
- Documentation: The official website offers detailed guides and practical examples to help you get started.

### 3.3. Page Object Pattern

The Page Object Pattern is a design approach in which each page of a web application is represented by its own class.

Within each class, you define locators for elements, such as input fields and buttons, along with methods for interacting with them, such as clicking or entering data. This reduces code duplication, makes tests easier to maintain, and improves readability. If the interface changes, you only need to update the relevant page class rather than modifying every test.

**Advantages for Automation:**

- Concise tests: Instead of writing a series of Selenide commands, you can call simple methods, such as `loginPage.enterCredentials()`.
- Encapsulated logic: The logic for interacting with each page is neatly packaged, which makes it easier for teams to collaborate.
- Seamless integration: Working with Cucumber and Allure means your scenarios are easy to understand, and your reports are detailed.

In short, the Page Object Pattern is the foundation for stable and scalable automated tests.

### 3.4. Cucumber

Cucumber is a BDD (Behavior-Driven Development) tool that enables teams to write tests in a format that’s clear to everyone in a team (QA engineers, developers, and managers).

Tests are described in natural language within feature files using intuitive keywords.

```
# language: en
Feature: User authorization
Scenario: Successful login
Given The user is on the login page
When They enter login "admin" and password "qwerty123"
Then The personal account opens
```

Here’s how this looks in code:

```
@When("The user is on the login page")

public void openLoginPage() {
    open("/login");
}

@Then("They enter login {string} and password {string}")

public void enterCredentials(String login, String password) {
    $("#username").setValue(login);
    $("#password").setValue(password).pressEnter();
}
```

**Why is this valuable?**

- Shared Understanding: Tests are written in a language that everyone on the team can understand, effectively turning them into living documentation.
- Reusable steps: Common actions, like "user login," can be defined once and used in multiple scenarios.

### 3.5. Allure

Allure is a framework for generating interactive, detailed reports from automated test runs.

It converts raw data, such as logs, screenshots, and metrics, into visual dashboards that make it easy to quickly pinpoint failures and assess the stability of your tests.

**How does it work?**

Allure integrates with your project through dependencies, such as Maven or Gradle, and special annotations. For example, when used with Selenide, Allure automatically captures screenshots whenever a test fails. With Cucumber, Allure displays test scenarios in the original Gherkin format for clarity.

You can enrich each report with additional context, such as:

1. Screenshots of errors (automatically captured by Selenide).
2. Request and response logs.
3. Labels, such as tags, severity, or epic, to help organize and filter tests.

Below is an example of how you might use an annotation in your code:

```
@Step("Enter login {login}")
public void enterLogin(String login) {
    $("#username").setValue(login);
}
```

After running your tests, you can generate a report with the command: `allure serve allure-results`.

What does the report show?

- Charts: overview of passed, failed, and skipped tests.
- Scenario tree: tests grouped by features, epics, and tags.
- Test steps: a detailed breakdown of each step, made possible by the @Step annotation.
- Attachments: screenshots, logs, and even videos (if configured).

**Advantages of Allure**

- Clarity: Even newcomers can easily see where and why a test failed.
- Flexibility: It works seamlessly with popular frameworks like Selenide, Cucumber, and JUnit.
- Simplicity: Generate comprehensive reports with just one terminal command.

**Conclusion**

Together, Selenide, Cucumber, and Allure cover the full automation cycle:

1. Selenide delivers stable, concise tests.
2. Cucumber allows you to write scenarios in clear, business-friendly language.
3. Allure provides clear analytics.

Now, let's put this into practice and write automated tests that work reliably and communicate their results in a way that everyone can understand! 🚀

## Chapter 4

### 4.1. Getting Started with the Framework

General recommendations for completing project tasks:

- Use Java 21 for all code.
- Place non-test components (helpers, functional methods, etc.) in the `src/main` older.
- Use the SOLID, DRY, and KISS architectural principles. Design objects to minimize future modifications and error risks.
- All tests must have descriptive names and include clear documentation via appropriate annotations.
- Every assertion should include a clear, readable error message.
- You’re free to use either JUnit or TestNG as your Test Runner — whichever you prefer.

By the end of this project, you will have developed a web UI test framework that leverages cutting-edge tools and differs from a production-grade version only in test coverage.

**A key skill for an AQA specialist: working with AI tools**

Another goal of the project is to help you effectively use modern AI tools to enhance your work.

**A critically important rule:**

1. First, complete the tasks manually—this is a mandatory requirement. Experienced specialists delegate tasks to AI only after they already know the solution themselves; AI is brought in to help optimize or generate similar work. Mark the results obtained manually, for example, as manual-solution.
2. After completing the task independently, implement it using AI—mark these results as ai-assisted-solution.
3. Compare the results—analyze what the AI did better and where it made mistakes.

**Security, Ethics, Critical Thinking:**

1. Never upload code containing real data, passwords, or commercial information to public AI models. In this training project, there is no such data, but the habit must be formed.
2. Check all generated code snippets for vulnerabilities and compliance with company standards.
3. In real-world work, AI makes mistakes constantly—it may generate code that looks good but doesn’t actually work. Verify all output results and correct them as needed.

### Task 1. Working with Selenide

In this task, you will gain hands-on experience with one of the most widely used tools for automating interactions with web interfaces. You will learn how to launch browsers, interact with page elements, enter text, and fully simulate user actions — everything a real user would do in a browser.

For this project, you’ll be testing <https://www.saucedemo.com/>, which you may recognize from the QA5\_Defects project in the first part of the QA program (manual testing).

Imagine that you are interning at a company that has developed a demo e-commerce site: <https://www.saucedemo.com/>. The company needs to ensure that every feature works as intended and provides a seamless shopping experience.

Your assignment is to create a suite of automated tests that cover the site’s key workflows.

1. Start by exploring the site’s functionality. Go through the entire user journey, from selecting a product to completing checkout.
2. Import all required Selenide dependencies into your project.
3. Set up authorization with valid credentials (login: standard\_user and password: secret\_sauce), then launch the WebDriver with the default settings in Chrome.
4. Add a check to confirm that you have successfully navigated to the products page.
5. Expand your test to include the following steps: select a product, click "Add to Cart," and verify that the cart counter increases. Then, proceed to implement the checkout process.
6. Don’t forget to cover negative scenarios:
   - Attempt to log in with invalid credentials.
   - Try to complete checkout without filling in the required fields.
7. Now, refactor your code using the Page Object pattern. Create separate classes for each page: `LoginPageNoCucumber`, `ProductsPageNoCucumber`, `CartPageNoCucumber`, and `CheckoutPageNoCucumber`. Move all element locators and interaction methods into these classes. (For now, implement this without Cucumber.)

**Recommendations for completing the task:**

- Use Gradle for building and managing dependencies.
- Organize your tests and base classes into separate packages.
- Use Selenide’s should methods for assertions and avoid using standard assert statements.
- Interact with page elements exclusively through Selenide’s API: `$`, `shouldBe()`, `setValue()`, `click()`, etc.
- Place your Page Object classes in the src/main directory and your test classes in the src/test directory.

**Comparison of manual and AI approaches to creating a page object**

1. After you have manually created all the Page Object classes, try generating one of the classes using AI.
2. Formulate a prompt based on the example (you may improve it): *"Generate a Java class for the login page (LoginPage) using the Page Object pattern and Selenide. The page has input fields for username (id="user-name") and password (id="password"), as well as a Login button (class="submit-button"). Add a method for successful login and a method for checking the error message."*
3. Compare your manually written class with the one suggested by AI.
4. Prepare answers for the P2P review:
   - Which locators did AI identify correctly, and what mistakes did it make?
   - How did AI name the methods? Do they follow Clean Code principles?
   - What did you take from the generated code for your final version?
5. Save all results with the manual-solution and ai-assisted-solution labels.

### Task 2. UI Test Configuration Specifics

UI tests require specific parameters such as browser window resolution, browser type, and custom wait settings. In this task, you will practice configuring these parameters correctly.

1. Start by exploring what you can do with gradle.properties.
2. Use this file to set the following parameters: browser resolution, browser type, and explicit wait times. Specify that the browser should launch in non-headless mode.
3. Update your tests to read and use these parameters. Try running your tests in a browser other than Chrome.

**Recommendations for completing the task:**

- Use Gradle for build and dependency management.
- Remember to add code to parse your custom parameters from the gradle.properties file, as shown in the example.

```
test {
   jvmArgs += "-Dbrowser=${browser}"
   jvmArgs += "-DtestUrl=${testUrl}"
}
```

- Set the browser resolution to the standard 1600x900.
- Make sure all your changes remain compatible with previously implemented tests.

### Task 3. Transition to Cucumber

It's now time for you to migrate your tests to Cucumber. As a result, your tests will be understandable to non-technical users, and you won't need to integrate with any test management system (TMS).

Migrating your tests to Cucumber will make your test scenarios understandable to non-technical team members and eliminate the need for integration with any external TMS.

1. Import all Cucumber dependencies into your project.
2. Create a new package for your test suite from Assignment 1 and reimplement your Page Object classes (without the "NoCucumber" suffix). Use Cucumber annotations for each method to define your test steps.
3. Describe a feature file in which you will specify your test steps, then try running your tests in two ways:

   a. Cucumber Runner;
   b. the Cucumber plugin for your IDE. (*Note: installing JetBrains plugins may require a VPN, as these products are unavailable in Russia. If you are from one of the campuses located in Russia, you will need a VPN.*)
4. Create a CucumberHooks class with a before method to initialize the WebDriver before each scenario.

**Recommendations for completing the task:**

- Use Gradle for build and dependency management.
- Explore all the features of Cucumber syntax. It offers flexible ways to pass data into your steps and lets you parameterize your tests.
- Pay close attention to the Gherkin keywords you use and ensure they accurately reflect the function of each annotated method.
- Keep your Page Object classes in the main package and your feature files in the resources folder within the test package.

**Generating Gherkin scenarios with AI**

After manual implementation, try generating scenario drafts using AI.

1. Formulate a prompt based on the example (the prompt can be improved): *"Write a Gherkin scenario in Russian for testing successful login on saucedemo.com. Use the keywords: Given, When, And, Then."*
2. Review the result. Then create a second, more detailed prompt, taking into account the order in which the user performs actions and specifying the actual existing elements on the page. Save a screenshot of the prompt.
3. Compare the AI-generated scenarios with the ones you wrote manually.
4. Prepare answers for the P2P review:

   - How well did AI understand the context and structure of Gherkin?
   - Did you have to rewrite the steps to align with your methods in the Step Definitions?
   - What from the AI's suggestions would you keep in the final version of the feature files?
5. Save all results with the manual-solution and ai-assisted-solution labels.

### Task 4. Integration with Allure

Finally, let's present your results in Allure, the most visually appealing and widely used reporting tool!

1. Import all the necessary Allure dependencies into the same project.
2. Generate a report after running your automated tests.

**Recommendations for completing the task:**

- Use Gradle for build and dependency management.
- There’s no need to add @Step annotations; simply integrate Allure with Cucumber using the Allure-Cucumber library.

**Analyzing a test report with AI**

1. After running the tests and generating an Allure report, open any failed test (you can intentionally introduce a bug into the test to see a failure).
2. Take a screenshot of the error page and copy the stack trace from the report.
3. Send this information to AI with a prompt based on the example (the prompt can be improved): *"Analyze this stack trace and screenshot. Explain why the UI test failed and suggest how to fix it."* Save a screenshot of the prompt and the output.
4. Evaluate the quality of the AI's analysis. Did its explanation match the actual cause?
5. Prepare answers for the P2P review: did the AI help diagnose the error, and can this approach be used in real-world work?

💡 [Press here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) **to leave feedback on this project.** It's anonymous and will help our «School 21» team improve the learning experience. We recommend completing the survey immediately after finishing the project.