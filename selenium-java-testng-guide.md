# Selenium Automation Framework Interview Guide

This article walks you through the Selenium-based Java automation framework for testing Amazon’s search functionality using Page Object Model (POM), TestNG, and integrated **Allure reporting** for enhanced visibility of test results.

---

## Features

* Automated UI tests for Amazon product search
* Page Object Model (POM) structure for reusable components
* TestNG for test orchestration and suite management
* Allure reporting for insightful test results
* Fluent and explicit waits for stability
* Cross-browser support via Driver Factory (Chrome, Firefox)
* Thread-safe WebDriver using Singleton + ThreadLocal

---

## Project Structure

```
src/
  main/
  test/
    java/
      com/practice/selenium/
        pageObjects/
          BasePage.java
          HomePage.java
          SearchResultsPage.java
        test/
          AmazonSearchTest.java
        utils/
          DriverFactory.java
    resources/
      chromedriver
pom.xml
```

---

## Prerequisites

* Java 17+
* Maven 3.6+
* Chrome or Firefox browser
* [Allure CLI](https://allurereport.org/docs/install-for-macos/)
* [chromedriver](https://chromedriver.chromium.org/) (already included)

---

## Setup Instructions

1. **Clone the repository:**

   ```sh
   git clone <repository-url>
   cd selenium-java-automation-framework
   ```

2. **Install dependencies:**

   ```sh
   mvn clean install
   ```

3. **Ensure ChromeDriver path is set:**
   Update `DriverFactory.java` if you need to specify a custom path to the driver.

---

## Running Tests

```sh
mvn test
```

To specify browser (default: Chrome):

```sh
mvn test -Dbrowser=firefox
```

---

## 📈 Generating Allure Report

```sh
mvn allure:report
```

Then serve it:

```sh
allure serve
```

This will open the report in your default browser.

[Allure Report Screenshot](https://github.com/smitha-kundapura/selenium-java-automation-framework/blob/main/image.png)

---

## Key Classes

| **Class**                | **Role**                                  |
| ------------------------ | ----------------------------------------- |
| `HomePage.java`          | Handles Amazon search input               |
| `SearchResultsPage.java` | Interacts with results list               |
| `AmazonSearchTest.java`  | Test flow from homepage to 2nd result     |
| `DriverFactory.java`     | Thread-safe cross-browser driver creation |

---

## Design Patterns Used

| **Pattern**                | **Where It's Used**                       | **Explanation**                                         |
| -------------------------- | ----------------------------------------- | ------------------------------------------------------- |
| Page Object Model (POM)    | `HomePage.java`, `SearchResultsPage.java` | Encapsulates page-specific logic for reuse.             |
| Test Base Pattern          | `BaseTest.java`                           | Handles setup/teardown centrally.                       |
| Factory Pattern            | `DriverFactory.java`                      | Supports Chrome and Firefox via a flexible constructor. |
| Singleton with ThreadLocal | `DriverFactory.java`                      | Isolates WebDriver per thread for safe parallel tests.  |
| DRY Principle              | Throughout framework                      | Eliminates repetition in page flows and utility code.   |

---

## XPath Reference Table

| **Summary**            | **XPath Example**                                               | **Explanation**                                               |
| ---------------------- | --------------------------------------------------------------- | ------------------------------------------------------------- |
| Absolute XPath         | `/html//div/div/div/div/div/div/div/img`                        | Full path from root to `<img>`. Fragile if DOM changes.       |
| Relative XPath         | `//img[@alt='LambdaTest']`                                      | Locates `<img>` with `alt='LambdaTest'` anywhere in DOM.      |
| aria-labelledby        | `//div[@aria-labelledby='sign_up_with_google_label']`           | Locates `<div>` by `aria-labelledby` attribute.               |
| placeholder (email)    | `//input[@placeholder='Business Email*']`                       | Locates input field by its placeholder value.                 |
| placeholder (password) | `//input[@placeholder='Desired Password*']`                     | Similar for password field.                                   |
| data-testid on button  | `//button[@data-testid='signup-button']`                        | Matches a button using `data-testid`.                         |
| contains()             | `//tagname[contains(@attribute,constantvalue)]`                 | Selects element with partial attribute match.                 |
| Chained XPath          | `//div[contains(@class,'signUpWithEmail')]//input[@id='email']` | Parent + child structure.                                     |
| following axis         | `//tagname[@attribute='value']//following::tagname`             | All tagname elements following a specific node.               |
| preceding axis         | `//tagname[@attribute='value']//preceding::tagname`             | All tagname elements preceding a specific node.               |
| Complex axis example   | `//input[@type='password']//ancestor::div//input[@id='email']`  | From password input, finds an ancestor div, then email input. |

---

## Notes

* Amazon presents a CAPTCHA that requires manual solving during automation
* Allure results are generated in `allure-results/`