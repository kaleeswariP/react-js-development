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
  * [Custom Hook]()
  * [Use State Hook]()
  * [Use Effect Hook]()
  * [Use Ref Hook]()
    
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

* [Virtual DOM]()
* [Components]()
* [Context API]()
* [React Hooks]()
* [React Router]()
* [Axios]()
* [Fetch API]()
* [Error boundary]()
* [Lazy loading]()
* [SSR- Server Side Rendering]()
* [Adding Style -CSS]()
* [State and Props]()
* [Unit Testing]

### Virtual DOM

The Virtual DOM (VDOM) in React.js is a concept that enhances the performance and efficiency of updating the user interface (UI) in web applications. Here’s a detailed explanation:

#### What is the Virtual DOM?

* Representation of the Real DOM:
  *The Virtual DOM is an in-memory representation of the actual DOM elements.
  *It is a lightweight copy of the real DOM that React uses to determine how the UI should change.

* How it Works:
  * When a component’s state or props change, React creates a new Virtual DOM tree.
  * React then compares this new Virtual DOM tree with the previous one using, a process called “diffing.”

* Efficient Updates:
  * The differences (or “diffs”) between the old Virtual DOM and the new one are calculated.
React then updates only the parts of the real DOM that have changed, rather than re-rendering the entire page.
  * This minimizes the number of manipulations to the real DOM, which is a costly operation in terms of performance.

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

**Phases of the Lifecycle**
1. **Mounting:** When an instance of a component is being created and inserted into the DOM.
2. **Updating:** When a component is being re-rendered as a result of changes to its props or state.
3. **Unmounting**: When a component is being removed from the DOM.

**Summary of Lifecycle Methods**<br><br>
* **Mounting:** `constructor()`, `getDerivedStateFromProps()`, `render()`, `componentDidMount()`.
* **Updating**: `getDerivedStateFromProps()`, `shouldComponentUpdate()`, `render()`, `getSnapshotBeforeUpdate()`, `componentDidUpdate()`.
* **Unmounting:** `componentWillUnmount()`.

**Lifecycle Methods**

**Mounting Phase**
1. `constructor(props)`:
    * Called before the component is mounted.
    * Used for initializing state and binding event handlers.
```javascript
constructor(props) {
  super(props);
  this.state = { count: 0 };
}
```
2. `static getDerivedStateFromProps(props, state)`:
    * Called right before rendering the element(s) in the DOM.
    * Used to update the state based on the props.
```javascript
static getDerivedStateFromProps(nextProps, prevState) {
  if (nextProps.someValue !== prevState.someValue) {
    return { someValue: nextProps.someValue };
  }
  return null;
}
```
3. `render()`:
    * The only required method in a class component.
    * Returns the JSX representing the component's UI.
```javascript
render() {
  return <div>{this.state.count}</div>;
}
```
4. `componentDidMount()`:
    * Called after the component is mounted and rendered.
    * Used for side effects like fetching data from APIs.
```javascript
componentDidMount() {
  fetch('/api/data')
    .then(response => response.json())
    .then(data => this.setState({ data }));
}
```
**Updating Phase**<br>

1. `static getDerivedStateFromProps(props, state)`:
    * Same as in the mounting phase, but called when the component receives new props or state.

2. `shouldComponentUpdate(nextProps, nextState)`:
    * Called before rendering when new props or state are received.
    * Used for performance optimization. Return true or false to control whether the component should update.

```javascript
shouldComponentUpdate(nextProps, nextState) {
  return nextState.count !== this.state.count;
}
```
3. `render()`:
    * Same as in the mounting phase.
      
4. `getSnapshotBeforeUpdate(prevProps, prevState)`:
    * Called right before the DOM is updated.
    * Used to capture some information from the DOM before it changes.
```javascript
getSnapshotBeforeUpdate(prevProps, prevState) {
  if (prevProps.list.length < this.props.list.length) {
    return this.listRef.scrollHeight;
  }
  return null;
}
```
5. `componentDidUpdate(prevProps, prevState, snapshot)`:

    * Called after the component is updated.
    * Used to operate on the DOM after the changes have been made.

