# react-js-development


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









