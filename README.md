# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling when dealing with user input.  Specifically, the code attempts to parse a user ID from the request parameters as an integer without verifying its validity.  This can lead to unexpected behavior or crashes if the ID is not a number.

## Bug Description
The `/users/:id` route handler does not handle the case where `req.params.id` is not a valid integer. Attempting to parse a non-numeric string with `parseInt()` will result in `NaN`, leading to the `user` variable being null.  Subsequently, the code will try to access properties of `null`, resulting in errors. 

## Solution
The solution involves adding error handling to check if `req.params.id` is a valid integer before attempting to parse it.  If it's not a valid integer, the handler should respond with an appropriate error message (e.g., 400 Bad Request).