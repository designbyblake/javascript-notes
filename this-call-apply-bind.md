# Understanding the this keyword, call, apply, and bind

## Implicit Binding

Left of the Dot at Call Time

```JS
var me = {
	name: 'Dan',
	age: 42,
	sayName: function(){
		console.log(this.name)
	}
}

me.sayName(); // Dan


var sayNameMixin = function(obj) {
	obj.sayname = funciton() {
		console.log(this.name);
	};
};

var me = {
	name: 'Dan',
	age: 42
};

var you = {
	name: 'Amanda',
	age: 36
};

sayNameMixin(me);
sayNameMixin(you);


me.sayName(); //Dan
you.sayName(); //Amanda


var Person = function(name, age) {
	return {
		name: naem,
		age:age,
		sayName: function(){
			console.log(this.name);
		},
		mother: {
			name: 'Mom',
			sayName: function() {
				console.log(this.name);
			}
		}
	};
};

var jim = Person('Jim', 42);
jim.sayName(); //Jim
jim.mother.sayName(); // Mom
```

## Explicit Binding

```JS
var sayName = function() {
	console.log('My name is ' + this.name);
};

var stacey = {
	name: 'Stacey',
	age: 34
}

sayName.call(stacey); // Explicitly setting this to stacey

var languages = ['JavaScript', 'Ruby', 'Python']
```

```JS
var sayName = function(lang1, lang2, lang3) {
	console.log(`My name is ${this.name} and I know ${lang1}, ${lang2}, and ${lang3}`);
};

var stacey = {
	name: 'Stacey',
	age: 34
}
var languages = ['JavaScript', 'Ruby', 'Python']

sayName.call(stacey, languages[0], languages[1], languages[2]); // My name is Stacey and I know JavaScript, Ruby, and Python`
```


```JS
var sayName = function(lang1, lang2, lang3) {
	console.log(`My name is ${this.name} and I know ${lang1}, ${lang2}, and ${lang3}`);
};

var stacey = {
	name: 'Stacey',
	age: 34
}
var languages = ['JavaScript', 'Ruby', 'Python']

sayName.apply(stacey, languages); // My name is Stacey and I know JavaScript, Ruby, and Python`
// Pass in arguments as array
```

## new Binding
```JS
var sayName = function(lang1, lang2, lang3) {
	console.log(`My name is ${this.name} and I know ${lang1}, ${lang2}, and ${lang3}`);
};

var stacey = {
	name: 'Stacey',
	age: 34
}
var languages = ['JavaScript', 'Ruby', 'Python']

var newFN = sayName.bind(stacey, languages);
// Returns a new function you can call later

newFn(); // My name is Stacey and I know JavaScript, Ruby, and Python`

```
* window Binding

```JS
//new Binding
var Animal = function(color, name, type) {
	this.color = color;
	this.name = name;
	this.type = type;
};

var zebra = new Animal('black and white', 'Zorro', 'Zebra');


//window Binding
var sayAge = function() {
	console.log(this.age)
}

var me = {
	age:25
}

sayAge(); // Undefined

window.age = 43;
sayAge(); //43 will fail in Strict mode.

```