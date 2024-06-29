# react-js-development

* [React JS]()
  
* [Core Concepts]()
  * [Virtual DOM]()
  * [Components]()
  * [Context API]()
  * [React Hooks]()
  * [React Router]()
  * [Error boundary]()
  * [Lazy loading]()
  * [SSR- Server Side Rendering]()
  * [Adding Style -CSS]()
  * [State and Props]()
  * [Unit Testing]()
    
* [Redux State Management]()
  * [Redux toolkit]()
  * [Redux Thunk]()
  * [Redux Saga]()
    
* [React Hooks]()
  * [Use State Hook]()
  * [Use Effect Hook]()
    
* [Handling Forms]()
* [Material UI Framework]()
* [Questions and Answers]()
  
* [Coding Snippets](https://github.com/kaleeswariP/react-js-development#coding-snippets)
  * [Redux toolkit Basic](https://github.com/kaleeswariP/react-js-development#redux-toolkit-code-snippet)
  * [Context API implementation]()
  * [Custom Hook implementation]()
  * [Redux toolkit with redux-saga]()
  * [React-router sample]()
  
* [Coding concepts challenges](https://github.com/kaleeswariP/react-js-development#coding-concepts-challenges)
  
* [Sample functionalities implementation](https://github.com/kaleeswariP/react-js-development#sample-functionalities-implementation)
  * [Implement the below UI functionality](https://github.com/kaleeswariP/react-js-development?tab=readme-ov-file#1-implement-the-below-ui-with-functionality)
  * [Counter functionality](https://github.com/kaleeswariP/react-js-development?tab=readme-ov-file#2-implement-the-counter-functionality)

* [React Project Development Tools]()
  * [Storybook]()
  * [Webpack]()
  * [Charts libraries]()
  * [Jest & React Testing Library]()
  * [Babel, env, prettier, linter]()
 
* [Other Frameworks]()
  * [Next JS]()
  * [Vue JS]()
  * [Gatsby]()
  
## React JS
React.js is a popular open-source JavaScript library developed by Facebook for building user interfaces, particularly for single-page applications.

React allows developers to create large web applications that can update and render efficiently in response to data changes.

### Core concepts of React.js

##### **Components:**
React is all about building reusable components. Components are the building blocks of a React application, representing parts of the user interface.
Components can be class-based or function-based (functional components).

Example of a simple functional component:
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

##### **JSX (JavaScript XML):**
*JSX is a syntax extension for JavaScript that looks similar to HTML and is used with React to describe what the UI should look like.*

JSX gets transpiled to JavaScript by tools like Babel before being executed by the browser.

Example of JSX:
```jsx
const element = <h1>Hello, world!</h1>;
```
##### **Props:**
Props (short for properties) pass data from one component to another. They are read-only and cannot be modified by the receiving component.

Example of passing props:
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

<Greeting name="Alice" />
```

##### **State:**

State is a built-in object that allows components to create and manage their data. Unlike props, the state is mutable and can be changed within the component.

Example of state in a class component:
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

##### **Lifecycle Methods:**

Class components in React have lifecycle methods that allow developers to run code at particular times in the component's life `(e.g., mounting, updating, unmounting)`.

Common lifecycle methods include `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

##### **Hooks:**

Hooks are functions that let you use state and other React features in functional components.
Common hooks include `useState`, `useEffect`, and `useContext`.

Example of useState and useEffect hooks:
```jsx
import React, { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

##### **Virtual DOM:**

The virtual DOM is a lightweight copy of the actual DOM. React uses the virtual DOM to efficiently update the real DOM by only re-rendering changed nodes.

This improves performance by minimizing the number of costly DOM manipulations.

##### **One-Way Data Binding:**

React enforces a one-way data flow, meaning that data flows from parent to child components via props. This makes it easier to understand and debug applications.

##### **Declarative UI:**

React allows developers to describe what the UI should look like for a given state, and React handles updating the UI when the state changes.

This declarative approach makes code more predictable and easier to debug.

##### **React Router:**

React Router is a library used to handle routing in React applications, allowing for the creation of single-page applications with multiple views.

Example of basic React Router usage:
```jsx
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/about" component={About} />
        <Route path="/" component={Home} />
      </Switch>
    </Router>
  );
}
```

## Core Concepts

### Virtual DOM

### Components
In React.js, components are the building blocks of the application. 
They allow developers to split the UI into independent, reusable pieces that can be managed separately. 
There are several types of components in React, each serving a different purpose and providing various functionalities.

#### Functional Components
Definition: Functional components are simple JavaScript functions that accept props as arguments and return React elements (JSX).

Characteristics:

* Stateless until the introduction of hooks.
* Simpler and easier to test.
* Can use hooks to manage state and lifecycle methods.
  
Example:
```jsx
Copy code
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage
<Welcome name="Alice" />
```

#### Class Components
Definition: Class components are ES6 classes that extend React.Component and have a render method that returns React elements (JSX).

Characteristics:

* Can hold and manage state.
* Have access to lifecycle methods.

Example:
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

// Usage
<Welcome name="Alice" />
```
##### Lifecycles of class component

##### Pure Components
Definition: Pure components are a type of class component that implements shouldComponentUpdate with a shallow prop and state comparison.

Characteristics:

* Avoid unnecessary re-renders, improving performance.
* Used when the component's render output depends only on its props and state.

Example:
```jsx
import React, { PureComponent } from 'react';

class PureWelcome extends PureComponent {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

// Usage
<PureWelcome name="Alice" />
```

#### Higher-Order Components (HOC)
Definition: HOCs are functions that take a component and return a new component with additional props or behavior.

Characteristics:

* Useful for reusing component logic.
* Do not modify the original component; instead, they compose them.

Example:
```jsx
function withLogging(WrappedComponent) {
  return class extends React.Component {
    componentDidMount() {
      console.log('Component Mounted');
    }

    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
}

// Usage
const EnhancedComponent = withLogging(Welcome);
```

#### Context Components
Definition: Context components are used to pass data through the component tree without having to pass props down manually at every level.

Characteristics:
* Useful for global data like themes, user information, or settings.

Example:
```jsx
const ThemeContext = React.createContext('light');

class ThemedButton extends React.Component {
  render() {
    return (
      <ThemeContext.Consumer>
        {theme => <button className={theme}>Button</button>}
      </ThemeContext.Consumer>
    );
  }
}

// Usage
<ThemeContext.Provider value="dark">
  <ThemedButton />
</ThemeContext.Provider>
```
#### Stateless Functional Components: 

These are simpler alternatives to class components and are just JavaScript functions that receive props and return JSX.

#### Other Techniques in Creating Component

##### Render Props
Definition: A technique for sharing code between React components using a prop whose value is a function.

Characteristics:
* Allows dynamic behavior in components.
  
Example:
```jsx
class MouseTracker extends React.Component {
  constructor(props) {
    super(props);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove = (event) => {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  }

  render() {
    return (
      <div onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}

// Usage
<MouseTracker render={({ x, y }) => (
  <h1>The mouse position is ({x}, {y})</h1>
)} />
```

##### Forwarding Refs
Definition: A technique to automatically forward refs to the underlying DOM element in a component.

This is used in `useRef` hook implementation

Characteristics:
* Useful for higher-order components and reusable components.

Example:
```jsx
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="fancy-button">
    {props.children}
  </button>
));

// Usage
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>
```

## Redux State Management

## React Hooks

## Form Handling

## Material UI Framework

# Questions and Answers

# Coding Snippets

## Redux toolkit code snippet

Link - https://codesandbox.io/p/sandbox/redux-toolkit-sample-hzw96y?file=%2Fsrc%2Fapp%2Fstore.js%3A9%2C1

# Coding concepts Challenges
**Execution Link of all the challenges** - 

## 1. What is the output of the code below? 

The setState method works asynchronously.

```import React from 'react';

class SetStateChalComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { Number: 0 };
  }

  componentDidMount() {
    this.setState({ Number: 1 });
    console.log(this.state.Number);
    this.setState({ Number: 2 });
    console.log(this.state.Number);
    this.setState({ Number: 3 });
    console.log(this.state.Number);
  }

  render() {
    return <div>setState output: {this.state.Number}</div>;
  }
}

export default SetStateChalComponent;
```
## 2. Event delegation and event bubbling challenge
 
 When clicking on the button both the onClick functions will be called(div and button) due to the event bubbling in jsx so we need to delegate an event properly.

```
import React from 'react';

const EventBubbleGoalComponent = () => {
  const shoot = (message, event) => console.log(message);
  return (
    <div>
      <div
        style={{ margin: '2px', padding: '10px' }}
        onClick={(event) => shoot('no goal', event)}
      >
        <button onClick={(event) => shoot('goal', event)}>click me</button>
      </div>
    </div>
  );
};

export default EventBubbleGoalComponent;

```

### 3. Routing challenge

Setting the path to * will be a catch-all for any undefined URLs. This is great for a 404 error page.
The nested <Route>s inherit and add to the parent route.

```
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import About from './Pages/About.jsx';
import HomePage from './Pages/Home.jsx';
import NoPage from './Pages/No.jsx';
import HomeComponent from './Home.jsx';

export default function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<HomeComponent />}>
          <Route index element={<HomePage />} />
          <Route path="about-us" element={<About />} />
          <Route path="*" element={<NoPage />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

```

### 4. useEffect hook dependency task



# Sample functionalities implementation

## 1. Implement the below UI with functionality
#### Custom Hook: 
Custom hooks should start with use, like useFormInput or useFetch.
Use React's built-in Hooks within your custom Hook as needed.
Return anything that will be useful for the component using this Hook.
Each custom hook should be responsible for a single piece of functionality.

Constraints:<br>
* It should have a useCallback hook
* It should have a custom hook
  
Use Case: Generate 3(dynamic) random numbers and check on the button click if those are the same show "JackPot!" otherwise give some message.

**UI**
![image](https://github.com/kaleeswariP/react-js-development/assets/22699303/1d1710e5-2b7c-48ec-8f64-f55a70367f03)

file name - ```customHook.js```
```javascript

import { useCallback, useEffect, useState } from "react";

export const useRandomHook = (count) => {
  const [array, setRandom] = useState([]);

  const verifyLuck = useCallback((array) => {
    return array.every((val, i, arr) => val === arr[0]);
  });

  const generateRandomNumbers = () => {
    let random = [];
    for (let i = 0; i < count; i++) {
      random.push(Math.floor(Math.random() * 10));
    }
    setRandom(random);
  };

  return [array, verifyLuck, generateRandomNumbers];
};

```

file name is ```checkLuck.js```

```javascript
import { useRandomHook } from "./customHooks.js";

const CheckLuck = () => {
  // Moved to custom hook
  // const [randoms, setRandoms] = useState([]);
  // const [isJackPot, setJackPot] = useState(false);
  const [hookVal, isMatch, tryLuck] = useRandomHook(3);

  // Moved to custom hook
  // const verifyLuck = useCallback((array) => {
  //   return array.every((val, i, arr) => val === arr[0]);
  // });

  const onTryLuck = () => {
    tryLuck();
    // setRandoms(randomNumbers);
    // setJackPot(verifyLuck(randomNumbers));
  };

  return (
    <>
      <div
        style={{
          display: "flex",
          alignItems: "center",
          alignContent: "center",
        }}
      >
        {hookVal.map((val) => (
          <p
            style={{
              width: "20px",
              border: "2px solid #767678",
              borderColor: "black",
              padding: "2px",
              margin: "5px",
            }}
          >
            {val}
          </p>
        ))}
        <button onClick={onTryLuck}>Try your luck</button>
      </div>
      <>{isMatch(hookVal) ? <p> JackPot!!</p> : <p> OOPS! Try next time </p>}</>
    </>
  );
};

export default CheckLuck;
```

## 2. Implement the counter functionality

Constraints:<br>
* Use the redux toolkit for the state management
* It should add the counter value asynchronously
* It should increment the counter by the given value

Create the store and configure the reducers.
filename is ```store.js```

```javascript
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from '../features/counter/counterSlice';

export default configureStore({
  reducer: {
    counter: counterReducer,
  },
});

```

Pass/configure the store to the application in ```main.js/app.js/index.js``` file

```javascript
import { Provider } from 'react-redux';
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

Create a slice for the counter feature in the ```counterSlice.js``` file.
```javascript
import { createSlice } from '@reduxjs/toolkit'

export const counterSlice = createSlice({
  name: 'counter',
  initialState: {
    value: 0,
  },
  reducers: {
    increment: (state) => {
      // Redux Toolkit allows us to write "mutating" logic in reducers. It doesn't mutate the state because it uses the immer library, which detects changes to a "draft state" and produces a brand new immutable state based on those changes
      state.value += 1
    },
    decrement: (state) => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    },
  },
})

export const { increment, decrement, incrementByAmount } = counterSlice.actions

// The function below is called a thunk, allowing us to perform async logic. It can be dispatched like a regular action: `dispatch(incrementAsync(10))`. This will call the thunk with the `dispatch` function as the first argument. Async code can then be executed and other actions can be dispatched
export const incrementAsync = (amount) => (dispatch) => {
  setTimeout(() => {
    dispatch(incrementByAmount(amount))
  }, 1000)
}

// Selector and allows us to select a value from the state..For example: `useSelector((state) => state.counter.value)`
export const selectCount = (state) => state.counter.value

export default counterSlice.reducer

```
and the main UI component is as follows, filename is 'counter.js'
```javascript
import React, { useState } from "react";
import { useSelector, useDispatch } from "react-redux";
import {
  decrement,
  increment,
  incrementByAmount,
  incrementAsync,
  selectCount,
} from "./counterSlice";
import styles from "./Counter.module.css";

export function Counter() {
  const count = useSelector(selectCount);
  const dispatch = useDispatch();
  const [incrementAmount, setIncrementAmount] = useState("2");

  return (
    <div>
      <div className={styles.row}>
        <button
          className={styles.button}
          aria-label="Increment value"
          onClick={() => dispatch(increment())}
        >
          +
        </button>
        <span className={styles.value}>{count}</span>
        <button
          className={styles.button}
          aria-label="Decrement value"
          onClick={() => dispatch(decrement())}
        >
          -
        </button>
      </div>
      <div className={styles.row}>
        <input
          className={styles.textbox}
          aria-label="Set increment amount"
          value={incrementAmount}
          onChange={(e) => setIncrementAmount(e.target.value)}
        />
        <button
          className={styles.button}
          onClick={() =>
            dispatch(incrementByAmount(Number(incrementAmount) || 0))
          }
        >
          Add Amount
        </button>
        <button
          className={styles.asyncButton}
          onClick={() => dispatch(incrementAsync(Number(incrementAmount) || 0))}
        >
          Add Async
        </button>
      </div>
    </div>
  );
}
```









