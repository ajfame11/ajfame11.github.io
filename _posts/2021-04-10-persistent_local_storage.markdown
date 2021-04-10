---
layout: post
title:      "Persistent Local Storage"
date:       2021-04-10 23:07:06 +0000
permalink:  persistent_local_storage
---


For my final project for the Flatiron School, I decided to create a simple game blog app. I will add extra functionality over time but for it allows the user to submit a post along with a title, description, and image of their choosing. There is a list of posts by images that can deleted or read through the show page.

For this project, we were instructed to use React, Redux, and React - Redux for the frontend of the project. React is an open-sourced Javascript library for building user interfaces. Redux is an open-sourced Javascript for managing application state. React Redux is a binding layer of react for redux, it allows react components to read data from redux store and dispatch actions to the store to update state.

During the building of my react application, one issue that I was running into was my site breaking after I would refresh the page after every other action. I learned that after some actions took place, the state of my objects was lost or forgotton by react. So I had to make use of 'localStorage'. 'localStorage' is a property that allows JavaScript based websites/applications to save key - value pairs in a web browser with no expiration date. To use localStorage, there are five methods to choose from:

<ol>
<li><code class=" prettyprinted" style=""><span class="pln">setItem</span><span class="pun">()</span></code>: Add key and value to <code class=" prettyprinted" style=""><span class="pln">localStorage</span></code></li>

<li><code class=" prettyprinted" style=""><span class="pln">getItem</span><span class="pun">()</span></code>: This is how you get items from <code class=" prettyprinted" style=""><span class="pln">localStorage</span></code></li>

<li><code class=" prettyprinted" style=""><span class="pln">removeItem</span><span class="pun">()</span></code>: Remove an item by key from <code class=" prettyprinted" style=""><span class="pln">localStorage</span></code></li>

<li><code class=" prettyprinted" style=""><span class="pln">clear</span><span class="pun">()</span></code>: Clear all <code class=" prettyprinted" style=""><span class="pln">localStorage</span></code></li>

<li><code class=" prettyprinted" style=""><span class="pln">key</span><span class="pun">()</span></code>: Passed a number to retrieve the key of a <code class=" prettyprinted" style=""><span class="pln">localStorage</span></code></li>
</ol>

I utilized two of the five methods listed above:<br/><br/>


**setItem()**: To store values in localStorage

This method allows you to store values in the localStorage object.

It takes two parameters: a key and a value. The key can be referenced later to fetch the value attached to it.

```
const GameCard = (props) => {
    const game = props.game
    const dispatch = useDispatch()
    const history = useHistory()
    const handleClick = () => {
        dispatch ({ type: 'SELECT_GAME', payload: game})
        localStorage.setItem("selectedItem", game.id)
        history.push('/GameDetails')
    }
```
<br/><br/>

**getItem()**: To get items from localStorage

To get items from localStorage, use the getItem() method. 

GetItem() allows you to access the data stored in the browser’s localStorage object.

getItem() accepts only one parameter, which is the key, and returns the value as a string.

To do this, we make use of the JSON.parse() method, which converts a JSON string into a JavaScript object.

```
if(localStorage.getItem("selectedItem")!=undefined){
      fetch("http://localhost:4000/games/"+localStorage.getItem("selectedItem"))
        .then(res => res.json())
        .then(res => {
          dispatch ({ type: 'SELECT_GAME', payload: res})
        })
```
<br/><br/>


Below here are the methods I did not need to use:<br/><br/>


**removeItem()**: To delete localStorage sessions

To delete local storage sessions, use the removeItem() method.

When passed a key name, the removeItem() method removes that key from the storage if it exists.

localStorage.removeItem('key-name');<br/><br/>



**clear()**: To delete all items in localStorage

Use the clear() method to delete all items in localStorage.

This method clears the entire storage of all records for that domain. It does not receive any parameters.

localStorage.clear();<br/><br/>



**key()**: To get the name of a key in localStorage

The key() method comes in where you need to loop through keys and allows you to pass a number or index to localStorage to retrieve the name of the key.

var KeyName = localStorage.key(index);
