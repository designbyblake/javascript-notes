# Objects & Classes

## Object.create
Object.create allows you to create an object which will delegate to another object on failed lookups.

```JS
const parent = {
	name: 'Dave',
	age: 65,
	heritage: 'Human'
}

const child = Object.create(parent)
child.name = 'Frank'
child.age = 21

console.log(child.name) // Frank
console.log(child.age) // 21
console.log(child.heritage) // Human, gets value from parent since blank
```

## Functional Instantiation
```JS
function Animal (name, energy) {
  let animal = {}
  animal.name = name
  animal.energy = energy

  animal.eat = function (amount) {
    console.log(`${this.name} is eating.`)
    this.energy += amount
  }

  animal.sleep = function (length) {
    console.log(`${this.name} is sleeping.`)
    this.energy += length
  }

  animal.play = function (length) {
    console.log(`${this.name} is playing.`)
    this.energy -= length
  }

  return animal
}

const leo = Animal('Leo', 7)
const snoop = Animal('Snoop', 10)
```

## Functional Instantiation With Shared Methods
Anytime a new method is added to animalMethods it must also be added to the animal function
```JS
const animalMethods = {
  eat(amount) {
    console.log(`${this.name} is eating.`)
    this.energy += amount
  },
  sleep(length) {
    console.log(`${this.name} is sleeping.`)
    this.energy += length
  },
  play(length) {
    console.log(`${this.name} is playing.`)
    this.energy -= length
  }
}

function Animal (name, energy) {
  let animal = {}
  animal.name = name
  animal.energy = energy
  animal.eat = animalMethods.eat
  animal.sleep = animalMethods.sleep
  animal.play = animalMethods.play

  return animal
}

const leo = Animal('Leo', 7)
const snoop = Animal('Snoop', 10)
```

## Functional Instantiation with Shared Methods and Object.create
Anytime a new method is added to animalMethods it is available to the Animal function since animal is using Object.create and referencing animalMethods.
```JS
const animalMethods = {
  eat(amount) {
    console.log(`${this.name} is eating.`)
    this.energy += amount
  },
  sleep(length) {
    console.log(`${this.name} is sleeping.`)
    this.energy += length
  },
  play(length) {
    console.log(`${this.name} is playing.`)
    this.energy -= length
  }
}

function Animal (name, energy) {
  let animal = Object.create(animalMethods)
  animal.name = name
  animal.energy = energy

  return animal
}

const leo = Animal('Leo', 7)
const snoop = Animal('Snoop', 10)

leo.eat(10)
snoop.play(5)
```


## Prototype
A Prototype is a property that points to an object

### Prototype Instantiaion

```JS
function Animal (name, energy) {
  let animal = Object.create(Animal.prototype)
  animal.name = name
  animal.energy = energy

  return animal
}

Animal.prototype.eat = function (amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

Animal.prototype.sleep = function (length) {
  console.log(`${this.name} is sleeping.`)
  this.energy += length
}

Animal.prototype.play = function (length) {
  console.log(`${this.name} is playing.`)
  this.energy -= length
}

const leo = Animal('Leo', 7)
const snoop = Animal('Snoop', 10)

leo.eat(10)
snoop.play(5)
```

When ever you use the new keyword infront of the funciton invocation JavaScript creates a new Ojbect and returns it to you.

```JS
function Animal (name, energy) {
  //let animal = Object.create(Animal.prototype)
  this.name = name
  this.energy = energy

  //return animal
}

Animal.prototype.eat = function (amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

Animal.prototype.sleep = function (length) {
  console.log(`${this.name} is sleeping.`)
  this.energy += length
}

Animal.prototype.play = function (length) {
  console.log(`${this.name} is playing.`)
  this.energy -= length
}

const leo = new Animal('Leo', 7)
const snoop = new Animal('Snoop', 10)

leo.eat(10)
snoop.play(5)
```

## Classes
JavaScript included classes with ES6


```JS
class Animal {
	constructor(name, energy) {
		this.name = name
		this.energy = energy
	}

	eat(amount) {
		console.log(`${this.name} is eating.`)
		this.energy += amount
	}

	sleep(length) {
		console.log(`${this.name} is sleeping.`)
		this.energy += length
	}

	play(length) {
		console.log(`${this.name} is playing.`)
		this.energy -= length
	}
}

const leo = new Animal('Leo', 7)
const snoop = new Animal('Snoop', 10)

leo.hasOwnProperty('name') // true
leo.hasOwnProperty('sleep') // false
leo instanceof Animal // true
```

## More on Prototype
To see what methods are available on an object.
```JS
const testArray = []

const testArrayPrototype = Object.getPrototypeOf(testArray)


```