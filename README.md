# browserstack-junit5-maven
[JUnit](https://junit.org/junit5/) Integration with BrowserStack.

Master branch contains **Selenium 3** samples, for **Selenium 4 - W3C protocol** please checkout [selenium-4](https://github.com/browserstack/junit-browserstack/tree/selenium-4) branch

![BrowserStack Logo](https://d98b8t1nnulk5.cloudfront.net/production/images/layout/logo-header.png?1469004780) 

## Setup
* Clone the repo
* Install dependencies `mvn install`
* Update *.conf.json files inside the `src/test/resources/conf` directory with your [BrowserStack Username and Access Key](https://www.browserstack.com/accounts/settings). 

## Running your tests
* To run single test, run `mvn test -P single`
* To run the tests in parallel, keep the configuration parameter- 'junit.jupiter.execution.parallel.enabled' as 'true' and run `mvn test -P parallel`
* To run local tests, run `mvn test -P local`
* Appium tests
    - To run android tests, run `mvn test -P android`
    - To run ios tests, run `mvn test -P ios`
    - To run appium tests in parallel,
        - Comment `@Execution(ExecutionMode.SAME_THREAD)` and uncomment `@Execution(ExecutionMode.CONCURRENT)`
        - Change the value of 'i' depending on the number of parallel tests to be launched
        - To run parallel test, run `mvn test -P appium_parallel`

## Parallel execution in Junit 5
* Add the following snippet to pom.xml as `configurationParameters` to enable parallel testing

```
junit.jupiter.execution.parallel.enabled = true
junit.jupiter.execution.parallel.mode.default = concurrent
```
* Add `@Execution(ExecutionMode.SAME_THREAD)` tag to a class or method that is to be run in parallel.
* In this project `@RepeatedTest` tag is used to support parallel testing.

 Understand how many parallel sessions you need by using our [Parallel Test Calculator](https://www.browserstack.com/automate/parallel-calculator?ref=github)

## Notes
* You can view your test results on the [BrowserStack Automate dashboard](https://www.browserstack.com/automate)
* To test on a different set of browsers, check out our [platform configurator](https://www.browserstack.com/automate/java#setting-os-and-browser)
* You can export the environment variables for the Username and Access Key of your BrowserStack account. 

  ```
  export BROWSERSTACK_USERNAME=<browserstack-username> &&
  export BROWSERSTACK_ACCESS_KEY=<browserstack-access-key>
  ```

## Addtional Resources
* [Documentation for writing Automate test scripts in Java](https://www.browserstack.com/automate/java)
* [Customizing your tests on BrowserStack](https://www.browserstack.com/automate/capabilities)
* [Browsers & mobile devices for selenium testing on BrowserStack](https://www.browserstack.com/list-of-browsers-and-platforms?product=automate)
* [Using REST API to access information about your tests via the command-line interface](https://www.browserstack.com/automate/rest-api)

