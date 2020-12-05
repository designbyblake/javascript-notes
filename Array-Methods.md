# Array Methods

## .concat
Used to merge two or more arrays. Does not mutate the original array.

```JS
const array1 = ['a','b','c'];
const array2 = ['d','e'];

const mergedArray = array1.concat(array2);

array1 // a,b,c
array2 // d,e
mergedArray // a,b,c,d,e
```

## .every
Used to determine if  evey element in array passes a test specified by a function. As soon as that function returns a flasy value, every will stop executing and return false. If no falses than it is true.

```JS
const ages = [18,21,28,34,22];

const groupCanVote = ages.every((age) => {
	return age >=18
})

const groupCanDrink = ages.every((age) => {
	return age >= 21

})

console.log(groupCanVote)  // true
console.log(groupCanDrink) // false
```

## .filter

Creates a new array after filtering out elements that don't pass a test specified by a given functioni.

```JS
const tweets = [
  { id: 1, stars: 13, text: 'Turns out "git reset --hard HEAD^" was a terrible idea.' },
  { id: 2, stars: 87, text: 'Tech conferences are too expensive.' },
  { id: 3, stars: 51, text: 'Clean code is subjective. Optimize for deletion.' },
  { id: 4, stars: 19, text: 'Maybe the real benefit of open source was the friendships we made along the way?' },
]

const popularTweets = tweets.filter((tweet) => {
  return tweet.stars > 50
})
```

## .find
Find the first element in an array which satisfieds a test specified by a given function.

```JS
const tweets = [
  { id: 1, stars: 13, text: 'Turns out "git reset --hard HEAD^" was a terrible idea.' },
  { id: 2, stars: 87, text: 'Tech conferences are too expensive.' },
  { id: 3, stars: 51, text: 'Clean code is subjective. Optimize for deletion.' },
  { id: 4, stars: 19, text: 'Maybe the real benefit of open source was the friendships we made along the way?' },
]

const tweet = tweets.find((t) => t.id === 3)

console.log(tweet) // {id: 3, stars: 51, text: "Clean code is subjective. Optimize for deletion."}
```

## .findIndex

Similar to find except it returns the index
```JS
const tweets = [
  { id: 1, stars: 13, text: 'Turns out "git reset --hard HEAD^" was a terrible idea.' },
  { id: 2, stars: 87, text: 'Tech conferences are too expensive.' },
  { id: 3, stars: 51, text: 'Clean code is subjective. Optimize for deletion.' },
  { id: 4, stars: 19, text: 'Maybe the real benefit of open source was the friendships we made along the way?' },
]

const index = tweets.findIndex((t) => t.id === 3)

console.log(index) // 2
```

## .forEach
Invokes a provided function once for each item in the array. It is similar to .map, which returns a new array.

```JS
const friends = ['Jake', 'Mikenzi', 'Jacob']

friends.forEach((friend) => addToDOM(friend))
```

## .includes
```JS
const friends = ['Jake', 'Mikenzi', 'Jacob']

friends.includes('Jake') // true
friends.includes('Karl') // false
```

## .indexOf
Returns the index of a value in the array, returns -1 if value does not exist

```JS
const friends = ['Jake', 'Mikenzi', 'Jacob']

friends.indexOf('Jake') // 0
friends.indexOf('Karl') // -1
```

## .join
Joins all elements of an array into a string and returns it.

```JS
const splitSentence = ['learn', 'react', 'at', 'ui.dev']

splitSentence.join() // learn,react,at,ui.dev
splitSentence.join(' ') // learn react at ui.dev
```

## .map
Creates a new array with the result of calling a provided function on every element in the original array.

```JS
const tweets = [
  { id: 1, stars: 13, text: 'Turns out "git reset --hard HEAD^" was a terrible idea.' },
  { id: 2, stars: 87, text: 'Tech conferences are too expensive.' },
  { id: 3, stars: 51, text: 'Clean code is subjective. Optimize for deletion.' },
  { id: 4, stars: 19, text: 'Maybe the real benefit of open source was the friendships we made along the way?' },
]

const tweetIds = tweets.map((tweet) => tweet.id) // [1,2,3,4]
```

In React, .map is used a lot along with JSX to create an unordered list.
```JS
render () {
  return (
    <ul>
      {this.state.todos.map((todo) => {
        return <li key={todo.id}>{todo.text}</li>
      })}
    </ul>
  )
}
```

## .pop
Remove the last element from an array and returns it.
```JS
const friends = ['Jake', 'Mikenzi', 'Karl']

const removedFriend = friends.pop()

console.log(removedFriend) // Karl
console.log(friends) // ['Jake', 'Mikenzi']
```

## .reduce
The idea of .reduce is that you can take an array and transform it into anything else - array, object, integer, etc.

## .reverse
Reverses the order of an array. It’s important to remember that this method mutates the original array.
```JS
const letters = ['a', 'b', 'c']
letters.reverse()

console.log(letters) // ['c', 'b', 'a']
```
The most common use case I see for .reverse is the interview question, “how do you reverse a string?”
```JS
const string = 'I like JavaScript'
const arr = string.split('') // Convert the string into an array

// Then reverse the array and join it back to a string.
arr.reverse().join('') // "tpircSavaJ ekil I"
```

## .shift
Remove the first element from an array and returns it.

## .slice
Allows you to create a new array from a portion of an existing array.
```JS
const friends = ['Jake', 'Mikenzi', 'Jordyn', 'Cash', 'Leo']
const bestFriends = friends.slice(1,4)

console.log(bestFriends) // ['Mikenzi', 'Jordyn', 'Cash']
```

## .some
Used to determine if any element in an array passes a test specified by a given function.
```JS
const ages = [6, 14, 12, 22, 13]

const hasAdultSupervision = ages.some((age) => {
  return age >= 21
})

const canRentCar = ages.some((age) => {
  return age >= 25
})

console.log(hasAdultSupervision) // true
console.log(canRentCar) // false
```

## .sort
```JS
const friends = ['Jake', 'Jacob', 'Mikenzi', 'Alex']
friends.sort()

console.log(friends) // ["Alex", "Jacob", "Jake", "Mikenzi"]

const users = [
  { name: 'Jim', age: 28 },
  { name: 'Alex', age: 32 },
  { name: 'Mikenzi', age: 26 },
  { name: 'Christina', age: 42 },
]
//To sort by the age, which is an integer, you would use the same pattern we used above, a - b.

users.sort((a,b) => a.age - b.age)
//To sort by name, you’d use a similar pattern, but instead of the minus sign, you’d use a greater than sign.

users.sort((a, b) => a.name > b.name)
//Note that .sort is mutative so each time you invoking it you’re modifying the original array.
```

## .unshift
Adds one or more elements to the beginning of an array and returns the array’s new length.
```JS

const ages = [22,27,29]

ages.unshift(20) // 4
console.log(ages) // [20,22,27,29]
//Favor using .concat or the Array spread operator instead of .shift as mutations are 👺.

const ages = [22,27,29]
const newAges = [20].concat(ages)

console.log(ages) // [22,27,29]
console.log(newAges) // [20,22,27,29]
const ages = [22,27,29]
const newAges = [20, ...ages]

console.log(ages) // [22,27,29]
console.log(newAges) // [20,22,27,29]
```

