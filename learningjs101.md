# Learning JS 101 # 
Notes version v0.1

To learn javascript, you really should learn 3 key ideas, which will inspire 
you to learn more.

After learning how to structure HTML & CSS on a webpage (the "DOM" or document 
object model), you want to learn how to wire up the javascript to interact with it.

## Understanding Javascript (JS) ##
Javascript is a programming language that allows you to manage a sequence of 
actions on the browser (when a webpage loads), or when a user engages with 
the webpage (event activity).

It can also be used on the server-side (by Node) to run the API requests.

FOr the scope of this learning, we are considering the client (browser) side.

Javascript has 3 main concepts:
- variables: a way to track stuff
- functions: a way to organize sequence of actions into a labelled group
- events: a way to engage with the browser

### Variables ###
There are 3 types of variables:
- var: once assigned, they can be changed, and they are available anywhere in the function (even if declared further down in it)
- const: 'constants' they cannot be re-assigned once set, so use these for things that don't change. They are available from the point they are declared
- let: like 'var' but they are only available at the point they are declared, and within the nearest set of {} block they are in.

### Functions ###
Functions have a name usually, and are given inputs or parameters. Sometimes they return output, othertimes they perform the actions within themselves.

For example:
function saveUser( name, email ){
    // will be given 2 local variables 'name' and 'email' that will have whatever values were passed in

    // functions will encapsulate a set of actions done (possibly with the incoming parameters)

    // they will then have side-effects (ex. write to a file, output to the DOM),

    // and/or they will return some data
    return [ `Welcome ${name}, your email is ${email}` ]
}

## JS Interacting With DOM ##
DOM Interaction is done with events. You can add event-listeners (ex an onclick) that when it detects a click on a
DOM element, will look for accompanying javascript function code to run.

DOM reading/writing is done by using the document-object, then a query-selector to choose something inside the DOM and and finally applying methods to it to read/write it.

Simple example:
<html>
<body>
<div id='firstDiv'>This is a DIV</div>

<form>
    <input id='firstInput' value='cool'>
    <button onClick='sendForm(event)'>
</div>

Changing the HTML in the DIV is done this way:
`document.querySelector('#firstDiv').innerHTML = "New <b>HTML</b>"`

Reading the input value is done this way:
`let inputVal = document.querySelector('#firstInput').value`

Running javascript on a click of something is done by adding an 'onClick' 
attribute to it. Then you put the name of the javascript function in; in this
case we could write this:
function sendForm(event){
    // prevent click from re-submitting form
    event.preventDefault()

    let inputVal = document.querySelector('#firstInput').value
    console.log( `You entered ${inputVal} on the form` )
}

## JS Tracking Stuff & Scope ##
Everything you want to track can be assigned to a variable. There are 3 types of 
variables:
var, let, const.
var + let allow you to re-assign the variable to new values, while const does not.

They all have the scope of where they are declared. If you declare them in a 
function, that is where they are usable; if you declare them at the top of your 
script, then are globally available to all functions.

Variables can be numbers, strings, boolean, arrays ("[]") or objects ("{}").

## Asyncronous JS ##
Any functions that are not immediate in javascript are make asyncronous, such that it runs, them, but doesn't wait for a result, and keeps running the next stuff.

For example, file write operations are asyncronous (and so database calls, etc); web calls (ex. API) are asyncronous as they could take seconds to complete, timeouts are also asyncronous.

If you want to wait for an asyncronous call to complete, you must wrap all the code in a async function, ex:
`async function mainApp(){ ... code with await in here ... }`

If we want to wait for a web API call, for example:
const apiResult = await fetch( 'https://someapi.com/feed' ).then( result=>result.json() )

The above line if it called a valid API would put the JSON data into apiResult.

## API Calls ##
API calls can be one of 4 types:
- GET: e`x. a normal browser-based URL call is a GET request.
- POST: when you submit a form, it's a POST request (as you are POSTing bigger data)
- PUT/DELETE: these are like POST/GET, but for update and delete operations.


... TO BE CONTINUED ... please ask if there are topics you would like covered in particular