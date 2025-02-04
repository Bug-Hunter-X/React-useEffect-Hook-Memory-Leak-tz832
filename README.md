# React useEffect Hook Memory Leak

This example demonstrates a common mistake with the React `useEffect` hook: forgetting the cleanup function (return statement).  The code logs a message when the component mounts, but it never unmounts, which can cause memory leaks if resources are being used within the effect.

## Problem

The `useEffect` hook in `bug.js` is missing the `return` statement, which is critical for cleaning up any side effects (like subscriptions or timers) when the component unmounts.  Without the cleanup, the `console.log` continues to be called even after the component is removed from the DOM.

## Solution

The `bugSolution.js` file provides the corrected code. By adding a `return` statement that returns a cleanup function, resources allocated in the `useEffect` are released when the component unmounts, preventing memory leaks.