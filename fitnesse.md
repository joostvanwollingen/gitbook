# System under test

We've selected a number of interesting websites to use in our tests tonight. 
Feel free to choose one or more of the options below and try your hand at a few of the exercises.

(If you don't mind some spoilers for the exercises you can peek at wiki pages at: 
https://github.com/fhoeben/sample-fitnesse-project/tree/testToolingWorkshop/wiki/FitNesseRoot/TestToolingWorkshop)

* Update ‘funda Storyboard test’
* Write front-end test for ‘typeform.com’
* Write API test for ‘typeform.com'
* Use scenario table

## Get started
* Open http://localhost:9090/HsacExamples
* Go to: [Slim Tests / BrowserTest](http://localhost:9090/HsacExamples.SlimTests.BrowserTests) (keep this page open to have reference of DSL for front-end tests)


## ‘funda Storyboard test’
* Click: [StoryboardTest](http://localhost:9090/HsacExamples.SlimTests.BrowserTests.StoryboardTest)
* Test at top of page

### Exercise
Update test to validate some more properties of the listing:
* ‘Woonoppervlakte’
* ‘Bouwjaar’

## typeform.com questionnaire

### Exercise
* Add new test page to [HsacExamples/SlimTests/BrowserTests](http://localhost:9090/HsacExamples.SlimTests.BrowserTests) suite
* Add script table using ‘browser test’
* Open questionnaire: https://fhoeben.typeform.com/to/fdx32Y  
* Answer all questions (clicking and using keyboard)
* Ensure you end up on page showing ‘Thanks for completing this typeform’

## typeform.com API

### Exercise
* Add new test page to [HsacExamples/SlimTests/HttpTests](http://localhost:9090/HsacExamples.SlimTests.HttpTests)
* Script table using ‘json http test’
* Get from https://api.typeform.com/v1/form/fdx32Y?key=96a5b83b3cfb12c128fa62debeb9dfb51d96a59e 
* Show response in test result
* Use ‘json path’ to check more than 0 responses completed

## Use scenarios to improve tests

### Exercises
* Use scenario to make test with complex json path more readable
* Use scenario instead of hardcoding question id
* Encapsulate retrieving of answers in scenario
* Create decision table using scenario
* Move scenarios to (new) ScenarioLibrary page so they can be used in multiple tests


