Baseline

Widely available

The **`formdata`** event fires after the entry list representing the form's data is constructed. This happens when the form is submitted, but can also be triggered by the invocation of a [`FormData()`](https://developer.mozilla.org/en-US/docs/Web/API/FormData/FormData "FormData()") constructor.

This event is not cancelable and does not bubble.

## [Syntax](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#syntax)

Use the event name in methods like [`addEventListener()`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener "addEventListener()"), or set an event handler property.

```js

addEventListener("formdata", (event) => { })

onformdata = (event) => { }

```

## [Event type](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#event_type)

## [Event properties](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#event_properties)

_Inherits properties from its parent interface, [`Event`](https://developer.mozilla.org/en-US/docs/Web/API/Event)._

[`FormDataEvent.formData`](https://developer.mozilla.org/en-US/docs/Web/API/FormDataEvent/formData)

Contains the [`FormData`](https://developer.mozilla.org/en-US/docs/Web/API/FormData) object representing the data contained in the form when the event was fired.

## [Examples](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#examples)

```js
// grab reference to form
const formElem = document.querySelector("form");

// submit handler
formElem.addEventListener("submit", (e) => {
  // on form submission, prevent default
  e.preventDefault();

  console.log(formElem.querySelector('input[name="field1"]')); // FOO
  console.log(formElem.querySelector('input[name="field2"]')); // BAR

  // construct a FormData object, which fires the formdata event
  const formData = new FormData(formElem);
  // formdata gets modified by the formdata event
  console.log(formData.get("field1")); // foo
  console.log(formData.get("field2")); // bar
});

// formdata handler to retrieve data

formElem.addEventListener("formdata", (e) => {
  console.log("formdata fired");

  // modifies the form data
  const formData = e.formData;
  // formdata gets modified by the formdata event
  formData.set("field1", formData.get("field1").toLowerCase());
  formData.set("field2", formData.get("field2").toLowerCase());
});
```

The `onformdata` version would look like this:

```
formElem.onformdata = (e) => {
  console.log("formdata fired");

  // modifies the form data
  const formData = e.formData;
  formData.set("field1", formData.get("field1").toLowerCase());
  formData.set("field2", formData.get("field2").toLowerCase());
};
```

## [Specifications](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#specifications)

| Specification |
| --- |
| [HTML  
\# event-formdata](https://html.spec.whatwg.org/multipage/indices.html#event-formdata) |

## [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#browser_compatibility)

## [See also](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFormElement/formdata_event#see_also)