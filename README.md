# TypeScript Closure Issue with setTimeout in Loop

This repository demonstrates an uncommon bug in TypeScript related to closures and the use of `setTimeout` within a loop.  The problem arises when the loop variable is captured by the closure of the `setTimeout` callback. Because of JavaScript's asynchronous nature and how closures work, the final value of `i` is used in each of the `setTimeout` callbacks rather than the value of `i` when the callback was scheduled. This leads to unexpected behavior.

## Problem Description
The `printNumbers2` function attempts to print numbers 1 to n using `setTimeout` for each iteration. However, due to the asynchronous nature of `setTimeout`, by the time each callback function executes, the loop has already completed, and `i` holds the final value (n+1).  Therefore, instead of printing 1, 2, 3, 4, 5, it prints 6 five times.

## Solution
The solution involves using an immediately invoked function expression (IIFE) or `let` within the loop to create a new scope for `i` for each iteration.  This ensures each callback function captures its own value of `i`. 

## How to Run
1. Clone this repository.
2. Make sure you have Node.js and npm installed.
3. Navigate to the repository directory.
4. Run `tsc` to compile the TypeScript files.
5. Run `node bug.js` and `node bugSolution.js` to see the problematic behavior and the corrected output, respectively.