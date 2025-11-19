# Hooks
---

- useMemo : React Hook
- The React hook useMemo is used to optimize performance by memoizing the result of an expensive computation and caching its value. This means React recalculates the memoized value only when one of the dependencies in the dependency array changes, avoiding unnecessary recalculations on every render.

How useMemo works:
It takes two arguments: a function that returns a computed value, and an array of dependencies.

React calls the provided function during the initial render and saves (memoizes) the result.

On subsequent renders, React recalculates the value only if the dependencies have changed.

If dependencies haven't changed, React returns the cached value immediately.

Why and when to use useMemo:
Use when you have an expensive or complex calculation in a component that should not run on every render unnecessarily.

Helps avoid performance bottlenecks caused by recalculating the same value multiple times.

Useful with derived data that depends on props or state, particularly if rendering happens frequently.

Also helps when passing objects or arrays as props to child components that depend on reference equality to prevent unnecessary re-renders.


```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import './App.css'
import { useMemo } from 'react'

function App() {
  const [count, setCount] = useState(0)
const[input,setInput]=useState(0);

function expensiveTask(num){
  console.log("inside expenisve task");
  for(let i=0;i<=1000000000;i++){}
  return num*2;
}

//useMemo(calculativefun,dependencies)
let value=useMemo(()=>expensiveTask(2),[input])


  return (
    <>
     <h1>use memo</h1>
     <button onClick={()=>setCount(count+1)}>inc</button>

     <div>
      COUNT:{count}
     </div>
     <div>
      DOUBLE Value:{value}
     </div>
     
     <input
     type='number'
     onChange={(e)=>setInput(e.target.value)}/>
    </>
  )
}

export default App

```
