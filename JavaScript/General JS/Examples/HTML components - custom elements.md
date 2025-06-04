[MDN web docs](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements)
Also See [[HTML Hide and Display element]]
### To create and use HTML components
(custom elements), you'll define a class that extends `HTMLElement`, register it with the browser using `customElements.define()`, and then use it in your HTML like a regular element. These components can encapsulate logic and style, allowing for reusable and modular web development. 

1. Defining the Component:

- **Create a class:** Start by creating a JavaScript class that extends `HTMLElement`. This class will contain the functionality of your component.
- **Example:**
```js
    class MyComponent extends HTMLElement {
        // Component implementation goes here
        constructor() {
            super();
            // Add logic, shadow DOM, etc.
        }
    }
```

2. Registering the Component:

- Use `customElements.define()`: Register your custom element with the browser by calling `customElements.define()`. This method takes the component's name and its class as arguments.
- **Example:**
```js
    customElements.define('my-component', MyComponent);
```

3. Using the Component in HTML:

- **Add to HTML:** Once registered, you can use your component in your HTML by adding the custom element name as a tag.
- **Example:**
```html
    <my-component>
        <!-- Content that might be used by the component -->
    </my-component>
```


4. Enhancements and Features:

- **[Shadow DOM](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=748a1dba1c2e2658&sxsrf=AE3TifMDIjgU7atYCF20DjyLl5w0RMvCrQ%3A1748392851858&q=Shadow+DOM&sa=X&ved=2ahUKEwj2taP29sSNAxWUCjQIHVefJB0QxccNegQIRhAB&mstk=AUtExfB5DkRARB11ICnfjy7EcJt_5Mo0D4zFF9CVPOVsqt1YOzFBij4DJNCFYYMVaEJfhNRGX_oFONzM1Hen-zhY6FpvynWFEGkpRWRNm-233s8nNCBdMFyWgwfDva7NPw4-qdHWtz7ud4Tp3OSuaULF57RV1hCjGfLMKUNhx6QHFGpd8Mw&csui=3):**
    Use Shadow DOM to encapsulate styles and structure, preventing them from leaking into the main DOM.   

- **[Templates](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=748a1dba1c2e2658&sxsrf=AE3TifMDIjgU7atYCF20DjyLl5w0RMvCrQ%3A1748392851858&q=Templates&sa=X&ved=2ahUKEwj2taP29sSNAxWUCjQIHVefJB0QxccNegQISRAB&mstk=AUtExfB5DkRARB11ICnfjy7EcJt_5Mo0D4zFF9CVPOVsqt1YOzFBij4DJNCFYYMVaEJfhNRGX_oFONzM1Hen-zhY6FpvynWFEGkpRWRNm-233s8nNCBdMFyWgwfDva7NPw4-qdHWtz7ud4Tp3OSuaULF57RV1hCjGfLMKUNhx6QHFGpd8Mw&csui=3):**
        Use the `<template>` and `<slot>` elements to define and reuse HTML markup within your component. 
    
- **[Attributes](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=748a1dba1c2e2658&sxsrf=AE3TifMDIjgU7atYCF20DjyLl5w0RMvCrQ%3A1748392851858&q=Attributes&sa=X&ved=2ahUKEwj2taP29sSNAxWUCjQIHVefJB0QxccNegQISBAB&mstk=AUtExfB5DkRARB11ICnfjy7EcJt_5Mo0D4zFF9CVPOVsqt1YOzFBij4DJNCFYYMVaEJfhNRGX_oFONzM1Hen-zhY6FpvynWFEGkpRWRNm-233s8nNCBdMFyWgwfDva7NPw4-qdHWtz7ud4Tp3OSuaULF57RV1hCjGfLMKUNhx6QHFGpd8Mw&csui=3):**
        Custom elements can use HTML attributes to configure their behavior. 
    
- **[Slots](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=748a1dba1c2e2658&sxsrf=AE3TifMDIjgU7atYCF20DjyLl5w0RMvCrQ%3A1748392851858&q=Slots&sa=X&ved=2ahUKEwj2taP29sSNAxWUCjQIHVefJB0QxccNegQIRxAB&mstk=AUtExfB5DkRARB11ICnfjy7EcJt_5Mo0D4zFF9CVPOVsqt1YOzFBij4DJNCFYYMVaEJfhNRGX_oFONzM1Hen-zhY6FpvynWFEGkpRWRNm-233s8nNCBdMFyWgwfDva7NPw4-qdHWtz7ud4Tp3OSuaULF57RV1hCjGfLMKUNhx6QHFGpd8Mw&csui=3):**
        Allow you to insert content from the outside into your component's shadow DOM, making it more flexible. 
    
Example of a basic component:
```js
class MyComponent extends HTMLElement {
    constructor() {
        super();
        const shadow = this.attachShadow({ mode: 'open' }); // Create a shadow DOM
        shadow.innerHTML = `
            <style>
                .my-component {
                    color: blue;
                }
            </style>
            <div class="my-component">
                <p>Hello from My Component!</p>
            </div>
        `;
    }
}

customElements.define('my-component', MyComponent);
```

```html
<my-component></my-component>
```

This component will display "Hello from My Component!" with blue text, all encapsulated within its own Shadow DOM. 

This video demonstrates how to build your first Web Component:
![[Pasted image 20250528093518.png]]
![[Pasted image 20250528093327.png]]