```javascript
componentDidUpdate(prevProps, prevState, snapshot) {
  if (snapshot !== null) {
    this.listRef.scrollTop = this.listRef.scrollHeight - snapshot;
  }
}
```

**Unmounting Phase**<br>

1. `componentWillUnmount()`:
    * Called right before the component is unmounted and destroyed.
    * Used for cleanup tasks like invalidating timers, canceling network requests, or cleaning up subscriptions.

```javascript
componentWillUnmount() {
  clearInterval(this.timerID);
}
```



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

### Context API
The Context API in React.js is a feature that allows for the sharing of state across the entire app (or part of it) without passing props down manually at every level of the component tree.

It provides a way to create global variables that can be passed around, which is useful for things like themes, user settings, and authenticated user data.

#### How Context API Works

1. Context:

  * A Context object (React.createContext()) is created.
  * It returns an object with two React components: Provider and Consumer.

 ```javascript
import React, { createContext } from 'react';

const MyContext = createContext();

 ```

2. Provider:

  * The Provider component, is used to wrap parts of your application where you want to make the context available.
  * It accepts a value prop, the data you want to make available to the components that consume this context.

```javascript
import React, { useState } from 'react';

const MyProvider = ({ children }) => {
  const [state, setState] = useState(initialState);

  return (
    <MyContext.Provider value={{ state, setState }}>
      {children}
    </MyContext.Provider>
  );
};

``` 
3. Consumer:
  * The Consumer component is used to access the context data.
  * It takes a function as a child, which receives the current context value and returns a React node.
```javascript
import React from 'react';

const MyComponent = () => (
  <MyContext.Consumer>
    {context => (
      <div>
        {context.state.someValue}
      </div>
    )}
  </MyContext.Consumer>
);

```
4. useContext Hook:

  * In functional components, the useContext hook can be used to access the context directly.
  * This hook simplifies the process by eliminating the need for the Consumer component.
```javascript
import React from 'react';

const MyComponent = () => (
  <MyContext.Consumer>
    {context => (
      <div>
        {context.state.someValue}
      </div>
    )}
  </MyContext.Consumer>
);

```

[Refer sample theme context implementation]()

## Redux State Management

### Redux

### Redux-saga

### Redux-thunk

[Refer redux-toolkit basics example]()

## React Hooks

## Form Handling
Handling forms in React.js involves managing form state, capturing user input, and responding to form submissions

1. Set Up State to Manage Form Data:
   * Use the useState hook to create state variables for each form field.
2. Create Form Elements:
   * Use HTML form elements such as <input>, <textarea>, and <select> to create the form.
3. Handle Form Field Changes:
   * Create event handler functions to update the state when a form field value changes.
4. Handle Form Submission:
   * Create a submit handler function to process the form data when the form is submitted.
  
### Example: Simple Form

set up state:

```javascript
import React, { useState } from 'react';

const SimpleForm = () => {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');

  const handleNameChange = (event) => {
    setName(event.target.value);
  };

  const handleEmailChange = (event) => {
    setEmail(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Name:', name);
    console.log('Email:', email);
    // Here, you can send the data to a server or perform other actions
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>
          Name:
          <input type="text" value={name} onChange={handleNameChange} />
        </label>
      </div>
      <div>
        <label>
          Email:
          <input type="email" value={email} onChange={handleEmailChange} />
        </label>
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default SimpleForm;

```
This is done using the JSX syntax, as shown in the example above. 
  * The value attribute of each input is bound to the state variable, and the onChange attribute is used to handle updates to the state.
  * The `handleNameChange` and `handleEmailChange` functions update the state whenever the user types in the input fields.
  * The `handleSubmit` function prevents the default form submission behavior and processes the form data (e.g., logging it to the console).


### Example: Advanced Form fields with the single state object

