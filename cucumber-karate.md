# This workshops gives you a intro on Karate with Cucumber based on the Karate GitHub documentation. {#markdown-header-cucumber}

# Cucumber {#markdown-header-cucumber}

**Intro \(which you can/must skip if you already know Cucumber\)**

Cucumber is a software tool used by computer programmers for testing other software. It runs automated acceptance tests written in a behavior-driven development \(BDD\) style. Central to the Cucumber BDD approach is its plain language parser called Gherkin. It allows expected software behaviors to be specified in a logical language that customers can understand. As such, Cucumber allows the execution of feature documentation written in business-facing text.

##### Engels

* Given: Given, And, But
* When: When
* Then: Then, And
* Extra's: Feature, Scenario \[Template\]

# Karate

[https://github.com/intuit/karate](https://github.com/intuit/karate)

## Web-Services Testing Made`Simple.`

Karate enables you to script a sequence of calls to any kind of web-service and assert that the responses are as expected. It makes it really easy to build complex request payloads, traverse data within the responses, and chain data from responses into the next request. Karate's payload validation engine can perform a 'smart compare' of two JSON or XML documents without being affected by white-space or the order in which data-elements actually appear, and you can opt to ignore fields that you choose.

Since Karate is built on top of [Cucumber-JVM](https://github.com/cucumber/cucumber-jvm), you can run tests and generate reports like any standard Java project. But instead of Java - you write tests in a language designed to make dealing with HTTP, JSON or XML -**simple**.

Karate does not attempt to have tests be in "natural language" like how Cucumber tests are [traditionally expected to be](https://cucumber.io/docs/reference#gherkin). That said, the syntax is very concise, and the convention of every step having to start with either

`Given`,`And`,`When`or `Then`,

makes things very readable. You end up with a decent approximation of BDD even though web-services by nature are "headless", without a UI, and not really human-friendly.

If you are familiar with Cucumber \(JVM\), you may be wondering if you need to write[step-definitions](https://cucumber.io/docs/reference/jvm#step-definitions). The answer is**no**.

So yes, you can say Karate is not a complete BDD framework.

For a detailed discussion on BDD and how Karate relates to Cucumber, please refer to this blog-post:

[Yes, Karate is not\_true\_BDD](https://medium.com/@ptrthomas/yes-karate-is-not-true-bdd-698bf4a9be39).

## Enough theory...

All given examples are also in the **demo.feature**

All awnsers are in **rijksmuseum.feature**

### Setting and Using Variables

## `def`

#### Set a named variable

```
#Example 1
Background:
# assigning a string value:
Given def myVar = 'world'
# using a variable
Then print myVar
```

Note that`def`will over-write any variable that was using the same name earlier.

_**Exercise**_** 1:** _Create a new feature file with a background scenario that defines 4 variables for Rijksmuseum API test. _

1. _Your Rijksmuseum API key \(hint: ?key=12345678\) ._
2. _Output JSON format as per Rijksmuseum API \(&format=json\)._
3. _Base url \(_[https://www.rijksmuseum.nl/api/\](https://www.rijksmuseum.nl/api/%29_\).\_
4. _Language code \(hint: culture\)_

## `assert`

#### Assert if an expression evaluates to`true`

Once defined, you can refer to a variable by name. Expressions are evaluated using the embedded JavaScript engine. The assert keyword can be used to assert that an expression returns a boolean value.

```
#Example 2
Given def color = 'red'
And def num = 5
Then assert color + num == 'red 5'
```

Everything to the right of the`assert`keyword will be evaluated as a single expression.

_**Exercise**_** 2:** _Create a new scenario that asserts:_

1. _The Base Url defined in the background equals "_[https://www.rijksmuseum.nl/api/](https://www.rijksmuseum.nl/api/)_"_
2. _The Output JSON format as defined in the background equals "&format=json"_

**Keywords**

## `url`

```
Given url 'https://jsonplaceholder.typicode.com/posts/1'
```

A URL remains constant until you use the`url`keyword again, so this is a good place to set-up the 'non-changing' parts of your REST URL-s.

## `method`

The HTTP verb -`get`,`post`,`put`,`delete`,`patch`,`options`,`head`,`connect`,`trace`.

Lower-case is fine.

```
When 
method post
```

It is worth internalizing that during test-execution, it is upon the`method`keyword that the actual HTTP request is issued. Which suggests that the step should be in the`When`form, for e.g.:`When method post`. And steps that follow should logically be in the`Then`form.

## `status`

This is a shortcut to assert the HTTP response code.

```
Then 
status 200
```

And this assertion will cause the test to fail if the HTTP response code is something else.

```
#Example 3
Scenario: Use of the keyword url, method (get) and status

Given url 'https://www.google.nl'
When method get
#the step that immediately follows the above would typically be:
Then status 200
```

** **_**Exercise**_** 3:** _Create a new scenario that issues a HTTP request to the Rijksmuseum website that gets the full collection. Note that the Rijksmuseum api always needs a key, output format and culture \(as per api\). And verify that the return status is 200._

## `response`

After every HTTP call this variable is set with the response body, and is available until the next HTTP request over-writes it. You can easily assign the whole`response`\(or just parts of it using Json-Path or XPath\) to a variable, and use it in later steps.

The response is automatically available as a JSON, XML or String object depending on what the response contents are.

## `match`

 Once you have a JSON or XML object, Karate provides multiple ways to manipulate, extract or transform data. And you can easily assert that the data is as expected by comparing it with another JSON or XML object.

The`match`operation is smart because white-space does not matter, and the order of keys \(or data elements\) does not matter.

```
#Example 4
Scenario: Try out a call to a webservice
Given url 'https://jsonplaceholder.typicode.com/posts/1'
When method get
Then status 200
And match response == {"userId":1,"id":1,"title":"sunt aut facere repellat provident occaecati excepturi optio reprehenderit","body":"quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"}
```

_**Exercise 4: **Create a new scenario that issues a HTTP request to the Rijksmuseum website that get the full collection. Only this time use a invalid key. Valid that the return status is 403 \(forbidden\) and the JSON response matches JSON with a field name 'message' and a value 'key not found'._

_Hint:_

```
{"message": "key not found"}
```

## `read`

Reading files is achieved using the`read`keyword. By default, the file is expected to be in the same folder \(package\) as the`*.feature`file.

```
#Example 5
Scenario: 
Use of the keyword read
Given def someJson = read('example.json')
Then match someJson userId == 1

example.json == 
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```

_**Exercise 5: **_

* _Create in folder of your feature files a new JSON file as per example below._
* Create a new scenario that defines the new JSON file as a variable
* Do a HTTP request to get the Rijksmuseum collection with objectNumber 'sk-c-5'
* Verify that the artikel object title in the JSON response equals the artikel object title in the newly created JSON file.
* Verify that the artikel object title in the JSON response equals

  ```
  Militia Company of District II under the Command of Captain Frans Banninck Cocq, Known as the ‘Night Watch’
  ```

  ```
  JSON example:
  {
    "artObject": {
      "title": "Militia Company of District II under the Command of Captain Frans Banninck Cocq, Known as the ‘Night Watch’"
    }
  }
  ```

   

_**Exercise 6:**_

* \_** **Verify in a new scenario that the Rijksmuseum exposition for \_2017-06-16 with expedition id expeditionId:

  ```
  '0d1beb4d-8173-40a9-a70b-ea234845e2d2'
  ```

   has place for a total of 15 people of which only 11 are still available.

   

To make dynamic data-driven testing easier, the following keywords also exist:[`params`](https://github.com/intuit/karate#params),[`headers`](https://github.com/intuit/karate#headers),[`cookies`](https://github.com/intuit/karate#cookies-json)and[`form fields`](https://github.com/intuit/karate#form-fields). They use JSON to build the relevant parts of the HTTP request.

## `param`

Setting query-string parameters:

```
    #Example 6
  Scenario: Use of the param keyword
    Given url 'https://jsonplaceholder.typicode.com/posts'
    * param userId = '1'
    * param id = '1'
    And header Accept = 'application/json'
    When method get
    Then status 200
    And match $..id == 1
    And match $..title == ["sunt aut facere repellat provident occaecati excepturi optio reprehenderit"]
```

You can also use JSON to set multiple query-parameters in one-line using[`params`](https://github.com/intuit/karate#params)and this is especially useful for dynamic data-driven testing.

---

Congratulations! You should now be good to go for the exercise as stated under the 'System under test' page or see below:

#### Exercises

* Find the start time of the calendar event "Rondleiding Hoogtepunten van het Rijksmuseum" on 2017-06-27
* Find the URL for a picture of the Nightwatch \(de Nachtwacht \) painting by Rembrandt van Rijn
* Check if the admission price for an adult is shown as 17.50 Euros on the website

You can also check out the answers in the **BolExercise.feature.**



