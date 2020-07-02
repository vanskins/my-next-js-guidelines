# Guidelines Next Front-end
- [Guidelines Next Front-end](#guidelines-next-front-end)
- [1. Next JS Packages](#1-next-js-packages)
- [2. Project folder structure](#2-project-folder-structure)
    - [2.1 Components](#21-components)
    - [2.2 Pages](#22-pages)
    - [2.3 Public](#23-public)
    - [2.4 actions](#24-actions)
- [3. Naming conventions](#3-naming-conventions)
- [4. Creating a new functional Components for Pages and reusable component.](#4-creating-a-new-functional-components-for-pages-and-reusable-component)
    - [Functional Component](#functional-component)
    - [So why should I use functional components at all?](#so-why-should-i-use-functional-components-at-all)
- [5. Routes](#5-routes)
- [6. Don't repeat yourself (DRY)](#6-dont-repeat-yourself-dry)
- [5. General rules](#5-general-rules)
- [6. Reference](#6-reference)

# 1. Next JS Packages

- [next-routes](https://github.com/fridays/next-routes) (For routing pages)
- [express](https://expressjs.com/) (For serving the pages server side)
- [next-i18next](https://github.com/isaachinman/next-i18next) (Handles translation support)
- [react-hook-form](https://react-hook-form.com/) (Form validations)

# 2. Project folder structure
### 2.1 Components
Inside of the components folder should have three folders layouts, partials, and shared. Every component that is created should be put in PascalCase. (Ex. ContactForm -> index.js). The index.js inside the components folder will export all the components for the pages to used.

Example
```
  import { Header, TransactionCard, ContactForm } from "../../components
```

### 2.2 Pages
Inside the pages folder will be the pages of the web application, naming of the folders should be related to the pages that it renders, pages that are related to each other should be group accordingly. [next-routes]("https://github.com/fridays/next-routes") will plot the routing of the web pages.

### 2.3 Public
Public folder consist of the static css, images, and language localization.

### 2.4 actions
This folder will have all the api calls to the backend. It should be group accordingly to the functionality it do. The index.js on every folder inside action will export all the functionalities for components or pages to consume.
Example
```
  import { create, retrieve, update, delete } from "../../actions/user
```

```bash
|--actions
|  |--user
|  |  |--create.js
|  |  |--retrieve.js
|  |  |--update.js
|  |  |--delete.js
|  |  |--index.js
|  |--products
|  |  |--create.js
|  |  |--retrieve.js
|  |  |--update.js
|  |  |--delete.js
|  |  |--index.js
|--build
|--components
|  |--layouts
|  |  |--Main.js
|  |--partials
|  |  |--Header
|  |  |  |--index.js
|  |  |--Footer
|  |  |  |--index.js
|  |  |--Sidebar
|  |  |  |--index.js
|  |--shared
|  |  |--ContactForm
|  |  |  |--index.js
|  |  |--TransactionCard
|  |  |  |--index.js
|  |--index.js (This file will export the re usable components)
|--config
|  |--api.js
|--libraries
|--node_modules
|--pages
|  |--about
|  |  |--index.js
|  |--contact-us
|  |  |--index.js      
|  |--index.js
|--public
|  |--assets
|  |  |--css
|  |  |--img
|  |--static (Static files)
|  |  |--locales (Files for translations)
|  |     |--en
|  |        |--common.json
|  |     |--it         
|  |        |--common.json
|--.env
|--.gitignore
|--i18n.js
|--index.js
|--next.config.js
|--routes.js
|--package.json

```

# 3. Naming conventions
| What | How | Implementation | Location | Other name rule |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| Component | PascalCase, singular | components | components | Component should be descriptive on what the components functionalities. It should be reusable.
| Pages | camelCase, singular | pages | pages | Pages that is created should be group on related pages for organization, file name should be related on what the page renders.
| Variable declaration | camelCase | - | - | the use of const and let should be strictly implemented for ES6 standard, variable should be understandable on it's purpose.|
|Function Declaration| camelCase | - | - | Functions that is created should be understandable on it's purpose and it should have maximum of 3 parameters and should only do one job for code reusability and so that it can be debug easily.
# 4. Creating a new functional Components for Pages and reusable component.
Utilized the used of react hooks, (useState, useEffect)
### Functional Component
```
  /**
    This component is for Footer consist of links and etc.
  */
  const Footer = props => {
    return (
      <div>
        <h1>This is footer</h1>
      <div>
    )
  }

  export default Footer;
```

### So why should I use functional components at all?
Benefits you get by using functional components in React.
- easier to read and test
- less code
- best practices.
- performance

[Please see reference for better understanding.]("https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108")

# 5. Routes

All routes should be set inside the routes.js and server.js.

Example code inside routes.js
```
  const routes = require('next-routes')
  const config = require('next/config').default()
  let routePrefix = ""

  if (config.routePrefix) routePrefix = config.routePrefix

  module.exports = routes()
  .add("index", `${routePrefix}/`, '/')
  .add("about", `${routePrefix}/about`, '/about')
```

If you can see the code about it has a variable for routePrefix it is set from .env file. We do it like this because when deploying to staging server we use /name-of-project in our domain names that is why we need to prepare the app for different environments depening on the values inside .env file we set.

# 6. Don't repeat yourself (DRY)

Components and functions inside libraries should have one purpose and responsibility, to lessen bugs and so that we can easily debug the code without affecting other parts of the app. 

# 5. General rules
- Proper indentions of (2 spaces)
- Proper singular/plural naming
- Remove unused codes like variables, deprecated functions etc.
- Add comments that describes the functionalites of component or functions you will create.
- File/class names should be DESCRIPTIVE
- Method names should be DESCRIPTIVE
- DO NOT put logical codes inside pages. Create libraries and actions for specific task in your code.
- Make sure that the next person that will read your code can understand it without you asking.

# 6. Reference
- [https://medium.com/yals/dry-out-react-code-into-presentational-components-8308f42a8b80](https://medium.com/yals/dry-out-react-code-into-presentational-components-8308f42a8b80)
- [https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108](https://medium.com/@Zwenza/functional-vs-class-components-in-react-231e3fbd7108)