Source:

1. [https://www.w3schools.com/js/js_functions.asp](https://www.w3schools.com/js/js_functions.asp)
2. [https://www.javascripttutorial.net/javascript-pass-by-value/#:~:text=In JavaScript%2C all function arguments,variables outside of the function](https://www.javascripttutorial.net/javascript-pass-by-value/#:~:text=In%20JavaScript%2C%20all%20function%20arguments,variables%20outside%20of%20the%20function).

# JavaScript Different types of loop

## 1. For loop

`for` - loops through a block of code a number of times

```jsx
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript For Loop</h2>

<p id="demo"></p>

<script>
let text = "";

for (let i = 0; i < 5; i++) {
  text += "The number is " + i + "<br>";
}

document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

## 2. For in

```jsx
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript For In Loop</h2>
<p>The for in statement loops through the properties of an object:</p>

<p id="demo"></p>

<script>
const person = {fname:"John", lname:"Doe", age:25}; 

let txt = "";
for (let x in person) {
  txt += person[x] + " ";
}
// Output: John Doe 25

document.getElementById("demo").innerHTML = txt;
</script>

</body>
</html>
```

Code example explained:

- The **for in** loop iterates over a **person** object
- Each iteration returns a **key** (x)
- The key is used to access the **value** of the key
- The value of the key is **person[x]**

## 3. While loop

The `while` loop loops through a block of code as long as a specified condition is true.

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript While Loop</h2>

<p id="demo"></p>

<script>
let text = "";
let i = 0;
while (i < 10) {
  text += "<br>The number is " + i;
  i++;
}
document.getElementById("demo").innerHTML = text;
</script>

</body>
```

## 4. The Do While loop

The `do while` loop is a variant of the while loop. This loop will execute the code block once, before checking if the condition is true, then it will repeat the loop as long as the condition is true.

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Do While Loop</h2>

<p id="demo"></p>

<script>
let text = ""
let i = 0;

do {
  text += "<br>The number is " + i;
  i++;
}
while (i < 10);  

document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>

```

# JavaScript function

A JavaScript function is a block of code designed to perform a particular task.

**Syntax:**

- A JavaScript function is defined with the `function` keyword, followed by a **name**, followed by parentheses **()**.
- Function names can contain letters, digits, underscores, and dollar signs (same rules as variables).
- The parentheses may include parameter names separated by commas:**(*parameter1, parameter2, ...*)**
- Javascript is dynamically typed language. Hence, passing different parameters in different types in a function is allowed.
- The code to be executed, by the function, is placed inside curly brackets: **{}**

```java
// a function that takes in two numbers, multiplies them, and returns the output
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
var x = myFunction(4, 3);
document.getElementById("demo").innerHTML = x;

function myFunction(a, b) {
  return a * b;
}
</script>

</body>
</html>
```

**JavaScript does support recursive function**

```java
// A recursive function that calculate the sum of natural numbers from 1 to n
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
let x = sum(4);
document.getElementById("demo").innerHTML = x;

function sum(n) {
  if (n <= 1) {
    return n;
  }
  return n + sum(n - 1);
}
</script>

</body>
</html>
```

**Return value**

- JavaScript doesn’t support functions that return multiple values. However, you can wrap multiple values into an array or an object and return the array or the object.
- Use destructuring assignment syntax to unpack values from the array, or properties from objects.

Returning multiple values from a function using an array

```java

<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
let names = getNames();
document.getElementById("demo").innerHTML = names;

function getNames() {
    // get names from the database or API
    let firstName = 'John',
        lastName = 'Doe';

    // return as an array
    return [firstName, lastName];
}
</script>

</body>
</html>
```

Returning multiple values from an function using an object

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
let names = getNames();
let firstName = names.firstName,
    lastName  = names.lastName;
document.getElementById("demo").innerHTML = firstName +" "+ lastName;

function getNames() {
  // get names from the database or API
  let firstName = 'John',
      lastName = 'Doe';

  // return values
  return {
    'firstName': firstName,
    'lastName': lastName
  };
}
</script>

</body>
</html>
```

# **JavaScript pass-by-value**

- In JavaScript, all function arguments are always passed by value. It means that JavaScript copies the values of the function into the function arguments.
- Any changes that you make to the arguments inside the function do not reflect the passing variables outside of the function.

**Pass-by-value of primitives values**

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
let y = 10;
let result = square(y);
document.getElementById("demo").innerHTML = "y = "+y +"<br />"+ "result = "+result;

function square(x) {
    x = x * x;
    return x;
}

</script>

</body>
</html>
```

**Pass-by-value of reference values**

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
let person = {
  name: 'John',
  age: 25,
};
let x = increaseAge(person);

document.getElementById("demo").innerHTML = "person age: "+person.age +"<br />"+ "x = "+x;

function increaseAge(obj) {
  obj.age += 1;
	return obj.age;
}

</script>

</body>
</html>
```

It seems that JavaScript passes an object by reference because the change to the object is reflected outside the function. However, this is not the case.

In fact, when passing an object to a function, you are passing the reference of that object, not the actual object. Therefore, the function can modify the properties of the object via its reference.

However, you cannot change the reference passed into the function. For example:
```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p>This example calls a function which performs a calculation 
and returns the result:</p>

<p id="demo"></p>

<script>
let person = {
  name: 'John',
  age: 25,
};
increaseAge(person);

document.getElementById("demo").innerHTML = "person age: "+person.age;

function increaseAge(obj) {
  obj.age += 1;

  // reference another object
  obj = { name: 'Jane', age: 22 };

}

</script>

</body>
</html>
```
