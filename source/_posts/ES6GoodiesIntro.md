---
title: 'ES6 Goodies Intro: Destructing Assignment'
tags: ES6
date: 2017-01-21 00:09:14
categories: JavaScript
banner:
  url: https://s19.postimg.org/bb7x25fs3/es6features.png
---

In this article series we're going to take a look to some of my favorites ES6 features

To get started: **What is ES6?**  


ES6 or ECMAScript2015 or ES2015 is not the latest version of JavaScript, currently it is the ES7 standard, but ES6 is the one that brings a lot of exciting features to JavaScript

Before ES6 was released, the latest version of a JavaScript standard was ES5 in 2009, which introduced JSON, so, you can realize that there is a gap between releases of 6 years, and as you can imagine it came whit a lot of new features and new ways of doing some things, fortunately, if you are working with ES5 and want to do the switch to ES6, you won't feel like you're programming in a completely new language, is more like feeling that you're developing with JavaScript on steroids, and to prove that, we're going to start with a simple but powerful feature: **Destructing Assignment**

## Destructuring Assignment

Destructuring assignment works for Arrays and Objects, but first let's see what it tries to accomplish  

In ES5 if you wanted to store some values of an array into variables, you have to make something like this:

```JS
var someImportantValues = [1,2,3,4,5];

var firstValue = someImportantValues[0];
var secondValue = someImportantValues[1];

console.log(firstValue, secondValue); //Outputs: 1 2
```
