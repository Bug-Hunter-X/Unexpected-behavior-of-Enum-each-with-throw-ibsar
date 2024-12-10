# Elixir Enum.each with throw

This example demonstrates an unexpected behavior when using `throw` within `Enum.each` in Elixir. The expectation is that once an error is thrown, the iteration should immediately stop. However, the code after the `if` condition but before the `end` still gets executed before the exception is raised.

## Bug

The `bug.ex` file contains the code that produces the unexpected behavior. The `throw` statement is intended to stop the processing if the value is 3, but the "Processing..." message is printed for all values before the error is raised.

## Solution

The `bugSolution.ex` file shows the solution to this problem. It uses `Enum.reduce` which provides a cleaner and more predictable way to handle errors and short-circuit the loop.

## How to reproduce

1. Save the code in `bug.ex`
2. Run the code using `elixir bug.ex`
3. Observe that the output contains "Processing..." for all elements in the list despite the `throw` statement.

## How to fix

1. Replace `Enum.each` with `Enum.reduce` as shown in `bugSolution.ex`
2. Use the second argument to return on error and avoid unnecessary computations. 