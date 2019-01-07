# A Vue.js Introductory Guide

> BY DAN & STEPH


----------


## Getting started with VUE.JS

### What is Vue?
Vue is a framework for creating user interfaces. It’s the V in MVC. It allows for adopters to easily use Vue for simple tasks like adding dynamic features to their app without a lot of maintenance. But can also be added to for more robust projects.

### How is it used?
Vue is simple to use for reactive interfaces and data binding. You can also use VUe for declarative rendering, nested components, and easy template logic. 

### How do I start using Vue?
You can start install using NPM (CLI) or include the <script> tag in your HTML file (CDN). For larger projects and more advanced uses, it's recommended to use vue-cli in Node.js.

### What are the most common Vue methods and how do we apply them?


``` bash
# install Vue from the command line
npm install vue-cli

# add Vue CDN to your HTML file (smaller projects)
<script src="https://unpkg.com/vue"></script>
```


----------


#### Declarative Rendering
One of the main features of Vue is it's simple-to-use render for DOM manipulation and  it reduces the lines of code you'd need to write in order to do so. Below is an example.
```
<div id="app">
  {{ message }}
</div>
```
```
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```


----------


#### Creating Objects and Data Binding
This creates new Vue objects that targets the id of the div tag. You can then data bind the keyword property.
```
const app = newVue({
    el: '#app',
    data: {
        keyword: 'Javascript'
    }
});
```
```
<div id='app'>
    {{keyword}}
</div>
```


----------


#### Conditionals in your HTML file
You can set conditionals in your HTML file directly by calling it using the v-if method.
```
<h1 v-if="isVisible == 'if'">If</h1>
<h1 v-else-if="isVisible === 'elseif'">Else If</h1>
<h1 v-else>Else</h1>
```
```
data: { isVisible: 'if' }
```


----------


#### Loops
Follow the syntax below in your JS and your HTML files to create easy loops in Vue.
```
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
```
```
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: 'Learn JavaScript' },
      { text: 'Learn Vue' },
      { text: 'Build something awesome' }
    ]
  }
})
```


----------


### Other fun stuff to do with Vue!
There are no limits to the things you can do with Vue, and we've only scratched the surface of the capabilities. Here are some other methods you can use


To let users interact with your app, we can use the v-on directive to attach event listeners that invoke methods on our Vue instances

```
<button v-on:click="reverseMessage">Reverse Message</button>
```

Vue also provides the v-model directive that makes two-way binding between form input and app state a breeze
```
<div id="app-6">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
```
```
var app6 = new Vue({
  el: '#app-6',
  data: {
    message: 'Hello Vue!'
  }
})
```

In Vue, a component is essentially a Vue instance with pre-defined options. Registering a component in Vue is straightforward
```
Vue.component('todo-item', {
  template: '<li>This is a todo</li>'
})
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
