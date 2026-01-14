# ReactJs
```
Visual Studio Code
Node Js

React Js is a javascript library . its single page app, and client side rendering

React js having virutal dom whenever u make state,prop changes only those changes will compare and replace in Main dom so whole page reloading will not happens
OR
React keeps a Virtual DOM (an in-memory representation of the UI).
When state/props change, React re-renders the component tree to produce a new Virtual DOM.
React then diffs (compares) the new vs. previous Virtual DOM and computes the minimal set of changes.
Finally, React updates the real DOM (often called “main DOM”) with only those necessary changes (reconciliation + commit).

React always returns a single Element

Babel - JS compiler
-------
Whenever you will create the React app basically babel gets created
Whenever u write a jsx code babel converts that code into Browser Understandable code that is JS

Converts JSX to JavaScript
Example: <h1>Hello</h1> becomes regular JavaScript code that React can run.

Extension
------------
EsLint
Prettier

npx create-react-app moviedux 
npm start

Serialization : convert object type to json type(data storing type)
DeSerialization : convert back from json to object type

State
---------
Manage Component Data
When the state values changes, the UI Re-Renders.

Consists of 2 parts (getting, setting)

1)UseState
2)UseEffect

Use Props
------------
Use for Event Handling , to pass data ,functions to component
You can pass props to nested component "Props Drilling"

Props Destructure
-------------------


import './App.css'

function Book({name,age})
{
  return <h1> {name} its My book and my age is {age}</h1>
}

function App() {

  return (
    <>
    <Book name="Manoj" age="27"/>
    <h1>Micro Degree</h1>
    </>
  )
}

export default App


UseReducer
------------

The useReducer hook is a built-in React hook that provides an alternative to useState for managing state in functional components. It is particularly useful when:

State logic is complex (e.g., involves multiple sub-values or decisions).
The next state depends on the previous state.
You want a more predictable and maintainable way to update state—especially as your application grows.









```
