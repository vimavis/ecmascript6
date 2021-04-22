# Summary of ECMAScript

## ES6 2015

- LET, CONST
```js
{
    var globalVar = 'Global var'
}

{
    let globalLet = 'Global let' // Scope local
}

console.log(globalVar)
console.log(globalLet)

const a = 'b'
a = 'c'

console.log(a)
```

- Default params
```js
function newFunction(name = 'Víctor', age = 27, country = 'Chile') {
    console.log(name, age, country)
}

newFunction()
newFunction('Vic', 15, 'CL')
```

- Literal template
```js
const phrase = `${'Hello'} ${'World!'}`
console.log(phrase)
```

- Multiline
```js
const lorem = `Lorem ipsum dolor sit amet, consectetur adipiscing elit, 
sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
Ut enim ad minim veniam, quis nostrud victor exercitation ullamco laboris 
ut aliquip ex ea commodo consequat. Duis aute irure dolor`

console.log(lorem)
```

- Destructuration
```js
const person = {
    'name': 'Vic',
    'age': 27,
    'country': 'Chile'
}

console.log(person.name, person.age, person.country)

const {name, age, country} = person

console.log(name, age, country)
```

- Spread operator
```js
const team1 = ['Victor', 'Nacho']
const team2 = ['Maria', 'Pepa', 'Flor']

const team3 = ['Percy', ...team2, ...team1]

console.log(team3)
```

- Param objects
```js
const name = 'Vic'
const age = 50

//es5
const obj1 = {name: name, age: age}

//es6
const obj2 = {name, age}

console.log(obj2)
```

- Arrow Functions
```js
const people = [
    {name: 'Vic', age: 27},
    {name: 'Juan', age: 24}
]

const listOfNames = people.map(function (person) {
    return person.name
})

const listOfNames2 = people.map(person => person.name)

console.log(listOfNames)
console.log(listOfNames2)

const square = num => num*num
console.log(square(4))
```

- Promises
```js
const helloPromise = (value) => {
    return new Promise((resolve,reject) => {
        if(value) {
            resolve('OK')
        } else {
            reject('Ups!')
        }
    })
}

helloPromise(true)
    .then(response => console.log(response))
    .then(() => console.log('Hey there'))
    .catch(error => console.log(error))

helloPromise(false)
    .then(response => console.log(response))
    .then(() => console.log('Hey there'))
    .catch(error => console.log(error))
```

- Clases
```js
class calculator {
    constructor(valA = 0, valB = 0) {
        this.valueA = valA
        this.valueB = valB
    }

    sum() {
        return this.valueA + this.valueB
    }
}

const calc = new calculator(2,4)
console.log(calc.sum())
```

- Modules
```js
import { hello } from './modulo'
hello()
```

- Generators
```js
function* helloWorld() {
    if(true){
        yield 'Hello, '
    }
    if(true) {
        yield 'World'
    }
}

const generatorHello = helloWorld()
console.log(generatorHello.next().value)
console.log(generatorHello.next().value)
console.log(generatorHello.next().value)
```

## ES7 July 2016

- Include Function
```js
const numbers = [1, 2, 3, 5, 6, 7, 8, 9]
if(numbers.includes(7)){
    console.log('I found it')
}else{
    console.log('I did not find it')
}
```

- Math
```js
const base = 4
const exponent = 3
const result = base**exponent
console.log(result)
```

## ES8 July 2017

- Object.entries
```js
const data = {
    frontend: 'Juan',
    backend: 'Victor',
    design: 'Johan'
}

const entries = Object.entries(data)
console.log(entries)
console.log(entries.length)
```

- Return Values
```js
const data = {
    frontend: 'Juan',
    backend: 'Victor',
    design: 'Johan'
}

const values = Object.values(data)
console.log(values)
console.log(values.length)
```

- Add in strings
```js
const string = 'Hello'
console.log(string.padStart(12, '_'))
console.log(string.padEnd(12, '_'))
```

- Trailing comma
```js
const comma = {
    name: 'Dan',
}
```

- Async Await
```js
const helloWorldPromise = (value) => {
    return new Promise((resolve,reject)=>{
        if(value) {
            setTimeout(() => resolve('Hello world'), 3000)
        } else {
            reject(new Error('Test error'))
        }
    })
}

const helloAsync = async (value) => {
    const hello = await helloWorldPromise(value)
    console.log('After await')
    console.log(hello)
}

helloAsync(true)
```

- Try catch
```js
const helloWorldPromise = (value) => {
    return new Promise((resolve,reject)=>{
        if(value) {
            setTimeout(() => resolve('Hello world'), 3000)
        } else {
            reject(new Error('Test error'))
        }
    })
}

const helloAsync = async (value) => {
    try {
        const hello = await helloWorldPromise(value)
        console.log(hello)
    } catch (error) {
        console.error(error)
    }
}

helloAsync(false)
```

## ES9 July 2018

- Idle Operators
```js
const obj = {
    name: 'Victor',
    age: 27,
    country: 'Chile'
}

const {country, ...all }  = obj
console.log(all)
```

- Concatenate items in objects
```js
const obj = {
    name: 'Victor',
    age: 27
}

const obj2 = {
    ...obj,
    country: 'Chile'
}

console.log(obj2)

const obj3 = {
    ...obj2,
    name: 'Juan'
}

console.log(obj3)
```

- Promise.finally
```js
const helloWorldPromise = (value) => {
    return new Promise((resolve,reject)=>{
        if(value) {
            setTimeout(() => resolve('Hello world'), 3000)
        } else {
            reject(new Error('Test error'))
        }
    })
}

helloWorldPromise(true)
    .then(response => console.log(response))
    .catch(error => console.log(error))
    .finally(() => console.log('ended'))
```

- Regex
```js
const regexData = /([0-9]{4})-([0-9]{2})-([0-9]{2})/
const match = regexData.exec('2020-04-20')
const year = match[1]
const month = match[2]
const day = match[3]
console.log(year,month,day)
```

## ES10 July 2019

- flat
```js
const array = [1,2,3, [4,5,6, [4,9,0]]]
console.log(array.flat()) // default value is 1
console.log(array.flat(2))

const array2 = [1,2,3,4,5]
console.log(array2.flatMap(value => [value,value*2]))
```

- trim start/end
```js
const hello = '            hello world     '
console.log(hello.trimStart())
console.log(hello.trimEnd())
console.log(hello.trim())
```

- try catch
```js
try{

} catch(error) {
    console.log(error)
}

// is same

try{

} catch {
    console.log(error)
}
```

- key value to object
```js
const entries = [
    ['name', 'Victor'], ['age', 27]
]

console.log(Object.fromEntries(entries))
```

- Description in symbol objects
```js
const mySymbol = `My symbol`
const symbol = Symbol(mySymbol)
console.log(symbol.description)
```
