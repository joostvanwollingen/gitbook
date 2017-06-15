# FitNesse with [HSAC-fixtures](https://github.com/fhoeben/hsac-fitnesse-fixtures) workshop

We will use a sample test project. This project can either be used from:
* inside the virtual machine prepared for the meetup (inside ~/Documents/Fitnesse directory)
* a locally downloaded and extracted [standalone.zip](https://github.com/fhoeben/sample-fitnesse-project/releases/download/test-tooling-0.1/sample-fitnesse-project-using-hsac-fixtures-1.0-SNAPSHOT-standalone.zip)
* its [source](https://github.com/fhoeben/sample-fitnesse-project/tree/test-tooling-0.1), using a JDK and Maven

## Start local wiki
First we will have to start our wiki server:
* Open a terminal (or command prompt)
* Go to the directory where the 'standalone.zip' was extracted (`cd ~/Documents/Fitnesse` in the virtual machine)
* Start the server: `java -jar fitnesse-standalone.jar -p 9090`

(If you want to run from source, with maven, use: `mvn compile exec:exec` from the project's root.)

## Overview

We've selected a number of interesting websites to use in our tests tonight.   
Feel free to choose one or more of the options below and try your hand at a few of the exercises.

\(If you don't mind some spoilers for the exercises you can peek at the predefined wiki pages below   
[http://localhost:9090/TestToolingWorkshop](http://localhost:9090/TestToolingWorkshop)\)

* Update ‘funda Storyboard test’
* Write front-end test for ‘typeform.com’
* Write API test for ‘typeform.com'
* Use scenario table

## Get started

* Open [http://localhost:9090/HsacExamples](http://localhost:9090/HsacExamples)
* Go to: [Slim Tests / BrowserTest](http://localhost:9090/HsacExamples.SlimTests.BrowserTests) \(keep this page open to have reference of DSL for front-end tests\)

## ‘funda Storyboard test’

* Click: [StoryboardTest](http://localhost:9090/HsacExamples.SlimTests.BrowserTests.StoryboardTest)
* Test at top of page

### Exercise

Update test to validate some more properties of the listing:

* ‘Woonoppervlakte’
* ‘Bouwjaar’

## typeform.com questionnaire

### Exercise

* Add new test page to [TestToolingWorkshop / FrontEndTests](http://localhost:9090/TestToolingWorkshop.FrontEndTests) suite
* Add script table using ‘browser test’
* Open questionnaire: [https://fhoeben.typeform.com/to/fdx32Y](https://fhoeben.typeform.com/to/fdx32Y)  
* Answer all questions \(clicking and using keyboard\)
* Ensure you end up on page showing ‘Thanks for completing this typeform’

## typeform.com API

### Exercise

* Add new test page to [TestToolingWorkshop / BackEndTests](http://localhost:9090/TestToolingWorkshop.BackEndTests)
* Script table using ‘json http test’
* Get from [https://api.typeform.com/v1/form/fdx32Y?key=96a5b83b3cfb12c128fa62debeb9dfb51d96a59e](https://api.typeform.com/v1/form/fdx32Y?key=96a5b83b3cfb12c128fa62debeb9dfb51d96a59e) 
* Show response in test result
* Use ‘json path’ to check more than 0 responses completed

## Use scenarios to improve tests

### Exercises

* Use scenario to make test with complex json path more readable
* Use scenario instead of hardcoding question id
* Encapsulate retrieving of answers in scenario
* Create decision table using scenario
* Move scenarios to \(new\) ScenarioLibrary page so they can be used in multiple tests



