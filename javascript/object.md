# Object

## Properties

- `Object.keys`: Creates an array containing every object property.

**Example:**
```
const person = {
    name: "John",
    age: 28,
    email: "john@email.com"
};

const keys = Object.keys(person);
console.log(keys);
// ["name", "age", "email"]
```

- `Object.values`: Creates an array containing the values from every object property.

**Example:**
```
const person = {
    name: "John",
    age: 28,
    email: "john@email.com"
};

const values = Object.values(person);
console.log(values);
// ["John", 28, "john@email.com"]
```

- `Object.entries`: Creates an array of arrays where each inner array contains both the property and the property value.
  from the object.

**Example:**
```
const person = {
    name: "John",
    age: 28,
    email: "john@email.com"
};

const values = Object.values(person);
console.log(values);
// [["name", "John"], ["age", 28], ["email", "john@email.com"]]
```
