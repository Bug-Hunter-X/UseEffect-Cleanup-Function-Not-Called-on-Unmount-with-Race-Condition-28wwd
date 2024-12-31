# React useEffect Cleanup Function Race Condition Bug

This repository demonstrates a subtle bug related to the React `useEffect` hook's cleanup function.  The issue occurs when a component unmounts before the `useEffect` function has a chance to run. In this scenario, the cleanup function might not execute, potentially leading to memory leaks or other unexpected side effects.

## Bug Description
The `bug.js` file contains a component that uses `useEffect` to log the current count and a cleanup message when the component unmounts.  However, if the component is quickly unmounted after mounting (e.g., due to navigation), the cleanup function might not be called. This is because the effect function's execution is asynchronous.

## Solution
The `bugSolution.js` demonstrates a solution to this issue using a flag to track the component's mounted status.