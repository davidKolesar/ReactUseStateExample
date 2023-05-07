# ReactUseStateExample

# Example of UseState hook in a functional component:

* useState is a React Hook that lets you add a state variable to your component.
* pattern is : const [state, setState] = useState(initialState);
* The convention is to name state variables like [something, setSomething] using array destructuring.
* Parameters follow the pattern:

- initialState: The value you want the state to be initially. It can be a value of any type, but there is a special behavior for functions. This argument is ignored after the initial render.

- If you pass a function as initialState, it will be treated as an initializer function. It should be pure, should take no arguments, and should return a value of any type. React will call your initializer function when initializing the component, and store its return value as the initial state. 

-Returns : useState returns an array with exactly two values:

- The current state. During the first render, it will match the initialState you have passed.
- The set function that lets you update the state to a different value and trigger a re-render.


#NOTES on UseState Hook:
* useState is a Hook, so you can only call it at the top level of your component or your own Hooks. You can’t call it inside loops or conditions. If you need that, extract a new component and move the state into it.
* In Strict Mode, React will call your initializer function twice in order to help you find accidental impurities. This is development-only behavior and does not affect production. If your initializer function is pure (as it should be), this should not affect the behavior. The result from one of the calls will be ignored.


# App.js

//importing useState Hook
import {React, useState } from 'react' 
// just CSS (duh)
import './App.css'; 

//Declaring a functional component (with no props)
export default function App() { 

  //Initializing useState hook "counter" at initialState 0 coupled with function "setCounter"
  const [counter, setCounter] = useState(0);


   //Obvious javascript convenience functions	
   const increase = () => {
    setCounter(count => count + 1);
   };	   
	
   const decrease = () => {
	   if (counter > 0) {
		setCounter(count => count - 1);
	   }
   };	   
   
   const reset = () => {
    setCounter(0);
   };	   
	
	
  //All functional components return JSX	
  return (
	<div className="counter">
		<h1>React Counter</h1>
		<span className="counter__output">{counter}</span>
		<div classname="btn__container">
			<button className="control__btn" onClick={increase}>+</button>
			<button className="control__btn" onClick={decrease}>-</button>
			<button className="control__btn" onClick={reset}>Reset</button>
		</div>
	</div>
  );
}