form.js

```javascript
import React, { useState } from 'react';

const AdvancedForm = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: ''
  });

  const handleChange = (event) => {
    const { name, value } = event.target;
    setFormData({
      ...formData,
      [name]: value
    });
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log('Form Data:', formData);
    // Perform form validation or send data to a server
  };

  return (
    <form onSubmit={handleSubmit}>
      <div>
        <label>
          Name:
          <input type="text" name="name" value={formData.name} onChange={handleChange} />
        </label>
      </div>
      <div>
        <label>
          Email:
          <input type="email" name="email" value={formData.email} onChange={handleChange} />
        </label>
      </div>
      <div>
        <label>
          Password:
          <input type="password" name="password" value={formData.password} onChange={handleChange} />
        </label>
      </div>
      <button type="submit">Submit</button>
    </form>
  );
};

export default AdvancedForm;
```
Form Validation:

You can add validation logic inside the handleSubmit function or use the onChange handlers to validate individual fields.

```javascript
const handleSubmit = (event) => {
  event.preventDefault();
  if (!formData.name) {
    alert('Name is required);
    return;
  }
  if (!formData.email.includes('@')) {
    alert('Email is invalid');
    return;
  }
  console.log('Form Data:', formData);
  // Submit form data
};

```

For more complex forms, consider using libraries like Formik and Yup for easier form management and validation.

### Dynamic Form handling
Creating a dynamic form in React that can handle multiple data types involves several steps, including defining the form structure, managing form state, handling input changes, and dynamically rendering form fields based on the data types.

**Step-by-Step Guide**<br><br>
1. Define the Form Structure:
    * Create a schema or configuration that defines the form fields and their data types.
2. Manage Form State:
    * Use React state to manage the form data.
3. Handle Input Changes:
    * Create a function to handle changes to the form inputs and update the state accordingly.
4. Dynamically Render Form Fields:
    * Use the schema to dynamically render form fields based on their data types.
      
Example:

```javascript
import React, { useState } from 'react';

const formSchema = [
  { name: 'name', label: 'Name', type: 'text', required: true },
  { name: 'age', label: 'Age', type: 'number', required: true },
  { name: 'email', label: 'Email', type: 'email', required: true },
  { name: 'dob', label: 'Date of Birth', type: 'date', required: false },
  { name: 'isActive', label: 'Active', type: 'checkbox', required: false }
];

const DynamicForm = () => {
  const [formData, setFormData] = useState({});
  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    setFormData({
      ...formData,
      [name]: type === 'checkbox' ? checked : value
    });
  };

  const validate = () => {
    const newErrors = {};
    formSchema.forEach(field => {
      if (field.required && !formData[field.name]) {
        newErrors[field.name] = `${field.label} is required`;
      }
    });
    return newErrors;
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    const validationErrors = validate();
    if (Object.keys(validationErrors).length > 0) {
      setErrors(validationErrors);
    } else {
      setErrors({});
      console.log('Form Data:', formData);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      {formSchema.map((field) => (
        <div key={field.name}>
          <label>
            {field.label}:
            <input
              type={field.type}
              name={field.name}
              value={field.type === 'checkbox' ? undefined : formData[field.name] || ''}
              checked={field.type === 'checkbox' ? formData[field.name] || false : undefined}
              onChange={handleChange}
            />
          </label>
          {errors[field.name] && <span style={{ color: 'red' }}>{errors[field.name]}</span>}
        </div>
      ))}
      <button type="submit">Submit</button>
    </form>
  );
};

export default DynamicForm;

```

## Material UI Framework

## Axios

## FetchAPI implementation
The Fetch API is a modern interface for making network requests in JavaScript. 

When using React, the Fetch API can be used to retrieve data from a server and update your components with that data. 

Fetch API:

* The Fetch API provides a simple, standard way to make HTTP requests.
* It returns a Promise that resolves to the Response object representing the response to the request.

### Sample Fetch API implementation

