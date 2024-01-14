[[Adv. Front-End Programming]]

## [[Chapter 1 - Introduction]]
---

## What's MERN?

It's a combination of technologies (aka a stack) that provides interactivity through the [[Single Page Application]] (SPA) paradigm

The inception of these technologies sparked the rise of more robust front-end frameworks such as Angular.js

Most of these front-end networks are built upon the [[Model View Controller {MVC}]] (MVC) design pattern

## MERN Components

### React

The defining component of the stack
Isn't a framework but a library (doesn't follow the MVC paradigm, only V exists but how to tie it to the back end is up to the programmer)

It was originally built by Facebook to manage how ads were displayed and since Facebook originally had a more MVC paradigm, any changes or updates needed the use of the rest of the MVC

So they just made a library that made the templates of their pages change themselves instead of replicating code

React was built to use declarative programming ([[Imperative vs declarative programming]])

#### Declarative

React makes it easier for programmers to not worry about any changes made to the front-end messing up the database 

A component in React will automatically determine how a view will look like based on the data that was provided

Traditionally, you would have to do some DOM manipulation of your own but React circumvents this by using virtual DOM technology

#### Component-based

Everything that you ever do in React is building components, which are blocks of code that maintains and renders itself

Components represents the state of the data (from your database) and how it's represented/rendered (view)

You can combine components together to make another larger component that would depict a complete page, which makes writing web applications easier because everything is being broken down into smaller steps

Components communicate with each other by outputting read-only statuses to their **children** or callbacks to their **parents**

#### No Templates

React automates repetitive DOM elements by using JavaScript, thus nulling the need for templates like in more traditional web apps

React uses a markup language similar to HTML called **JSX** (short for JavaScipt XML) which developers use to represent a Virtual DOM

It's pretty simple to learn like HTML

#### Isomorphic

**Isomorphic**: when the application uses the same rendering engine on the server and the client 

This means that the same code can be run on the browser and the server which makes things like SEO easier

### Node.js

Allows for the ability to run JS outside of a browser using Chrome's V8 JS engine

The Node.js runtime is similar to how the Java runtime works and creates a more robust way to do back end in JS

#### Node.js Modules

You can run and put together multiple JS files which you couldn't previously do before without tat least one HTML file

JS files can now communicate with each other using node.js modules without the need for an HTML page

Modules are like libraries and can be included in other JS files using the ``require`` keyword

There are pre-written modules which help access things such as the file system, network, and i/o

#### Node.js and npm

npm is the default package manager and allows the installation of many user uploaded open source js libraries such as jQuery and React

### Express

This is a framework that simplifies the act of writing server code

Express uses routes that tell the web app what to do when a certain HTTP request is made

You can also write middleware for your database which helps create functionality such as logging and authentication

### MongoDB

This is the database that the MERN stack uses as is a *NoSQL document oriented* database