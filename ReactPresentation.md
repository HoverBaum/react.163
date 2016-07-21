# ReactJS

### Structuring development

----

### ES6

The code in this presentation makes heavy use of [*ES6*](http://es6-features.org/). If you are not familiar with the syntax please look it up.

- [Arrow Functions](http://es6-features.org/#ExpressionBodies)
- [Constants](http://es6-features.org/#Constants)
- [Object.assign](http://es6-features.org/#ObjectPropertyAssignment)
- [Default values for parameters](http://es6-features.org/#DefaultParameterValues)
- [Exporting and importing](http://es6-features.org/#ValueExportImport)

Or read [a full introduction to ES6 features](https://github.com/lukehoban/es6features).

---

# An introduction

----

[*ReactJS*](https://facebook.github.io/react/) takes a simple enough approach:

> For a given state describe how to render your application.

Thus we need concepts and tools to compliment ReactJS when we want to build an application.

----

### Components

A *Component* is a description of how to render a part of our application, like a button.

```JavaScript
//A simple button component.
import React from 'react'

const button = ({disabled, text, click}) => (
    <button onClick={disabled ? () => {} : click} >
        {text}
    </button>
)

export default button
```

---

# Redux

> Redux is a predictable state container for JavaScript apps.

----

A popular approach to handle this `state` that ReactJS renders is [*Redux*](http://redux.js.org/).

It takes a unidirectional approach to dataflow. Meaning data only flows in a single direction. This makes our application more predictable.

----

<img id="flowDiagram" src="res/redux-flow.png" style="height: 45vh;padding: 3rem;" />
<label for="flowDiagram">
    Visualizing dataflow in Redux
</label>

----

### Store

The *Store* is the current representation of the state of your application.

```JavaScript
//The store is simply one big object in JavaScript.
{
    printing: false,
    orders: [...]
}
```

----

### Actions

You can think of this as an event. While the *Action* is the actual thing being propagated there are also *Actioncreators* which are functions used to create an action.

```JavaScript
//Use ES6 Syntax to define a function.
export const startPrinting = () => {
    return {
        type: 'PRINTING_START'
    }
}
```

----

### Reducers

*Reducers* are function that take a current store and return a new one based on an Action.

```JavaScript
//Return a state for the action or a standard one.
const printing = (state = false, action) => {
    if(action.type === 'PRINTING_START') {
        return true
    } else if(action.type === 'PRINTING_STOP') {
        return false
    } else {        
        return state
    }
}
```

---

# Pure functions

----

## Definition

A pure function is one that fulfills two conditions:

- For a given input it always returns the same output
- It has no *"side effects"*
-
----

## Gains

- Testability
- Predictability
- Timetravel

We gain a lot from making our Components and Reducers pure functions and also have our Reducers return new Objects.

----

<img id="flowDiagram" src="res/updateStore1.png" style="height: 45vh;padding: 3rem;" />

----

<img id="flowDiagram" src="res/updateStore2.png" style="height: 45vh;padding: 3rem;" />

----

<img id="flowDiagram" src="res/updateStore.png" style="height: 45vh;padding: 3rem;" />

---

# Folderstructure

----

### Overview

```
.
├── docs                        All documentation lives here
│   ├── actions                 Redux Action documentation
│   ├── config                  Config to generate docs
│   └── templates               Templates to generate docs
├── node_modules                NPM dependencies
├── package.json            
├── src                        
│   ├── cssPre                  Your CSS preprocessing language of choice
│   ├── img                     Image resources
│   └── js                      JavaScript files
├── test                    
│   ├── reducers                Testing your reducers
│   └── test.js                 Entry point for all tests
└── webpack.config.js           Webpack configuration
```

----

### JS Folderstructure

```
.
├── actions
│   └── index.js                Your Actioncreators
├── components                  Visible components
│   ├── button.js
│   └── orderList.js
├── containers                  Redux containers
│   └── visibleOrderList.js
├── index.js                    The main entry point
└── reducers                    Reducers for each part of the store
    ├── index.js
    └── ordersReducer.js
```

----

Folderstructure helps especially to quickly find the JS files to work on, mainly distinguishing between:

- Reducers
- Components
- Containers
- Actions

---

# Testing

----

### Reducers

Since our reducers are pure functions they are an ideal thing to test.

[*Tape*](https://github.com/substack/tape) is a lightweight testing framework for JavaScript. Let's look at how to use it for our ReactJS application.

----

### Testfiles

```
.
├── reducers
│   ├── orders.js               Testing orders reducer
│   └── printing.js             Testing printing reducer
└── test.js                     Entry point for all tests
```


---

# Debugging

---

# To tackle a problem

---

# Links

Helpful things and further reading.

----

### This is build using:

- Reveal for JS based slides
- Reveal-md for prototyping
- [nodetree](https://www.npmjs.com/package/nodetree) for nice filetrees

----

### Follow the links

- [Introducing React](https://www.youtube.com/watch?v=XxVg_s8xAms)
- [Redux devtools](https://github.com/gaearon/redux-devtools)

<!-- Create some styles -->
<style>
    @media print {
        img {
            min-height: 300px;
        }
    }
</style>
