# Hackages JavaScript Masterclass Notes
> Messy notes at the moment (WIP)!

## About the course

Koans = set of games/exercises, all by tdd

We are going to make a library.
Has a set of functions to manipulate collections.
Programming get some data make some transformation.

Dive into the tools.

```
package.json - about your modules - the manifest
project with set of other libs/dependencies
npm yarn these are the tools who will fetch the packages for your
scripts -> what can the project do? test, live, ...
coverage -> how much code is tested
docs -> will create an entire
```

## About asserts

describe = encapsulating your test
it = what it does

## About equality

types in js = Boolean, Number, String, Object, undefined

few type have the + operator
it will call toString() when trying to use the + operator
({}).toString();

check the value and the type == vs ===

## About truthyness

1 = true, 0 = false; -1=true, null=false

only a few things are false:
* 0
* ""
* undefined
* null
* false
* NaN

## About assignment

var -> it goes everywhere in the function

```
function test(value) {
// var username; //hoisting mechanism with var

    if (value) {
        var username = "Bram";
    }
    return username;

}
```

```
test(); // Bram
```

when using let = block scoped no hoisting + let is going to block you redeclare a var
test(); // ReferenceError username is undefined

const is better

it is bad practice to reassign variable because you have to remember the state
the value can be changed,
the first thing you have to write is const then switch to let when you really need it

## About prototype chain & prototypal inheritance

when you use prototype, you are saying it uses inheritance
in the console you can see `__proto__`

what is a prototype? a prototype is a blueprint, you use it when you want a certain structure and reuse it
`__proto__` -> you reach the object itself

TypeError: is not a function -> it does not find it
it goes up to the parent (chain)
when using it in a for loop it will go up in the chain
we can use hasOwnProperty to check this
sometimes you want to go on the same level

(when you log an object with inheritance it will only show it when you explicitly ask for it B.name in stead of B

every single entity will have its own version of run -> user1.run === user2.run > false
but you need only one of them
by moving it to the prototype you are improving your performance

User.prototype.run() =
everything is an object
const User = {}
User.run
function User() {}
User.run

## About this

new and `this`, by removing new it will return undefined
by default it returns undefined
the context `this`

```
const company = {
employees: [],
addEmployees: function
}
```

```
function Test(tst){
    debugger
    this.name = tst // `this` = Test // we call it with new
    function init(){
        debugger
        this.test = tst // `this` = Window // who is calling you ? // Window
    }

    init();
}
```

`this` is something that changes depending on who is calling the fuction

`this` is tied to a function, `this` is different, how do you know which `this`
looking for what is right before it, if there is nothing it is global
`this` will be the closest function,

by running with new everything that is applied to `this`, is available

maybe we need to force the `this` to be something employees
by default `this` is defined by what it is called by
you can use a call function and in that function you can decide what you want `this` to be

when you use a setTimeout then the `this` will be global Window, the context has changed

we will end up in situation where we don't have control over `this`, there are ways to fix that, we want `this` to be what we want
the api has given us techniques, what is the technique?

```
const obj = {
    employees: []
}

addEmployees.call(obj, "Davy"); // you are forcing the context of `this` to be obj
// The call() method calls a function with a given `this` value and arguments provided individually.

const product = {
    title: "",
};

const computer = Object.create(product);
computer.title = "apple";

const book = Object.create(product);
book.title = "JS is not great";

function search(term){
    if(this.title.includes === term) {
        return this; //return the object
    }

    throw;
}

search.call(computer, "apple"); // will find and return computer
search.call(book, "apple"); // undefined
search("apple"); // `this` will crash
```

the search can now be called by anyone

when you use bind, it will replace every `this` by what you give in the parameters
search = search.bind(book)

game what did you learn yesterday, 3 things that you can explain

`this` is versatile, you don't control it but you can with these functions
bind // while defining
call // while calling
apply 

https://zellwk.com/blog/this/

function think scope
var vs let vs const
var had a scope issue, you had to put all your vars on top of the file
with let and const you have block scope

```
function scope(value) { // => module
// Private API
function init() {} // by default private //scoped got this block

    // Public API
    function run() {
        init();
    }
    return {
        run; // by returning init we have made it public and visible outside
    }

}

const s = scope("value");
```

---

```
function UserModule(value) { // a function is a => module
// Private API
function init() {} // by default it is private/scoped to this block

    // Public API
    function run() {
        init();
    }
    return {
        Bank: function(){
            return {
                Online
            }
        }; // by returning init we have made it public and visible outside
    }

}

const s = UserModule.Bank("value");
```

then you had to include scripts in the correct way
with import and export ES6 its much easier

go a bit deeper in modules

## code share session

```
function User() {

}

const user = new User();

user.prototype; // will be undefined, it does not have a prototype but has __proto__

console.log(user.__proto__ === User.prototype); // true
console.log(User.prototype.__proto__ === Obeject.prototype); // true
// user is the instance


// object.create //

// in ES6

class User { // a class is actually a function // typeof
    constructor(){} // = new User()
}
```

All browsers have different js engine V8, jscore, chakra, rhino
NodeJS might we using chakra in stead off V8

js deadzone
with var no error, with let and const will crash it is safer

a function will always be hoisted, completely on the top

Js is mono threaded -> [pro1, pro2, pro3, setTimeout, ...]

spread operator ...


an arrow function does not have a this
the arrow function will capture this, it's litteraly a bind
(self = this)

object destructurin es6

arrow functions don't have arguments and this

(...args)


acc -> where it started, array of element that you want do something with
item -> next one on the loop

rest and spread operator

wallaby js

## what's next

this & prototype understanding
other things are making the code more readable

understand what is happening under the hood

not for, reduce map filter (es5)

not all the browsers support ...
we use babel to do that configuration
gives you the features today

007@hackages