So far it seems that React-Query(RQ) doesn't get along and creates conflicts, with libraries that previously worked fine. 

Context is a perfect example. Before RQ components would get data from context and function well. Not so after.  I would like to move RQ to Context and it seems possible, but maybe not worth the hassle. 

Re-above:: I was able to move  the category query to its own context and with useEffect synchronize  category context. This worked pretty well as I was able to use features of Category context that I had already implemented.

Before RQ, HTTP-proxy-middleware would pass queries along to the server. Naturally now RQ expect a direct line to the source and I must disable the proxy to find out...nope that wasn't the problem. 

Not sure why but, exporting Axios from future_self_api stopped working for form submits. Currently, I am in the process of [implementing RQ in place of basic Axios calls](https://tkdodo.eu/blog/react-query-and-forms), but of course this is not a direct path. If data which will be created in the form is not defined in the mutate at the component call, react errors as ''data is undefined''. Defaults can't be set and uncontrolled fields don't work with the preferred method. Since I am already using uncontrolled fields, I am using the less preferred method of separating the mutate into a function that only calls the form. 