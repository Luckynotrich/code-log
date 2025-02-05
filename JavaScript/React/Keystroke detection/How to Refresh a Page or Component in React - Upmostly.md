![A web browser with a component to refresh a page in React.](https://cdn.shortpixel.ai/spai/w_985+q_lossy+ret_img+to_webp/https://cdn-upmostlymulti.pressidium.com/wp-content/uploads/react-refresh-page.jpg)

In React, there are two ways to refresh a page: [updating the state](https://upmostly.com/tutorials/how-to-use-the-setstate-callback-in-react) and forcing a page reload. Let’s explore both methods of using React to refresh a page.

### Check our full video walkthrough:

## Method 1: Refresh a Page Using JavaScript

The first way of refreshing a page or component is to use vanilla JavaScript to call the **_reload_** method to tell the browser to reload the current page:

```
window.location.reload(false);
```

This method takes an optional parameter which by default is set to false. If set to true, the browser will do a complete page refresh from the server and _not_ from the cached version of the page.

Let’s take a look at how to use the **_location.reload_** method inside of a React component:

```js
import React from 'react';

function App() {
  
  function refreshPage() {
    window.location.reload(false);
  }
  
  return (
    <div>
      <button onClick={refreshPage}>Click to reload!</button>
    </div>
  );
}

export default App;
```

> React uses JavaScript at its core, therefore you can use vanilla JavaScript whenever and however you want.

The code above renders a single button that when clicked, calls the **_refreshPage_** function which triggers the **_window.location.reload_** method. We can even call the reload method inline in the onClick handler, like so:

```
<button onClick={() => window.location.reload(false)}>Click to reload!</button>
```

## Method 2: Updating the State

The second, and more appropriate method of refreshing a page in React, is to **update the state** inside of the React component.

React is a modern JavaScript library and therefore does not require a page refresh to display the latest data in the UI.

A really common example of refreshing a page when the UI needs to be updated is an e-commerce site. In a typical e-commerce site, when you add an item to a shopping cart you’re taken to another page showing you the contents of your cart.

We’re using React, not some old-school PHP e-commerce framework! Let’s build a shopping cart component to demonstrate how to refresh a page using state:

```
import React, { useState } from 'react';

function ShoppingCart() {
  const [cart, setCart] = useState([]);

  function addItemToCart(e) {
    const item = e.target.value;
    console.log(item);
    setCart([...cart, item]);
  }

  return (
    <div className="app">
      <div className="items">
        <button value="MacBook Pro" onClick={addItemToCart}> MacBook Pro</button>
        <button value="iPhone XS" onClick={addItemToCart}>iPhone XS</button>
        <button value="Gem" onClick={addItemToCart}> Gem</button>
        <button value="Teddy Bear" onClick={addItemToCart}> Teddy Bear</button>
      </div>
      <div className="cart">
        Cart
        <ul>
          {cart.map(item => <li key={item}>{item}</li>)}
        </ul>
      </div>
    </div>
  );
}

export default ShoppingCart;
```

If you drop the ShoppingCart component into a running React app, you’d see something that looks like this:

The page is refreshing each time an item gets added to the cart without the need to hard refresh the page.

Why? Because of state. If you’d like to learn more about state, check out my in-depth tutorial [Simplifying React State and the useState Hook](https://upmostly.com/tutorials/simplifying-react-state-and-the-usestate-hook).

![Avatar photo](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA5NiA5NiIgd2lkdGg9Ijk2IiBoZWlnaHQ9Ijk2IiBkYXRhLXU9Imh0dHBzJTNBJTJGJTJGY2RuLXVwbW9zdGx5bXVsdGkucHJlc3NpZGl1bS5jb20lMkZ3cC1jb250ZW50JTJGdXBsb2FkcyUyRkphbWVzLURpZXRyaWNoLVByb2ZpbGUtUGljdHVyZS1VcG1vc3RseS05Nng5Ni5wbmciIGRhdGEtdz0iOTYiIGRhdGEtaD0iOTYiIGRhdGEtYmlwPSIiPjwvc3ZnPg==)

James Dietrich is an experienced web developer, educator, and founder of Upmostly.com, a platform offering JavaScript-focused web development tutorials. He's passionate about teaching and inspiring developers, with tutorials covering both frontend and backend development. In his free time, James contributes to the open-source community and champions collaboration for the growth of the web development ecosystem.