The **`History`** interface of the [History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API) allows manipulation of the browser _session history_, that is the pages visited in the tab or frame that the current page is loaded in.

There is only one instance of `history` (It is a _singleton_.) accessible via the global object [`history`](https://developer.mozilla.org/en-US/docs/Web/API/Window/history "history").

**Note:** This interface is only available on the main thread ([`Window`](https://developer.mozilla.org/en-US/docs/Web/API/Window)). It cannot be accessed in [`Worker`](https://developer.mozilla.org/en-US/docs/Web/API/Worker) or [`Worklet`](https://developer.mozilla.org/en-US/docs/Web/API/Worklet) contexts.

## [Instance properties](https://developer.mozilla.org/en-US/docs/Web/API/History#instance_properties)

_The `History` interface doesn't inherit any property._

[`length`](https://developer.mozilla.org/en-US/docs/Web/API/History/length "length") Read only

Returns an `Integer` representing the number of elements in the session history, including the currently loaded page. For example, for a page loaded in a new tab this property returns `1`.

[`scrollRestoration`](https://developer.mozilla.org/en-US/docs/Web/API/History/scrollRestoration "scrollRestoration")

Allows web applications to explicitly set default scroll restoration behavior on history navigation. This property can be either `auto` or `manual`.

[`state`](https://developer.mozilla.org/en-US/docs/Web/API/History/state "state") Read only

Returns an `any` value representing the state at the top of the history stack. This is a way to look at the state without having to wait for a [`popstate`](https://developer.mozilla.org/en-US/docs/Web/API/Window/popstate_event "popstate") event.

## [Instance methods](https://developer.mozilla.org/en-US/docs/Web/API/History#instance_methods)

_The `History`_ _interface doesn't inherit any methods._

[`back()`](https://developer.mozilla.org/en-US/docs/Web/API/History/back "back()")

This asynchronous method goes to the previous page in session history, the same action as when the user clicks the browser's Back button. Equivalent to `history.go(-1)`.

Calling this method to go back beyond the first page in the session history has no effect and doesn't raise an exception.

[`forward()`](https://developer.mozilla.org/en-US/docs/Web/API/History/forward "forward()")

This asynchronous method goes to the next page in session history, the same action as when the user clicks the browser's Forward button; this is equivalent to `history.go(1)`.

Calling this method to go forward beyond the most recent page in the session history has no effect and doesn't raise an exception.

[`go()`](https://developer.mozilla.org/en-US/docs/Web/API/History/go "go()")

Asynchronously loads a page from the session history, identified by its relative location to the current page, for example `-1` for the previous page or `1` for the next page. If you specify an out-of-bounds value (for instance, specifying `-1` when there are no previously-visited pages in the session history), this method silently has no effect. Calling `go()` without parameters or a value of `0` reloads the current page.

[`pushState()`](https://developer.mozilla.org/en-US/docs/Web/API/History/pushState "pushState()")

Pushes the given data onto the session history stack with the specified title (and, if provided, URL). The data is treated as opaque by the DOM; you may specify any JavaScript object that can be serialized. Note that all browsers but Safari currently ignore the _title_ parameter. For more information, see [Working with the History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API/Working_with_the_History_API).

[`replaceState()`](https://developer.mozilla.org/en-US/docs/Web/API/History/replaceState "replaceState()")

Updates the most recent entry on the history stack to have the specified data, title, and, if provided, URL. The data is treated as opaque by the DOM; you may specify any JavaScript object that can be serialized. Note that all browsers but Safari currently ignore the _title_ parameter. For more information, see [Working with the History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API/Working_with_the_History_API).

## [Specifications](https://developer.mozilla.org/en-US/docs/Web/API/History#specifications)

| Specification |
| --- |
| [HTML Standard  
<small># the-history-interface</small>](https://html.spec.whatwg.org/multipage/nav-history-apis.html#the-history-interface) |

## [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/API/History#browser_compatibility)

[Report problems with this compatibility data on GitHub](https://github.com/mdn/browser-compat-data/issues/new?mdn-url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FAPI%2FHistory&metadata=%3C%21--+Do+not+make+changes+below+this+line+--%3E%0A%3Cdetails%3E%0A%3Csummary%3EMDN+page+report+details%3C%2Fsummary%3E%0A%0A*+Query%3A+%60api.History%60%0A*+Report+started%3A+2024-04-23T19%3A14%3A17.476Z%0A%0A%3C%2Fdetails%3E&title=api.History+-+%3CSUMMARIZE+THE+PROBLEM%3E&template=data-problem.yml "Report an issue with this compatibility data")

|  | desktop | mobile |
| --- | --- | --- |
|  | 
Chrome

 | 

Edge

 | 

Firefox

 | 

Opera

 | 

Safari

 | 

Chrome Android

 | 

Firefox for Android

 | 

Opera Android

 | 

Safari on iOS

 | 

Samsung Internet

 | 

WebView Android

 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 

`History`

 |  |  |  |  |  |  |  |  |  |  |  |
| [`back`](https://developer.mozilla.org/en-US/docs/Web/API/History/back) |  |  |  |  |  |  |  |  |  |  |  |
| [`forward`](https://developer.mozilla.org/en-US/docs/Web/API/History/forward) |  |  |  |  |  |  |  |  |  |  |  |
| [`go`](https://developer.mozilla.org/en-US/docs/Web/API/History/go) |  |  |  |  |  |  |  |  |  |  |  |
| [`length`](https://developer.mozilla.org/en-US/docs/Web/API/History/length) |  |  |  |  |  |  |  |  |  |  |  |
| [`pushState`](https://developer.mozilla.org/en-US/docs/Web/API/History/pushState) |  |  |  |  |  |  |  |  |  |  |  |
| 

Whether the `unused` parameter is used

DeprecatedNon-standard



 |  |  |  |  |  |  |  |  |  |  |  |
| [`replaceState`](https://developer.mozilla.org/en-US/docs/Web/API/History/replaceState) |  |  |  |  |  |  |  |  |  |  |  |
| 

Whether the `unused` parameter is used

DeprecatedNon-standard



 |  |  |  |  |  |  |  |  |  |  |  |
| [`scrollRestoration`](https://developer.mozilla.org/en-US/docs/Web/API/History/scrollRestoration) |  |  |  |  |  |  |  |  |  |  |  |
| [`state`](https://developer.mozilla.org/en-US/docs/Web/API/History/state) |  |  |  |  |  |  |  |  |  |  |  |

### Legend

Tip: you can click/tap on a cell for more information.

Full support

Full support

No support

No support

Non-standard. Check cross-browser support before using.

Deprecated. Not for use in new websites.

See implementation notes.

## [See also](https://developer.mozilla.org/en-US/docs/Web/API/History#see_also)

-   [`history`](https://developer.mozilla.org/en-US/docs/Web/API/Window/history "history") global object