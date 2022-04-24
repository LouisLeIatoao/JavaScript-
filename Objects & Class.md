# PLP 5

source: 
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#enumerate_the_properties_of_an_object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#enumerate_the_properties_of_an_object)
https://www.geeksforgeeks.org/function-overloading-in-javascript/

## JavaScript Object

- JavaScript does support objects
- Object name, its instances, and its functions are written as camelCase

## **Enumerate the properties of an object (standard function for all objects)**

- `[for...in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in)` loops. This method traverses all enumerable properties of an object and its prototype chain.
- `[Object.keys(o)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)`. This method returns an array with all the own (not in the prototype chain) enumerable properties' names ("keys") of an object `o`.
- `[Object.getOwnPropertyNames(o)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyNames)`. This method returns an array containing all own properties' names (enumerable or not) of an object `o`.

## **JavaScript Classes**

### Class syntax

Use the keyword `class` to create a class.

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Class</h2>

<p>How to use a JavaScript Class.</p>

<p id="demo"></p>

<script>
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}

const myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML =
myCar.name + " " + myCar.year;
</script>

</body>
</html>
```

### Class Methods

2 type of methods: constructor and normal method

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Class Method</h2>

<p>How to define and use a Class method.</p>

<p id="demo"></p>

<script>
class Car {
  // Constructor method
  constructor(name, year) {
    this.name = name;
    this.year = year;

  }
	// A method of this class
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}

let myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML =
"My car is " + myCar.age() + " years old.";
</script>

</body>
</html>
```

### Class Inheritance

- Inheritance enables you to define a class that takes all the functionality from a parent class and allows you to add more.
- Using class inheritance, a class can inherit all the methods and properties of another class.
- To create a class inheritance, use the `extends`keyword.
- **JavaScript does not support multiple inheritance**

```java
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Class Inheritance</h2>

<p>Use the "extends" keyword to inherit all methods from another class.</p>
<p>Use the "super" method to call the parent's constructor function.</p>

<p id="demo"></p>

<script>
// Base class
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

// Class model inherit class car properties 
class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

let myCar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = myCar.show();
</script>

</body>
</html>
```

## Overloading

JavaScript does NOT natively support method overloading. So, if it sees/parses two or more functions with a same names it’ll just consider the last defined function and overwrite the previous ones.

```java
function foo(arg1) {
	console.log(arg1);
}

/* The above function will be
overwritten by the function
below, and the below function
will be executed for any number
and any type of arguments */
function foo(arg1, arg2) {
	console.log(arg1, arg2);
}

// Driver code
foo("Geeks")
```

**Output:**

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e903b08d-fe86-4148-8f43-8e58800e4966/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220424%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220424T154414Z&X-Amz-Expires=86400&X-Amz-Signature=97d900f509968b29ca94b5f1760db4338e94d6e6ca21fe11a7a09257c1bf5707&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D"Untitled.png"&x-id=GetObject)

The reason for the “undefined” in the output is: In JavaScript if two functions are defined with same name then the last defined function will overwrite the former function.

So in this case the foo(arg1) was overwritten by foo(arg1,arg2), but we only passed one

Argument (“Geeks”) to the function. It means that the second argument is undefined, So when we tried to print the second argument, it is printed as “undefined”.

**The way to implement overloading in javascript**

```java
// Creating a class "foo"
class foo {

	// Creating an overloadable method/function.
	overloadableFunction() {

		// Define three overloaded functions
		var function1 = function (arg1) {
			console.log("Function1 called with"
					+ " arguments : " + arg1);
			return arg1;
		};

		var function2 = function (arg1, arg2) {
			console.log("Function2 called with"
					+ " arguments : " + arg1
					+ " and " + arg2);
			return arg1 + arg2;
		};

		var function3 = function (arg1) {
			var concatenated__arguments = " ", temp = " "

			// Concatenating all the arguments
			// and storing them into a string
			for (var i = 0; i < arg1.length; i++) {
				concatenated__arguments =
					concatenated__arguments + arg1[i]
			}

			/* Just ignore this loop and temp variable,
			we are using this loop to concatenate
			arguments with a space between them */
			for (var i = 0; i < arg1.length; i++) {
				temp = temp + " " + arg1[i]
			}

			console.log("Function3 called with this"
				+ " array as an argument : [" + temp + "]");
			console.log("Output of log is : ")

			// Returns concatenated argument string
			return concatenated__arguments;
		};

		/* Here with the help of the length of the
		arguments and the type of the argument
		passed ( in this case an Array ) we
		determine which function to be executed */
		if (arguments.length === 1
				&& Array.isArray(arguments[0])) {
			return function3(arguments[0]);
		} else if (arguments.length === 2) {
			return function2(arguments[0], arguments[1]);
		} else if (arguments.length === 1
				&& !Array.isArray(arguments[0])) {
			return function1(arguments[0]);
		}
	}
}

// Driver Code

// Instantiate an object of the "foo" class
var object = new foo();

// Call the overloaded functions using the
// function overloadableFunction(...)
// We are passing 1 argument so executes function1
console.log(object.overloadableFunction("Geeks"));

// We are passing two arguments so executes function2
console.log(object.overloadableFunction("Geeks", "for"));

// We are passing an array so executes function3
console.log(object.overloadableFunction(
				["Geeks", "for", "Geeks"]));
```

Output:

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/125d1d25-db1c-4f1c-afdd-be705968d5a0/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220424%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220424T154531Z&X-Amz-Expires=86400&X-Amz-Signature=a0d074893888639e46e0a20389558c53d548ffce0748ea46406fe6e92a22941c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D"Untitled.png"&x-id=GetObject)

**Explanation:**

In the above program, when different number of arguments are passed to the same function, then based on the number and type of arguments, the arguments will be passed to the respective function.

In this case, we have used three different functions (*function1, function2, function3*) for function Overloading.
