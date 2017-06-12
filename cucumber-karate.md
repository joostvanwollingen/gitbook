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

### Setting and Using Variables

## `def`

#### Set a named variable

```
# assigning a string value:
Given def myVar = 'world'
# using a variable
Then print myVar
```

Note that`def`will over-write any variable that was using the same name earlier.

1. Create a Cucumber background scenario that defines 4 variables for Rijksmuseum API test.  
   1. Your Rijksmuseum API key \(hint: ?key=12345678\)  
   2. Output JSON format as per Rijksmuseum API \(&format=json\)  
   3. Base url \([https://www.rijksmuseum.nl/api/](https://www.rijksmuseum.nl/api/\)\)  
   4. Language code \(culture\) \(hint: en/\)

## `assert`

#### Assert if an expression evaluates to`true`

Once defined, you can refer to a variable by name. Expressions are evaluated using the embedded JavaScript engine. The assert keyword can be used to assert that an expression returns a boolean value.

```
Given 
def color = 
'red '
And 
def num = 5

Then 
assert color + num == 
'red 5'
```

Everything to the right of the`assert`keyword will be evaluated as a single expression.

**Keywords**

## `url`

```
Given 
url 'https://myhost.com/v1/cats'
```

A URL remains constant until you use the`url`keyword again, so this is a good place to set-up the 'non-changing' parts of your REST URL-s.