1. Setting Up the Component:
  * Create a functional component.
  * Use the useState and useEffect hooks to manage state and side effects.
2. Fetching Data:
  * Use fetch() to make an HTTP request inside the useEffect hook.
  * Handle the Promise returned by fetch() to process the response.
3. Updating State:
  * Update the component’s state with the fetched data to trigger a re-render.

```javascript
import React, { useState, useEffect } from 'react';

const DataFetchingComponent = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      })
      .then(data => {
        setData(data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h1>Data from API</h1>
      <ul>
        {data.map(item => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
};

export default DataFetchingComponent;
```

### Advanced Fetch API Implementation

Handing post requests
```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ key: 'value' })
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```
using Async/await

```javascript
import React, { useState, useEffect } from 'react';

const AsyncDataFetchingComponent = () => {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://api.example.com/data');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        setData(data);
        setLoading(false);
      } catch (error) {
        setError(error);
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return (
    <div>
      <h1>Data from API</h1>
      <ul>
        {data.map(item => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </div>
  );
};

export default AsyncDataFetchingComponent;
```

## Error boundaries

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the whole component tree.

Creating an Error Boundary

1. Create a Class Component:

  * Error boundaries have to be class components because they rely on lifecycle methods not available in functional components.

2. Implement componentDidCatch and getDerivedStateFromError:
  * `componentDidCatch(error, info)`: This lifecycle method is called after an error has been thrown by a descendant component.
  * `getDerivedStateFromError(error)`: This static lifecycle method is called when an error is thrown, allowing you to update the state to show a fallback UI.

### Error boundary Example

```javascript
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Update state so the next render will show the fallback UI
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // You can also log the error to an error reporting service
    console.error('Error caught by ErrorBoundary:', error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // Fallback UI
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children;
  }
}

export default ErrorBoundary;

```
 Wrap the components that may throw errors with the `ErrorBoundary` component.

import React from 'react';
import ErrorBoundary from './ErrorBoundary';
import MyComponent from './MyComponent';

const App = () => (
  <ErrorBoundary>
    <MyComponent />
  </ErrorBoundary>
);

export default App;

### Other error-handling methods

#### Error Handling in Event Handlers

React does not automatically catch errors inside event handlers. You need to handle these manually.

```javascript
import React from 'react';

const MyComponent = () => {
  const handleClick = () => {
    try {
      // Code that may throw an error
      throw new Error('An error occurred!');
    } catch (error) {
      console.error('Caught an error:', error);
      // Handle the error appropriately
    }
  };

  return <button onClick={handleClick}>Click Me</button>;
};

export default MyComponent;

```
#### Error Handling in Asynchronous Code

Errors in asynchronous code (e.g., `fetch` requests) must be handled using `.catch()` for Promises or `try...catch` for `async/await` syntax.

Example with promises

```javascript
import React, { useEffect, useState } from 'react';

const DataFetchingComponent = () => {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      })
      .then(data => setData(data))
      .catch(error => setError(error));
  }, []);

  if (error) return <p>Error: {error.message}</p>;
  if (!data) return <p>Loading...</p>;

  return <div>Data: {JSON.stringify(data)}</div>;
};

export default DataFetchingComponent;
```
Example with `async/await`

```javascript
import React, { useEffect, useState } from 'react';

const AsyncDataFetchingComponent = () => {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://api.example.com/data');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        setData(data);
      } catch (error) {
        setError(error);
      }
    };

    fetchData();
  }, []);

  if (error) return <p>Error: {error.message}</p>;
  if (!data) return <p>Loading...</p>;

  return <div>Data: {JSON.stringify(data)}</div>;
};

export default AsyncDataFetchingComponent;

```

#### Displaying Error Messages
Displaying error messages to users can improve user experience. You can conditionally render error messages based on the state.

