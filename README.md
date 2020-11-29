# Notes from JavaScript Course

## Variables

- A variable declaration introduces a new identitfier. By default it is undefined.
- Variable initialization is when it is first assigned a value
- Variables have scope, either global scope or funcion scope.
- var is function scoped
- let is block scoped
- const is also  block scoped, and it is immutable.
- If an object is set to const, you can't change the value of the const but the object itself can be updated.

## Object and Array Destructuring

Destructuring allows us to extract multiple properties from an object
```JS
//Old
const name = user.name;
const handle = user.handle;
const location = user.location;


// With Destructuring
const { name, handle, location } = user;
```

Destructuring allows the results of invocations
```JS
function getUser () {
  return {
    name: 'Tyler McGinnis',
    handle: '@tylermcginnis',
    location: 'Eden, Utah'
  };
}

const { name, handle, location } = getUser();
```

Arrays can also be destructured
```JS
var user = ['Dan Blake', '@designbyblake', 'Baltimore, MD'];

var [name, handle, location ] = user;

console.log(handle); // @designbyblake
console.log(location); // Baltimore, MD


var csv = '2019, Chevy, Colorado, My car';
var [ year, make, model, description ] = csv.split(',');

console.log(make); // Chevvy
console.log(model); //Colorado
```

Destructure and rename at the same time.
```JS
var user = {
	n: 'Dan Blake',
	h: '@designbyblake',
	l: 'Baltimore, MD'
};

var {n: name, h: handle, l: location } = user;

console.log(handle);// @designbyblake
```

Destructuing of function parameters
```JS
// value after the equal is the default value
function fetchRepos({language='All', minStars=0, maxStars='', createdBefore='', createdAfter=''}){

}

fetchRepos({
	language: 'JavaScript',
	createdBefore: new Date('01/01/2017').getTime(),
	minStars:100
});
```


## Computed Propery Names
```JS
// Old

function objectify (key, value) {
	let obj = {};
	obj[key] = value;
	return obj
}

// New
function objectify (key, value) [
	return {
		[key] value
	}
}
```

## Template Literals

Use the backtick to allow multiline strings as well as use variables in the string with *${variable}
```JS
function welcomeMsg(fName, lName, email) {
	return `
		<h1>Hello, ${fName} ${lName}.</h1>
		<p>The email you used to sign up is "${email}"</p>
	`;
}
```

## Arrow Functions

Arrow functions do NOT create a new context allowing the use of the this keyword inside an arrow function with this being scoped outside the function
```JS
 // Function declaration
 function add(x,y) {
	 return x + y;
 }

// Function expression
var add = function(x,y) {
	return x + y;
}

var add = (x,y) => {
	return x + y;
}


function getTweets (uid) {
  return fetch('https://api.users.com/' + uid)
    .then(function (response) {
      return response.json()
    })
    .then(function (response) {
      return response.data
    }).then(function (tweets) {
      return tweets.filter(function (tweet) {
        return tweet.stars > 50
      })
    }).then(function (tweets) {
      return tweets.filter(function (tweet) {
        return tweet.rts > 50
      })
    })
}

function getTweets(uid) {
	return fetch('https://api.users.com/' + uid)
		.then(response => response.json())
		.then(reponse => response.data)
		.then(tweet => tweets.filter(tweet => tweet.stars >  50))
		.then(tweets) => tweets.filter(tweet=>  tweet.rts > 50))
	}
```

## Default Parameters

```JS
// ES5 way
function calculatePayment (price, salesTax, discount) {
	salesTax = typeof salesTax === 'undfined' ? 0.047 : salesTax;
	discount = typeof discount === 'undfined' ? 0 : discount;
}

// Make sure a parameter is passed, basically provied a nice error message
function isRequired (name) {
	throw new Error(name + 'is required')
}

// With default parameters
function caclulatePayment (price = isRequired('price'), salesTax = 0.047, discount = 0) {

}
```

## Compiling vs Polyfills with Babel
