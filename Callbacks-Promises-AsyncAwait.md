# Callbacks, Promises, Async/Await

## Callbacks
A function thtat recieves a function as an argument it is called a **Higher Order Function** and the argument passed in is a **Callback**.

```JS
function add (x,y) {
  return x + y
}

function higherOrderFunction (x, callback) {
  return callback(x, 5)
}

higherOrderFunction(10, add)
```

## Promises

Promises exist to make the complexity of making asynchronous requests more manageable.


```JS
// Create a new promise
const promise = new Promise()

// Change the status of a promise
```

### How do you change the status of a promise?
The Promise constructor function takes in a single argument, a (callback) function. This function is going to be passed two arguments, resolve and reject.

**resolve** - a function that allows you to change the status of the promise to **fulfilled**

**reject** - a function that allows you to change the status of the promise to **rejected*.

In the code below, we use setTimeout to wait 2 seconds and then invoke resolve. This will change the status of the promise to fulfilled.

```JS
function onSuccess () {
  console.log('Success!')
}

function onError () {
  console.log('💩')
}

var promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve()
  }, 2000)
})

promise2.then(onSuccess)
promise2.catch(onError)
```

```JS
import $ from "jquery";

function showError(e) {
  console.warn("Error", e);
}

function updateUI(info) {
  $("#app").text(JSON.stringify(info));
}

function getLocationURL([city, state]) {
  return `https://api.openweathermap.org/data/2.5/forecast?q=${city},${state}&APPID=7c748e66ec4489f390a888a83eb4a0f4`;
}

function getUser(id) {
  return new Promise((resolve, reject) => {
    $.getJSON({
      url: `https://api.github.com/users/${id}`,
      success: resolve,
      error: reject
    });
  });
}

function getWeather(user) {
  return new Promise((resolve, reject) => {
    $.getJSON({
      url: getLocationURL(user.location.split(",")),
      success: weather => resolve({ user, weather: weather.city }),
      error: reject
    });
  });
}

$("#btn").on("click", () => {
  getUser("designbyblake")
    .then(getWeather)
    .then(data => {
      updateUI(data);
    })
    .catch(showError);
});

// same output as above.
// JS Engine will not move to weather until user is resolved
$('#btn').on('click', async () => {

	try {
	const user = await getUser('designbyblake')
	const weather = await getWeather(user);

	updateUI({
		user,
		weather
	})
	} catch (e) {
		showErr(e)
	}
})
```

Async functions always return a promise.