```javascript
import React, { useState } from 'react';

const LoginForm = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const [error, setError] = useState(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    if (username === '' || password === '') {
      setError('Username and password are required');
    } else {
      setError(null);
      // Perform login
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      {error && <p style={{ color: 'red' }}>{error}</p>}
      <div>
        <label>
          Username:
          <input
            type="text"
            value={username}
            onChange={(e) => setUsername(e.target.value)}
          />
        </label>
      </div>
      <div>
        <label>
          Password:
          <input
            type="password"
            value={password}
            onChange={(e) => setPassword(e.target.value)}
          />
        </label>
      </div>
      <button type="submit">Login</button>
    </form>
  );
};

export default LoginForm;

```

# Questions and Answers

### Error handling in react.js?
Error handling in React.js is an essential aspect of building robust applications. It involves capturing errors that occur <strong>during rendering<.strong>, **in lifecycle methods**, and **in asynchronous code**, and responding to them appropriately. 

1. Error Boundaries
Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the whole component tree.

Error handling in React involves 
* using error boundaries to catch errors during rendering and `lifecycle` methods,
* manually handling errors in event handlers
* managing asynchronous errors using `try...catch` or `.catch()`.
* displaying meaningful error messages to users.

By implementing these techniques, you can build more robust and user-friendly React applications.

Refer - [Error boundaries]()

### How do you configure webpack in the React JS app?
Refer [webpack]()
### How do you manage the side effects of the redux state management using redux-thunk or redux-saga?
Refer [Redux Thunk]() and [Redux saga]()

**What is Redux middleware**<br><br>
A Redux middleware lies between an action and a reducer. This enables actions to contain something else other than a plain object, as long as the middleware intercepts this, performs its logic, and returns a plain object to pass along to the reducer.

**Redux Thunk**<br><br>
Redux Thunk, a common alternative to Redux Saga, *allows functions to be passed into the Redux store dispatch, which checks to see if it is a function or an action object*, executing the function in the former case, and directly passing along the action object to the reducer in the latter case. 

These functions can then perform whatever complex asynchronous logic that they want and produce a plain action object to be then passed into the reducer.

