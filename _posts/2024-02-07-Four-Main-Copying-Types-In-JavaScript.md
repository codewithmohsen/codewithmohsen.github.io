<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/default.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>
<!-- and it's easy to individually load additional languages -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/languages/go.min.js"></script>

<script>hljs.highlightAll();</script>

### Four Main Copying Types In JavaScript

JavaScript has four main copy types:

1. Copying primitives by value
2. Copying objects by reference
3. Shallow copy
4. Deep copy

#### 1. Copying primitives by value

when you assign a primitive data type (like strings, numbers, or booleans) to a variable, it's copied by value. This means the variable stores a copy of the actual value.

<pre>
<code>
let  variable1 = "Mohsen";
let variable2 = variable1; // b is now a copy of variable1
variable2 = "Sepidaar"; // Changing variable2 doesn't affect variable1
console.log(variable1); // Output: Mohsen
console.log(variable2); // Output: Sepidaar
</code>
</pre>

#### 2. Copying objects by reference

when you assign an object (including arrays and functions) to a variable, it's copied by reference. This means the variable doesn't store the actual object but rather a reference (memory address) to the object.

<pre>
<code>
let object1 = { name: "Mohsen" };
let object2 = object1; // object2 now points to the same object as object1
object2.name = "Sepidaar"; // Changing object2 affects object1
console.log(object1.name); // Output: Sepidaar
console.log(object2.name); // Output: Sepidaar
</code>
</pre>

Copying by reference means that changes made to the copied object through one variable will affect the original object and vice versa.

#### 3. Shallow copy

Shallow copy creates a new object and copies all top-level properties of the original object. However, if the properties themselves are objects, they are still referenced, not copied. One common way to shallow copy an object is using the spread operator or Object.assign().

<pre>
<code>
const object1 = { name: "Mohsen", info: { country: "Iran" } };
const object2 = { ...object1 }; // or Object.assign(object1);
object1.info.country = "Canada";
console.log(object2.info.country); // Output: Iran (since the nested object is still referenced)
</code>
</pre>

#### 4. Deep copy

Deep copy creates a new object and recursively copies all nested objects and their properties, ensuring that the copied object is entirely independent of the original one.

<pre>
<code>
function deepCopy(obj) {
    if (typeof obj !== 'object' || obj === null) {
        return obj; // Return non-object values and null as is
    }
    let copy = Array.isArray(obj) ? [] : {}; // Determine if obj is an array or object
    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            copy[key] = deepCopy(obj[key]); // Recursively copy nested objects
        }
    }
    return copy;
}
const object1 = { name: "Mohsen", info: { country: "Iran" } };
const object2 = deepCopy(object1);// or structuredClone(object1); or JSON.parse(JSON.stringify(object1));
object1.info.country = "Canada";
console.log(object2.info.country); // Output: Canada (since the nested object is deep-copied)
</code>
</pre>
