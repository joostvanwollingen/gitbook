# Cypress.io

## Creating your first project

> Note: If you haven't installed Cypress.io yet refer to the [Setup](/setup.md) section. If you are using the VM it should be in the list of shortcuts on the left.

* Open Cypress either by clicking the icon or by running `cypress open` on the command line
* Sign-in to your [GitHub](https://github.com/join) account
* Click `"Add Project"` in the top left
* Create a new folder: `/home/vagrant/Documents/Cypress`
* Open the project in IntelliJ \(choose `File>Open`\)or your favorite editor

> Optionally: Click `example_spec.js`  in the Cypress UI to see the example tests run and get a feel for Cypress.

## Project structure

```
├── cypress
│   ├── fixtures
│   │   └── example.json
│   ├── integration
│   │   ├── example_spec.js
│   ├── support
│   │   ├── commands.js
│   │   ├── defaults.js
│   │   └── index.js
├── README.md
└── cypress.json
```



