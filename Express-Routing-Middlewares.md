# **Express REST API**
---
---

## **A.** [Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes).

## **B.** [Routing](https://expressjs.com/en/guide/routing.html).

## **C.** [Express Routing](https://www.digitalocean.com/community/tutorials/learn-to-use-the-new-router-in-expressjs-4).

---

## **A. Classes:**
#### **-Classes** are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics.

#### **Defining classes (Two way to define classes):**
    1. Class declarations:
```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```
    2. Class expressions:
        - unamed class.
        - named class.
```js
// unnamed
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// output: "Rectangle"

// named
let Rectangle = class Rectangle2 {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// output: "Rectangle2"
```
#### **Class body and method definitions:**
- **[Strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)** The body of a class is executed in strict mode, i.e., code written here is subject to stricter syntax for increased performance, some otherwise silent errors will be thrown, and certain keywords are reserved for future versions of ECMAScript.
- **Constructor** The constructor method is a special method for creating and initializing an object created with a class. There can only be one special method with the name "constructor" in a class. A SyntaxError will be thrown if the class contains more than one occurrence of a constructor method.

#### **Sub classing with extends:**
The extends keyword is used in class declarations or class expressions to create a class as a child of another class.
```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name); // call the super class constructor and pass in the name parameter
  }

  speak() {
    console.log(`${this.name} barks.`);
  }
}

let d = new Dog('Mitzie');
d.speak(); // Mitzie barks.
```

#### **Super class calls with super:**
The super keyword is used to call corresponding methods of super class. This is one advantage over prototype-based inheritance..
```js
class Cat {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Lion extends Cat {
  speak() {
    super.speak();
    console.log(`${this.name} roars.`);
  }
}

let l = new Lion('Fuzzy');
l.speak();
// Fuzzy makes a noise.
// Fuzzy roars.
```
---

## **B. Routing:**
#### **-Routing** refers to how an application’s endpoints (URIs) respond to client requests. For an introduction to routing, see Basic routing.You define routing using methods of the Express app object that correspond to HTTP methods; for example, app.get() to handle GET requests and app.post to handle POST requests. For a full list, see app.METHOD. You can also use app.all() to handle all HTTP methods and app.use() to specify middleware as the callback function (See Using middleware for details).

#### **The following code is an example of a very basic route:**
```js
const express = require('express')
const app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/', (req, res) => {
  res.send('hello world')
})
```

#### **Route methods:**
A route method is derived from one of the HTTP methods, and is attached to an instance of the express class.

The following code is an example of routes that are defined for the **GET** and the **POST** methods to the root of the app.
```js
// GET method route
app.get('/', (req, res) => {
  res.send('GET request to the homepage')
})

// POST method route
app.post('/', (req, res) => {
  res.send('POST request to the homepage')
})
```
#### **special routing method, app.all():**
There is a special routing method, app.all(), **used to load middleware** functions at a path for all HTTP request methods. **For example, the following handler is executed for requests to the route “/secret” whether using GET, POST, PUT, DELETE, or any other HTTP request method supported in the http module**.
```js
app.all('/secret', (req, res, next) => {
  console.log('Accessing the secret section ...')
  next() // pass control to the next handler
})
```

#### **Route paths:**
- Here are some examples of route paths based on string patterns.This route path will match **acd and abcd**.
```js
app.get('/ab?cd', (req, res) => {
  res.send('ab?cd')
})
```
- This route path will match abcd, **abbcd, abbbcd, and so on**.
```js
app.get('/ab+cd', (req, res) => {
  res.send('ab+cd')
})
```
- This route path will match **abcd, abxcd, abRANDOMcd, ab123cd, and so on**.
```js
app.get('/ab*cd', (req, res) => {
  res.send('ab*cd')
})
```
- This route path will match **/abe and /abcde**.
```js
app.get('/ab(cd)?e', (req, res) => {
  res.send('ab(cd)?e')
})
```
- Examples of route paths based on regular expressions:**This route path will match anything with an “a” in it**.
```js
app.get(/a/, (req, res) => {
  res.send('/a/')
})
```
- This route path will **match butterfly and dragonfly, but not butterflyman, dragonflyman, and so on**.
```js
app.get(/.*fly$/, (req, res) => {
  res.send('/.*fly$/')
})
```
#### **Route parameters:**
Route parameters are named URL segments that are used to capture the values specified at their position in the URL. The captured values are populated in the req.params object, with the name of the route parameter specified in the path as their respective keys.
```js
Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }

app.get('/users/:userId/books/:bookId', (req, res) => {
  res.send(req.params)
})

----------
//Since the hyphen (-) and the dot (.) are interpreted literally, they can be used along with route parameters for useful purposes.
Route path: /flights/:from-:to
Request URL: http://localhost:3000/flights/LAX-SFO
req.params: { "from": "LAX", "to": "SFO" }

Route path: /plantae/:genus.:species
Request URL: http://localhost:3000/plantae/Prunus.persica
req.params: { "genus": "Prunus", "species": "persica" }
```

#### **Route handlers (middleware):**
```js
// middleware Example ----->
const cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

const cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

app.get('/example/d', [cb0, cb1], (req, res, next) => {
  console.log('the response will be sent by the next function ...')
  next()
}, (req, res) => {
  res.send('Hello from D!')
})
```
---
## **C. Express Routing:**
#### **Conclusion**
#### With the inclusion of the Express 4.0 Router, we are given more flexibility than ever before in defining our routes. To recap, we can:

- Use express.Router() multiple times to define groups of routes
- Apply the express.Router() to a section of our site using app.use()
- Use route middleware to process requests
- Use route middleware to validate parameters using .param()
- Use app.route() as a shortcut to the Router to define multiple requests on a route

---
- [BACK (Main Page)](./README.md)
---