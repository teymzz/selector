# selectorJs
The selectorJs plugin is a lightweight javascript plugin that extends the flexibility of selecting html elements. Selected elements are converted to array that can be iterated over. In this way it reduces the number of line of codes required to perform certain checks on html elements' presence or absence within the dom and keeps the code cleaner and easier to maintain.

### Initializing class
This class can be initialized easily as shown below: 

 ```js
 let selector = new Selector();
 ```

### Query selector
Html elements can be selected using the already known javascript query selectors. This selection is done through the use of ```toSelectionArray()``` method or by the use of its alias method which is the shortened ```select()``` method.

 ```js
 let selector = new Selector();

 let divs = selector.toSelectionArray('div');
 ```

 > We can do this similarly with the ```select()``` method

 ```js
 let selector = new Selector();

 let divs = selector.select('div'); //same as above
 ```

 > When items are selected, an array is usually returned which can then be processed further. The selection made above will select all the _div_ elements present on the html document. Assuming we have an html sample as below: 

 ```html
 <div id="div-one" class="item first"></div>
 <div id="div-two" class="item second"></div>
 ``` 

 > We can select all the div elements simply as shown below 

 ```js

 let selector = new Selector();

 let divs = selector.select('div');

 divs.forEach( div => {

    console.log(div.getAttribute('class')); 

 })
 ``` 

 > When an item is not found, an empty array is always returned which helps to keep our code safe from breaking. This is shown below

 ```js
 let selector = new Selector();

 let spans = selector.select('span');

 spans.forEach( span => {

    console.log(span.getAttribute('class')); 

 })
 ```

 > In the code above, because there is no span element existing in our html code, the _forEach()_ condition will never run because the returned selections will be an empty array.

### Set Element Selection Standard

When selecting an element using _document.querySelector()_ or _document.getElementById()_, the first selected item is usually being returned by default. The _selector_ plugin handles this type of selection similarly as an array which helps to maintain our code structure regardless of the element selector used. 

```js 
let selector = new Selector();

let divs = selector.select(document.querySelector('item'));

divs.forEach( div => {
    
    console.log(div.getAttribute('class')); 

})
```

> In the sample above, although, only the first item is selected, the _selector_ plugin converts this into an array that can be iterated over. This makes it possible to maintain the same code structure and reduces the number of checks or validations that may be required to be done.


### JQuery Selector 
Jquery is a javascript library that simplifies working with javascript. The _selector.js_ plugin takes advantage of this and makes it possible to convert elements selected with Jquery selector back to Javascript array format. This is shown below

```js 
let selector = new Selector;

let divs = selector.select($('.item'));

divs.forEach( div => {
    
    console.log(div.getAttribute('class')); 

})
```

> From the sample above, the parsed ```$('.item')``` will be converted back to an array format. It is important to know that when a jquery selection is supplied into the ```select()``` method, it loses its Jquery extended methods and reverts back to the native selection. This is why we used the _getAttribute()_ method rather than the Jquery _attr()_ method in the sample above. We can also see from the sample above that the code structure remains the same. This is the benefit of the _selector_ plugin in which a universal standard code structure is maintained.

The feature above is useful for developers who use Jquery and may need to find a balance between handling Jquery selections and the native Javascript selections. This is also good for Javascript plugins that may need to provide extended support for Jquery users.