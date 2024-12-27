# React setInterval Memory Leak Bug

This repository demonstrates a common bug in React applications: memory leaks caused by the improper use of `setInterval` within the `useEffect` hook.  The `bug.js` file shows the problematic code, while `bugSolution.js` provides the corrected implementation.

The bug arises from failing to clear the interval using `clearInterval` before the component unmounts. This leads to an interval continuing to run indefinitely, consuming resources and potentially causing memory leaks. 

## How to Reproduce

1. Clone the repository.
2. Open `bug.js` to see the buggy code. Note that the console might not show immediate errors, but running this component in a browser and checking developer tools will show multiple setInterval entries. 
3. Open `bugSolution.js` to see the corrected version with cleanup.

## Solution

The solution is simple: use the return value of `useEffect` to provide a cleanup function that calls `clearInterval` before the component is unmounted.  This ensures that the interval is stopped properly, preventing memory leaks. 