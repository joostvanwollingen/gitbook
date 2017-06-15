# Cypress.io

If you haven't installed Cypress.io yet refer to the [Setup](/setup.md) section. If you are using the VM it should be in the list of shortcuts on the left.

## 1. Creating your first project

* Open Cypress either by clicking the icon or by running `cypress open` on the command line
* Sign-in to your [GitHub](https://github.com/join) account
* Click `"Add Project"` in the top left
* Create a new folder: `/home/vagrant/Documents/Cypress`
* Open the project in IntelliJ \(choose `File>Open` \) or your favorite editor
* Open the [Cypress.io documentation](https://docs.cypress.io/) in a tab in your browser. We will use this to lookup commands.

> Optionally: Click `example_spec.js`  in the Cypress GUI to see the example tests run and get a feel for Cypress.

### Project structure

By default Cypress creates some folders and files that you will probably need. During this workshop we will only use `integration/*.js` and `support/commands.js` files. If you want to know what the other files do, checkout the [Cypress.io documentation.](https://docs.cypress.io/docs/writing-your-first-test)

```
│   ├── fixtures
│   │   └── example.json
│   ├── integration
│   │   ├── example_spec.js
│   ├── support
│   │   ├── commands.js
│   │   ├── defaults.js
│   │   └── index.js
└── cypress.json
```

## Creating our first test

* Create a file: `integration/rijksmuseum.js`

* Copy/paste the code below. It will be our template for the exercises.

```
describe('Rijksmuseum exercises', function () {

    //Statements in this function will be executed before each test in this file
    beforeEach(function () {                      
        cy.visit('https://www.rijksmuseum.nl')
    })

    it('Find the agenda event for 2017-07-27', function() {
        //Implement first test here
    })

    it('Find out if the admission price for an adult is still 17.50 euro', function() {
       //Second test goes here
    })
})
```

* Run the tests with the Cypress GUI by clicking `rijksmuseum.js`. You will notice that the site opens and it executes two tests, but nothing happens yet. Let's change that!
* In order to get to the agenda page on [https://www.rijksmuseum.nl](https://docs.cypress.io/docs/writing-your-first-test) we have to click a few links. `("Plan je bezoek" > "Nu in het museum" > "Dagagenda")`. To click on an item we first need to locate it, [Cypress uses CSS-locators](https://docs.cypress.io/docs/finding-elements) to find elements in the page DOM \(HTML\). The most important one is the [`get command`](https://docs.cypress.io/v1.0/docs/get).

  Copy/paste the code below to see how you could click the "Plan je bezoek"-link.

```
cy                                            //The cy  object is how we can interact with the browser through Cypress.
    .get("span:contains('Plan je bezoek')")   //This locates the span element that contain the text we want to click on
    .click()                                  //We click it
```

* Expand the script with the locators for the [Anchor-elements](https://www.w3.org/MarkUp/1995-archive/Elements/A.html) : `"Nu in het museum" & "Dagagenda"`
* Now that we are on the [Dagagenda-page](https://www.rijksmuseum.nl/nl/agenda/) we have to:
  1. Open the calendar
  2. Click next to go to July
  3. Click the 27th
* Write the statements for these steps
* Finally we want to verify that the start and end time for the `Rondleiding Hoogtepunten van het Rijksmuseum`  event matches 11:00 - 12:00. First we need a locator for the HTML element that contains this piece of information and finally we can use Cypress' [should method](https://docs.cypress.io/v1.0/docs/should) to verify its contents.
* Congrats, you've just finished your first test using Cypress.io!

## Second exercise: Admission price

Before we go to the museum, let's check the admission price for adults. This information is displayed on the ["Openingstijden & prijzen page"](https://www.rijksmuseum.nl/nl/praktische-informatie/openingstijden-en-prijzen). You can navigate there by clicking `Plan je bezoek" > "Praktische info" > "Openingstijden en prijzen.`

Writing locators every time we just want to click visible text gets a bit tiring. Let's see if we can create a function that makes that a bit easier.

* Open the `support/commands.js` file. This file contains [custom commands](https://docs.cypress.io/v1.0/docs/commands) that we can re-use throughout our tests.
* Add the following code:

```
Cypress.addParentCommand("clickOn", function (input) {
    var input = input || ""

    var log = Cypress.Log.command({
        name: "clickOn",
        message: [input],
        onConsole: function () {
            return {
                text: input
            }
        }
    })

    cy
        .get("body")
        .contains(input)
        .click()
        .then(function () {
            log.snapshot().end()
        })
})
```

* Now use this command in your test to navigate to the Openingstijden page.



