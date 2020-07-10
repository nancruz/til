# How to extend JS Error to create custom errors

Below is the "pseudocode" for the built-in Error class defined by JavaScript itself.

```js
class Error {
  constructor(message) {
    this.message = message;
    this.name = "Error"; // (different names for different built-in error classes)
    this.stack = <call stack>; // non-standard, but most environments support it
  }
}
```

To create a custom error we need to extend that implementation.

```js
class MyCustomError extends Error {
    constructor(message) {
        super(message);
        this.name = "MyCustomError";
    }
}
```

When handling exceptions, the error types can be checked using `instanceof`.

```js
try {
    ...
} catch (e) {
    if (e instanceof MyCustomError) {
        // Handle the MyCustomError
    } else {
        // Handles other possible error
    }
}
```