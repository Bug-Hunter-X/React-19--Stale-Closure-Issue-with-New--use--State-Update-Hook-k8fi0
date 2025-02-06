# React 19 Stale Closure Bug

This repository demonstrates a subtle bug that can occur in React 19 when using the new `use` syntax for state updates within functional components.  Incorrect usage can lead to stale closures, resulting in unexpected behavior and incorrect state updates.

## Bug Description
The issue arises when the update function passed to `use` does not correctly handle the current state value.  If the function directly uses the state variable, it captures the value at the time of the function's creation, not its current value.  This results in the update function always using the outdated state value.

## Solution
The correct approach is to use a functional update, passing a function to `setCount` that takes the previous state value as an argument.  This ensures the update function always works with the most recent state.

## How to Reproduce
1. Clone this repository.
2. Navigate to the project directory.
3. Run `npm install` to install dependencies.
4. Run `npm start` to start the development server.
5. Observe that clicking the increment button does not correctly increment the counter due to the stale closure.