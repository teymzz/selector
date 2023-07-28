# selector.js

The selector.js is a lightweight javascript plugin that extends the flexibility of selecting html elements. Selected elements are converted to array that can be iterated over. In this way it reduces the number of line of codes required to perform certain checks on elements' presence or absence within the dom and keeps the code cleaner and easier to maintain.

### Initializing class

 This class can be initialized easily as shown below: 

 ```js
 let selector = Selector;
 ```

### String selector

Strings are selected similarly to the already known javascript ```document.querySelectorAll()``` query selectors. This selection is done through the use of ```toSelectionArray()``` method or by the use of its alias method which is the shortened ```select()``` method.

 ```js
 let selector = Selector;

 let divs = selector.toSelectionArray('div');
 ```

 > We can do this similiary with the ```select()``` method

 ```js
 let selector = Selector;

 let divs = selector.select('div'); //same as above
 ```

 > When items are selected, an array is usually returned which can then be processed further. The selection made above will select all the _div_ elements present on the html document. Assuming we have an html sample as below: 

 ```html
 <div id="div-one" class="item first"></div>
 <div id="div-two" class="item second"></div>
 ``` 

 > We can select all the div element on the html element simply as shown below 

 ```js
 let selector = Selector;

 let divs = selector.select('div');

 divs.forEach( div => {

    console.log(div.attribute('class')); 

 })
 ``` 

 > The sample below will display the classes of each div item regardless of the number of div item existing in the html document. Similarly, we can also use the already known query selectors. For example, the code below is used to select the 
 div element based on their class

 ```js
 let selector = Selector;

 let items = selector.select('.item');

 items.forEach( item => {

    console.log(item.attribute('class')); 

 })
 ```  

 > When an item is not found, an empty array is always returned which helps to keep our code safe from breaking. This is shown below

 ```js
 let selector = new Selector;

 let spans = selector.select('span');

 spans.forEach( span => {

    console.log(span.attribute('class')); 

 })
 ```

 > In the code above, because there is no span element existing in our code, the _forEach()_ condition will never run because the returned selections will be an empty array.

### Single Object Selector 

When selecting an element using a _document.querySelector()_ or single selectors such as _document.getElementById()_, the first item is usually being returned by default. However, the _selector_ plugin makes handles such objects similarly as an array which helps to maintain out code structure. 

```js 
let selector = new Selector;

let divs = selector.select(document.querySelector('item'));

divs.forEach( div => {
    
    console.log(div.attribute('class')); 

})
```

> In the sample above, although, only the first item is selected, the _selector_ plugin converts this into an array that can be iterated over. This makes it possible to maintain the same code structure and reduces the number of checks or validations that may be required to be done. In a similar way, we can also handle the response of element selected using _document.getElementById()_ or even with the _document.querySelectorAll()_ .


### JQuery Object Selector 

Jquery is a javascript library that makes it easier to select items. The _selector.js_ plugin takes advantage of this and makes it possible to convert selected items back to javascript iterable items. This is shown below

```js 
let selector = new Selector;

let divs = selector.select($('item'));

divs.forEach( div => {
    
    console.log(div.getAttribute('class')); 

})
```

> Assuming we selected an element using the Jquery Library selector, the _selector.js_ helps to convert such selected items back to the native selection in which they can be easily iterated over rather than using the _Jquery.each()_ method. The code sample above shows that we used a jquery selector to select the target element _item_ . The selected object was loaded into the selector plugin which converted this items back to an array that can be iterated over. This makes it easier to keep the same code structure that was used for previous selections. It is also important to note that when the jquery selection object supplied into the selector plugin loses its Jquery extended methods and reverts back to the native selection. This is why we used the _getAttribute()_ method rather than the Jquery _attr()_ method in the sample above.

