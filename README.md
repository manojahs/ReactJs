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

function Book({name,age,children})
{

  return <>
  <h1> {name} </h1>
  <h1>{age}</h1>
   {children}
  <h1>Namma MicroDegree</h1>
   </>
}


function App() {

const firstName ={
  name:"Manoj",
  age:27  
}

const secondName ={
  name:"Nikki",
  age:40
}


  return (
    
    <>
    <Book name={firstName.name} age={firstName.age}/>
    <Book name={secondName.name} age={secondName.age}/>
    <Book name="kamal">This book is Awesome</Book>
    </>
  )
}

export default App

Or

By considering it in Array of objects

import './App.css'

function Book({name,age,children})
{

  return <>
  <h1> {name} </h1><h1>{age}</h1>
   {children}
  <h1>Namma MicroDegree</h1>
   </>
}


function App() {

const BookList=[
  {
      name:"Manoj",
      age:27  
  },
  {
      name:"Nikki",
      age:40
  }
]


  return (
    
    <>
    {
     BookList.map((book)=>
      {
        return <Book name={book.name} age={book.age}/>
      }
    )
    }
   
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

React Hooks
------------
Use State- This is state management hooks we can change the state dynamically

ex: title will be Manoj after button click title name will get change as Kumar

import logo from "./logo.svg";
import "./App.css";
import { useState } from "react";

function App() {
  const [state, setState] = useState("Manoj");

  function handleClick(e) {
    setState("Kumar");
  }

  return (
    <div>
      <h1>{state}</h1>
      <button type="button" value={state} onClick={handleClick}>
        Click Me
      </button>
    </div>
  );
}

export default App;

UseEffect
---------
->This is the hook we ll be using it in Re-Render operation
->Main thing we use it for Fetching the data 

  useEffect(() => {
    console.log(data);
  });
If its having only function then its prints for reach re-render
-------------------------
  useEffect(() => {
    console.log(data);
  }, []);
If its having array as 2nd param then it runs only once
-------------------------------
 const [count, setCount] = useState(0);

  const increaseValue = () => {
    setCount(count + 1);
  };

  useEffect(() => {
    console.log(data);
  }, [count]);

If there are so many components then ur useeffect should work only for one specific component then u can use that state in the array. this kind of use affect array we call it as Dependency array. whenever count value changes use effect will print the console data 

-> In one component u can add many UseEffect hooks

how to written multiple return statement
-------------------------------------
Here comes Conditional Rendering 

function App() {
  const [loading, setLoading] = useState(false);
  if (loading) {
    return <div>Loading...</div>;
  }
  return <div>Not Loading..</div>;
}

Short Circuit Evaluation
--------------------------
const [text, setText] = useState("microdegree");
const firstName = text || "Guest"; //microdegree in OR Condition
const lastName = text && "Guest"; //Guest in AND Condition

Ternary Operator
-------------------
function App() {
  const [value, setValue] = useState("");
  return <div>{value ? "Value is there" : "Empty String"}</div>;
}

we cannot add if or else condition in return statement that is why we use Ternary Operator

React Forms
-----------

Basically we use for submit the form or page

import logo from "./logo.svg";
import "./App.css";
import { useState } from "react";

function App() {
  const [name, setName] = useState("");
  const [age, setAge] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(name + " " + age);
  };
  return (
    <div>
      <form onSubmit={handleSubmit}>
        <label htmlFor="name">Name</label>
        <input
          type="text"
          id="name"
          name="name"
          value={name}
          onChange={(e) => {
            setName(e.target.value);
          }}
        />
        <label htmlFor="age">Age</label>
        <input
          type="number"
          id="age"
          name="age"
          value={age}
          onChange={(e) => setAge(e.target.value)}
        />

        <button type="submit">Submit</button>
      </form>
    </div>
  );
}

export default App;

------------------------------------------
React Route
-------
Mainly we for Home , About , Contact for different navigation path we use Route

npm install react-router-dom
npm start

import logo from "./logo.svg";
import "./App.css";
import { useState } from "react";
import Home from "./Home.js";
import Abouts from "./About.js";
import Contact from "./Contact.js";
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";

function App() {
  return (
    <div>
      <Router>
        <Routes>
          <Route path="/home" Component={Home} />
          <Route path="/about" Component={Abouts} />
          <Route path="/contact" Component={Contact} />
        </Routes>
      </Router>
    </div>
  );
}

export default App;

----------------------------------------

Route-Link
--------------
Imported Link Tag and we need to use to to give the Link Path

import { Link } from "react-router-dom";

export default function Home() {
  return (
    <div>
      <ul>
        <li>
          <Link to="/"> Home </Link>
        </li>
        <li>
          <Link to="/about"> About </Link>
        </li>
        <li>
          <Link to="/contact"> Contact </Link>
        </li>
      </ul>
    </div>
  );
}

React Context
-----------------
React Context is React’s built-in way to pass data (state + functions) through a component tree without “prop drilling”—useful when many nested components need the same value (e.g., theme, locale, current user, feature flags).

Here we will Use useContext and CreateContext

import logo from "./logo.svg";
import "./App.css";

function App() {
  const userInfo = {
    username: "Manoj",
    isAdmin: true,
  };

  return (
    <div>
      <h1>Post Title</h1>
      <Post userInfo={userInfo} />
    </div>
  );
}

function Post({ userInfo }) {
  return (
    <div>
      <h1>Post Comments</h1>

      <Comments userInfo={userInfo} />
    </div>
  );
}

function Comments({ userInfo }) {
  return (
    <div>
      <h1>{userInfo.username}</h1>
      <button></button>
    </div>
  );
}
export default App;

Reason to Use UseContext
------------------------
Prop drilling is when you pass data (props) from a top component to a deeply nested component through several intermediate components that don’t actually need the data—only to “carry it along.”


React Vite Version 19
----------------------

npm create vite@latest

npx vite/npm run dev

npm run build/npx vite build -> it will create dist file

Consider there are 2 env file
1)Dev - VITE_API_URL = "localhost:3000/api"
2)Production - VITE_API_URL = "https://myserver.com/api"

to get the env variable
---------------------
  const apiUrl = import.meta.env.VITE_API_URL;

To run the application
1)npm run dev - Development
2)npm run preview - Production 

Unit Testing
----------------------
npm install -D vitest @testing-library/react @testing-library/jest-dom

vitest
jtest


```
