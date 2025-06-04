# [ HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)
HTTP defines a set of **request methods** to indicate the purpose of the request and what is expected if the request is successful. Although they can also be nouns, these request methods are sometimes referred to as _HTTP verbs_. Each request method has its own semantics, but some characteristics are shared across multiple methods, specifically request methods can be [safe](https://developer.mozilla.org/en-US/docs/Glossary/Safe/HTTP), [idempotent](https://developer.mozilla.org/en-US/docs/Glossary/Idempotent), or [cacheable](https://developer.mozilla.org/en-US/docs/Glossary/Cacheable).

[`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/GET)
The `GET` method requests a representation of the specified resource. Requests using `GET` should only retrieve data and should not contain a request [content](https://developer.mozilla.org/en-US/docs/Glossary/HTTP_Content).

[`HEAD`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/HEAD)
The `HEAD` method asks for a response identical to a `GET` request, but without a response body.

[`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/POST)
The `POST` method submits an entity to the specified resource, often causing a change in state or side effects on the server.

[`PUT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PUT)
The `PUT` method replaces all current representations of the target resource with the request [content](https://developer.mozilla.org/en-US/docs/Glossary/HTTP_Content).

[`DELETE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/DELETE)
The `DELETE` method deletes the specified resource.

[`CONNECT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/CONNECT)
The `CONNECT` method establishes a tunnel to the server identified by the target resource.

[`OPTIONS`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/OPTIONS)
The `OPTIONS` method describes the communication options for the target resource.

[`TRACE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/TRACE)
The `TRACE` method performs a message loop-back test along the path to the target resource.

[`PATCH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PATCH)
The `PATCH` method applies partial modifications to a resource.

## [Safe, idempotent, and cacheable request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods#safe_idempotent_and_cacheable_request_methods)

The following table lists HTTP request methods and their categorization in terms of safety, cacheability, and idempotency.

| Method | Safe | Idempotent | Cacheable |
| --- | --- | --- | --- |
| [`GET`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/GET) | Yes | Yes | Yes |
| [`HEAD`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/HEAD) | Yes | Yes | Yes |
| [`OPTIONS`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/OPTIONS) | Yes | Yes | No |
| [`TRACE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/TRACE) | Yes | Yes | No |
| [`PUT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PUT) | No | Yes | No |
| [`DELETE`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/DELETE) | No | Yes | No |
| [`POST`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/POST) | No | No | Conditional\* |
| [`PATCH`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PATCH) | No | No | Conditional\* |
| [`CONNECT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/CONNECT) | No | No | No |

\* `POST` and `PATCH` are cacheable when responses explicitly include [freshness](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Caching) information and a matching [`Content-Location`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Location) header.

## [Specifications](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods#specifications)

| Specification |
| --- |
| [HTTP Semantics  
\# POST](https://httpwg.org/specs/rfc9110.html#POST) |
| [HTTP Semantics  
\# DELETE](https://httpwg.org/specs/rfc9110.html#DELETE) |
| [HTTP Semantics  
\# PUT](https://httpwg.org/specs/rfc9110.html#PUT) |
| [HTTP Semantics  
\# OPTIONS](https://httpwg.org/specs/rfc9110.html#OPTIONS) |
| [HTTP Semantics  
\# GET](https://httpwg.org/specs/rfc9110.html#GET) |
| [HTTP Semantics  
\# HEAD](https://httpwg.org/specs/rfc9110.html#HEAD) |
| [HTTP Semantics  
\# CONNECT](https://httpwg.org/specs/rfc9110.html#CONNECT) |

## [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods#browser_compatibility)

## [See also](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods#see_also)