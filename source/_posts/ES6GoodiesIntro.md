---
title: 'ES6 Goodies Intro: Destructuring Assignment'
tags: ES6
date: 2017-01-21 00:09:14
categories: JavaScript
banner:
  url: https://s19.postimg.org/bb7x25fs3/es6features.png
---

In this article series we're going to take a look to some of my favorites ES6 features

To get started: **What is ES6?**  


ES6 or ECMAScript2015 or ES2015 is not the latest version of JavaScript, currently it is the ES7 standard, but ES6 is the one that brings a lot of exciting features to JavaScript

Before ES6 was released, the latest version of a JavaScript standard was ES5 in 2009, which introduced JSON, so, you can see that there is a gap between releases of 6 years, and as you can imagine it came whit a lot of new features and new ways of doing some things, fortunately, if you are working with ES5 and want to switch to ES6, you won't feel like you're programming in a completely new language, is more like feeling that you're programming with JavaScript on steroids, and to prove that, we're going to start with a simple but powerful feature: **Destructuring Assignment**

---

some variables declarations include the keywords _const_ and _let_, these keywords are going to be explained in another post

---

## Destructuring Assignment

_Destructuring assignment_ works for Arrays and Objects, but first let's see what it is trying to accomplish  

In ES5 if you wanted to store some values of an array into variables, you have to do something like this:

```JS ES5
var someImportantValues = [1,2,3,4,5]
var firstValue = someImportantValues[0]   
var secondValue = someImportantValues[1]    
console.log(firstValue, secondValue)   //Outputs: 1 2
```

And in ES6 you could do something like this:

```JS ES6
const someImportanValues = [1,2,3,4,5];   
const [firstValue, secondValue] = someImportanValues
console.log(firstValue, secondValue)  //Outputs: 1 2
```

At first this might look weird, the first time I saw this notation I tough that it was making two copies of the object someImportanValues, but it just get the values from the array based on its positions

In objects Destructuring Assignment works based on matching keys:
```JS ES6
const object = {key: 1, value: 'some value', secondValue: 'second value'}
//Storing properties of the object into variables
const {key, value, secondValue, something} = object
console.log(key, value, secondValue, something)
//Outputs 1 'some value' 'second value' undefined
```
Note that the value of **something** is _undefined_, this is because no property name of the object match with "something", so, no value is assigned to the const "something"

You can implement this feature in multiple ways

---
### Managing multiple return values

let's say we have a function that returns an object that describes your birthday, but at some point you're going to need to handle the day, month, and year separately

```JS ES5
var getBirthDay = function () {
  var date = {day: 12, month: 12, year: 1996}
  return date
}
//Storing temporarily the day, month and year
var myBirthday = getBirthDay()
var day = myBirthday.day
var month = myBirthday.month
var year = myBirthday.
console.log(day, month, year) //Outputs 12 12 1996
```

with ES6 destructuring you can write it in a cleaner way

```JS ES6
function getBirthday () {
  const date = {day: 12, month: 12, year: 1996}
  return date
}
//Storing temporarily the day, month and year
const myBirthday = getBirthday()
const {day, month, year} = myBirthday //day = 12, month = 12, year = 1996

```

The last two lines could be avoided by writing it this way:

```JS ES6
const {day, month, year} = getBirthday()
console.log(day, month, year) //Outputs 12 12 1996
```
---
### Swaping variables values

It's a simple thing, the following code just changes the values of x to the value of y, and the value of y to the value of x

```JS ES6
let x = 4
let y = 10
[x,y] = [y,x]
console.log(x,y) //Outputs 10 4
```

---

### Getting values from parameters

This is my favorite implementation of _Destructing Assignment_ because of the use that can be given to it in _React_ and _Vue_

Before diving into React, let's look a little example:

We're going to use a function that accepts an object as a parameter, but the function only need certain properties

{% codeblock ES6 lang:js%}
function formatPostHeader ({title, author}) {
  return $`{title} written by {author}`
}

//Post Object
const post : {
  title: 'Blog post'
  body: 'Some dummy data',
  author: 'Efrain',
  category: 'Stuff'
}
//Call the function passing the post object
const header = formatPostHeader(post)
console.log(header) //Outputs 'Blog post written by Efrain'
{% endcodeblock %}

_The notation {% raw %}$`some text here {variable}`{% endraw %} is going to be covered in another post_

As we only need certain values from the object parametes, we use _destructuring assignment_ to choose what we need

And this is the implementation in React _functional stateless components_. We try to keep this type of components as simple as possible, so, you can destruct the props object that it receives.

```JS ES6 without destructuring
const Post = (props) => {
  return (
    <div>
      <h1> {props.post.title} </h1>
      <p> {props.post.body} </p>
      <h4> Written by: {props.post.author} </h4>
    </div>
  )
}
```

And we can improve it with _destructuring assignment_

```JS ES6 with destructuring
const Post = ({post}) => {
  return (
    <div>
      <h1> {post.title} </h1>
      <p> {post.body} </p>
      <h4> Written by: {post.author} </h4>
    </div>
  )
}
```

## Conclusion

**Destructing Assignment** is a simple but powerful feature, as you can see in the implementations examples, and is just the tip of the iceberg of all the goodies that ES6 brings to the JavaScript development  