[Refer sample](https://medium.com/@usamaijaz912/redux-thunk-real-examples-for-better-understanding-ed66ab732ac6)

**Redux Saga**<br><br>
Redux Sagas are slightly different in that *a separate set of actions is defined in your Redux application, which is captured exclusively by watcher functions (as part of your saga)*. 

Upon capturing the action, the saga will execute the corresponding logic and dispatch a resultant action to your application's reducer. 

The saga essentially acts as a separate thread to your application, listening for specific actions from your main application to perform complex asynchronous tasks and updating your application's state once it is completed.


### How to reduce the bundle size of the React JS applications?


### Can you detail how you would create a dynamic form in React that can handle multiple data types?

Refer to [Dynamic form handling]()

### When would you choose to use a class component over a functional component in React?
In modern React development, functional components are generally preferred due to their simplicity and the power provided by hooks. However, there are still certain situations where class components might be chosen over functional components. 

#### When to Choose Class Components:
1. **Legacy Codebases:** If you are working on an older codebase that primarily uses class components, it might be more consistent and practical to continue using class components to maintain a uniform codebase.
   
2. **Existing Expertise:** If your team has significant experience with class components and is less familiar with hooks, there might be a steeper learning curve to switch to functional components and hooks.
3. **Library or Framework Constraints:** Some third-party libraries or frameworks may still rely on or provide examples in class components. In such cases, using class components might simplify integration.
4. **Understanding Component Lifecycle:** If you need explicit control over component lifecycle methods (like shouldComponentUpdate, componentDidCatch), and are more comfortable using lifecycle methods directly instead of hooks, you might prefer class components.

##### Real-time Use cases
1. **Error Boundaries:** As of now, error boundaries can only be implemented using class components. Functional components do not support the lifecycle methods (componentDidCatch and getDerivedStateFromError) required for error boundaries.

Refer to [Error boundaries]()

2. **Complex Lifecycle Logic:**

If your component has complex lifecycle management that is better understood and managed with class lifecycle methods (`componentDidMount`, `componentDidUpdate`, `componentWillUnmount`), you might prefer using a class component. However, with hooks like `useEffect`, most of these scenarios can also be managed in functional components.

### How do you handle state management in a complex React application with nested components?

1. **Lifting State Up**: Lifting state up involves moving the state to the closest common ancestor of the components that need access to it. This method works well for relatively simple applications.
2. **Context API**: The Context API allows you to create a global state that can be accessed by any component in the tree without prop drilling. This is useful for medium-sized applications.
3. **Redux:** Redux is a state management library that provides a predictable state container. It is suitable for large and complex applications.
   

### How will you avoid rerendering child components in react?

1. **Use `React.memo`:** `React.memo` is a higher-order component that prevents a functional component from re-rendering if its props have not changed. Refer to [React Momo]()
2. **Use `useCallback` and `useMemo`:** `useCallback` and `useMemo` hooks help in memoizing functions and values, respectively, so that they are not re-created on every render.
3. **Split State into Multiple `useState` Hooks:** When state is managed using multiple `useState` hooks instead of a single state object, it can help reduce unnecessary re-renders.
4. **Use `shouldComponentUpdate` in Class Components:** In class components, you can override the shouldComponentUpdate lifecycle method to prevent unnecessary re-renders.
5. **Use `PureComponent`:** React.PureComponent automatically implements shouldComponentUpdate with a shallow prop and state comparison.
6. **Avoid Inline Functions and Objects:** Inline functions and objects are recreated on every render, causing child components to re-render. Using useCallback for functions and useMemo for objects helps prevent this.

Example for Inline function and Objects:
```javascript
const ParentComponent = () => {
  const [count, setCount] = useState(0);
  const [text, setText] = useState('');

  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []);

  const memoizedValue = useMemo(() => ({ text }), [text]);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <input value={text} onChange={(e) => setText(e.target.value)} />
      <ChildComponent onClick={handleClick} value={memoizedValue} />
    </div>
  );
};

const ChildComponent = React.memo(({ onClick, value }) => {
  console.log('ChildComponent rendered');
  return (
    <div>
      <button onClick={onClick}>Click me</button>
      <div>{value.text}</div>
    </div>
  );
});

```
### Is there any other available to communicate to the child component except props?
Yes, there are several other ways to communicate with child components in React besides using props. 

1. Context API
2. Refs
3. Custom Hooks
4. State Management Libraries


### How do you optimize webpage loading speeds while dealing with large CSS files?

1. **Minify CSS:** Minifying CSS files reduces their size by removing unnecessary characters such as spaces, comments, and line breaks.
    Tools: CSSNano, CleanCSS
2. **Split CSS:** Split your CSS into smaller chunks and load them as needed. This can be done using code-splitting techniques or by separating critical CSS from non-critical CSS.

  * Critical CSS: Load essential CSS required for above-the-fold content first.
  * Non-critical CSS: Load the rest of the CSS asynchronously.
```html
<!-- Inline critical CSS -->
<style>
  /* Critical CSS here */
</style>
<!-- Load non-critical CSS asynchronously -->
<link rel="stylesheet" href="styles.css" media="print" onload="this.media='all'">
<noscript><link rel="stylesheet" href="styles.css"></noscript>
```
3. **Use CSS-in-JS:** CSS-in-JS libraries, such as styled-components or emotion, help scope CSS to specific components, reducing the overall size of CSS.

Example with styled-components:
```javascript
import styled from 'styled-components';

const Button = styled.button`
  background: blue;
  color: white;
`;
```
4. **Optimize Images and Fonts:** Large images and fonts can slow down page load times, which indirectly affects the perceived performance of CSS. Optimizing these assets is also crucial.

Images: Compress images using tools like ImageOptim or TinyPNG.
Fonts: Use font-display: swap to ensure text remains visible during font loading.

5. **Lazy Load CSS:** Lazy load CSS files that are not immediately needed. This can be done using JavaScript.

Example:
```javascript
function loadCSS(href) {
  const link = document.createElement('link');
  link.rel = 'stylesheet';
  link.href = href;
  document.head.appendChild(link);
}

loadCSS('non-critical.css');
```
6. **Tree-Shaking Unused CSS**

### Can you outline your process for setting up a CI/CD pipeline for a full-stack application?

Setting up a CI/CD (Continuous Integration/Continuous Deployment) pipeline for a full-stack application involves several steps. This includes automating the build, test, and deployment processes to ensure efficient and reliable delivery of updates. 

1. **Project Setup**
    * Source Control Management: Ensure your project is in a version control system like Git and hosted on platforms such as GitHub, GitLab, or Bitbucket.
    * Branching Strategy: Define a branching strategy (e.g., GitFlow) to manage the development process.
2. **CI/CD Tool Selection**
Choose a CI/CD tool that suits your project needs. Popular choices include:
* Jenkins
* GitHub Actions
* GitLab CI
* CircleCI
* Travis CI
3. **Configuration**
Create configuration files for the CI/CD tool. These files define the steps for building, testing, and deploying your application.

Example with GitHub Actions: Create a `.github/workflows/ci-cd.yml` file.
4. Build Process
    * Install Dependencies: Ensure all project dependencies are installed.
    * Build Application: Compile or build the application (frontend and backend).
          * Frontend: Typically involves compiling assets using tools like Webpack, Babel, etc.
          * Backend: May involve compiling code or setting up the server.
5. Testing
    * Unit Tests: Run unit tests to ensure individual components work correctly.
    * Integration Tests: Run integration tests to ensure components work together.
    * End-to-End Tests: Run end-to-end tests to simulate user interactions and verify the entire application workflow.
6. Linting and Code Quality
    * Linting: Run linters (e.g., ESLint) to ensure code quality and style guidelines.            * Static Analysis: Run static analysis tools to detect potential issues.
7. Deployment
    * Staging Environment: Deploy to a staging environment for further testing.
    * Production Environment: Deploy to production after successful testing in the staging environment.
Deployment Example:
Heroku: For a Node.js application, you can use GitHub Actions to deploy to Heroku.
8. Notifications
    * Set up notifications (e.g., Slack, email) to inform the team about the status of builds, tests, and deployments.
9. Monitoring and Rollback
    * Monitoring: Implement monitoring to track application performance and errors.
    * Rollback: Define rollback procedures in case of deployment failures.








----------------------------------------------------------------------------------------
# Brief about concepts/key points:   

------------------------------------------------------------------------------------------
# Coding Snippets

## Redux toolkit code snippet

Link - https://codesandbox.io/p/sandbox/redux-toolkit-sample-hzw96y?file=%2Fsrc%2Fapp%2Fstore.js%3A9%2C1

## Theme functionality using context API

1. Create the Context:
2. Refs
3. Custom Hooks
4. State Management Libraries

```javascript
import { createContext } from 'react';

const ThemeContext = createContext();
export default ThemeContext;

```

2. Create a Provider:

```javascript
import React, { useState } from 'react';
import ThemeContext from './ThemeContext';

const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme(theme === 'light' ? 'dark' : 'light');
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

export default ThemeProvider;
```

3. Use the Context in a Component:

```javascript
import React, { useContext } from 'react';
import ThemeContext from './ThemeContext';

const ThemedComponent = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div style={{ background: theme === 'light' ? '#fff' : '#333', color: theme === 'light' ? '#000' : '#fff' }}>
      <p>The current theme is {theme}</p>
      <button onClick={toggleTheme}>Toggle Theme</button>
    </div>
  );
};

export default ThemedComponent;
```

4. Wrap Your Application with the Provider:

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import ThemeProvider from './ThemeProvider';
import App from './App';

ReactDOM.render(
  <ThemeProvider>
    <App />
  </ThemeProvider>,
  document.getElementById('root')
);
```

### [Simple Form example]()
### [Advanced form handling example]()
### [Dynamic form sample]()
### [Fetch API with promise example]()
### [Fetch API with async/await example]()

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
## 3. How do you show file upload/ task process update in react client with node server background?
Using Server-sent events.

Ref to [post](https://medium.com/@imanshurathore/server-sent-events-in-react-30021f9ffc4a)

# [React Project Development Tools]()
  * [Storybook]()
  * [Webpack]()
  * [Charts libraries]()
  * [Jest & React Testing Library]()
  * [Babel, env, prettier, linter]()

### Webpack
Webpack is a powerful module bundler primarily used for JavaScript, but it can transform front-end assets like HTML, CSS, and images if the proper plugins and loaders are included. 

In a React.js application, Webpack is often used to bundle JavaScript files and ensure that your application can be run in a browser.

It helps in managing dependencies, optimizing the code for production, and improving performance.

1. Module Bundling:
Bundles JavaScript files and other assets into single or multiple bundles for easier inclusion in your HTML.

2. Code Splitting:
Splits code into various bundles that can be loaded on demand, improving the initial load time of your application.

3. Loaders:
Transforms files into modules as they are processed. For example, Babel loader to transpile ES6+ code into ES5.

4. Plugins:
Extend Webpack's functionality. For example, HtmlWebpackPlugin generates an HTML file and injects your bundles into it.

6. Development Server:
Includes a development server that provides live reloading and hot module replacement for a better development experience.

#### Setting Up Webpack in a React.js Application
Step 1: Initialize Your Project
Step 2: Install Dependencies

```bash
mkdir react-webpack-app
cd react-webpack-app
npm init -y

Step 2: Install Dependencies

```
Step 3: Project Structure
```arduino
react-webpack-app/
│
├── src/
│   ├── index.js
│   ├── App.js
│   ├── styles.css
│
├── public/
│   └── index.html
│
├── .babelrc
├── webpack.config.js
└── package.json

```
Step 4: Configure Babel
Create a `.babelrc` file to configure Babel:

```json
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}

