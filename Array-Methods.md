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