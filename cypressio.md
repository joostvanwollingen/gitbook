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

By default Cypress creates some folders and files for you that you will probably need. During this workshop we will only use `integration/*.js` and `support/commands.js` files. If you want to know what the other files do, checkout the [Cypress.io documentation.](https://docs.cypress.io/docs/writing-your-first-test)

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

### Creating our first test

* Create a file: `integration/rijksmuseum.js`
* Copy paste the code below. It will be our template for the exercises.

```
describe('Rijksmuseum exercises', function () {

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

```
cy
    .get("[data-role='site-menu-items']")
    .contains("Plan je bezoek")
    .click()
```