```
Step 5: Configure Webpack

Create a `webpack.config.js` file to configure Webpack:

```
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: 'babel-loader'
      },
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      }
    ]
  },
  plugins: [
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin({
      template: './public/index.html'
    })
  ],
  devServer: {
    contentBase: path.join(__dirname, 'dist'),
    compress: true,
    port: 9000
  },
  mode: 'development'
};
```
Step 6: Create Source Files

Create `src/index.js`:
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './styles.css';

ReactDOM.render(<App />, document.getElementById('root'));
```
Create `src/App.js`:


```javascript
import React from 'react';

const App = () => {
  return (
    <div>
      <h1>Hello, Webpack and React!</h1>
    </div>
  );
};

export default App;
```
Create s`rc/styles.css`:

```css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}
```
Create `public/index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>React Webpack App</title>
</head>
<body>
  <div id="root"></div>
</body>
</html>
```
Step 7: Add Scripts to package.json
Update `package.json` to include scripts for building and running the development server:

```json
{
  "name": "react-webpack-app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "webpack serve --open --mode development",
    "build": "webpack --mode production"
  },
  "dependencies": {
    "react": "^17.0.2",
    "react-dom": "^17.0.2"
  },
  "devDependencies": {
    "@babel/core": "^7.14.6",
    "@babel/preset-env": "^7.14.7",
    "@babel/preset-react": "^7.14.5",
    "babel-loader": "^8.2.2",
    "clean-webpack-plugin": "^4.0.0",
    "css-loader": "^6.2.0",
    "html-webpack-plugin": "^5.3.2",
    "style-loader": "^3.2.1",
    "webpack": "^5.51.1",
    "webpack-cli": "^4.8.0",
    "webpack-dev-server": "^3.11.2"
  }
}
```
Step 8: Run the Development Server
Start the development server by running:

`npm start`



## Other Frameworks]
  * [Next JS]()
  * [Vue JS]()
  * [Gatsby]()






