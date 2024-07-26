---
created: 2024-07-25T08:52:17 (UTC -07:00)
source: https://dev.to/fatehmohamed14/typescript-event-types-for-react-3epa?signin=true
author: Fateh Mohamed
---

# Typescript event types for React - DEV Community

> ## Excerpt
> When you migrate your React applications from Javascript to Typescript you want everything to be...

---
[![Cover image for Typescript event types for React](https://media.dev.to/cdn-cgi/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fu5jxzf8mnlvnlobcrjri.png)](https://media.dev.to/cdn-cgi/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fu5jxzf8mnlvnlobcrjri.png)

[![Fateh Mohamed 🐢](https://media.dev.to/cdn-cgi/image/width=50,height=50,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Fuser%2Fprofile_image%2F500314%2F0811b900-8a2e-4116-a416-87dacab863d2.jpeg)](https://dev.to/fatehmohamed14)

 ![](https://dev.to/assets/sparkle-heart-5f9bee3767e18deb1bb725290cb151c25234768a0e9a2bd39370c382d02920cf.svg) 8

When you migrate your React applications from Javascript to Typescript you want everything to be typed right! and If you start having the type **any** it means that you are in the wrong direction 😞

Ok cool, you have to create your own types, interfaces... but what about React types, for instance React Events types.  
For instance you have a submit event  

```ts
 const handleSubmit = (event) =>; {
    event.preventDefault()
    const data = new FormData(event.currentTarget)
    console.log({
      email: data.get('email'),
      password: data.get('password'),
    })
  }
```

Typescript is complaining and you need to provide a type for your event

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--6oDqIZ0V--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eyhaq0hoxztvy58hmenm.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--6oDqIZ0V--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eyhaq0hoxztvy58hmenm.png)

You need to know what type is your **event** here, but how? 🤔  
All what you have to do is to write an inline event handler and hover over the event parameter to know that it's of type `React.FormEvent<HTMLFormElement>` 👍

[![Image description](https://res.cloudinary.com/practicaldev/image/fetch/s--IoTRHYkw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/enhfq9zn7lqmha79qnlq.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--IoTRHYkw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/enhfq9zn7lqmha79qnlq.png)

Great! Here is your new code and Typescript is happy  

```ts

const handleSubmit = (event: React.FormEvent;<HTMLFormElement>;) =>; {
 ...
```

Till now everything is good but can't you see that it's a long ugly type 😫 You can make it shorter and nicer.

Let us create a new types file **types.ts** where we can create new types or in our case only renaming existing ugly ones. Examples bellow  

```
type FormEvent = React.FormEvent&lt;HTMLFormElement&gt;
type MouseEvent = React.MouseEvent&lt;HTMLButtonElement&gt;
type ChangeEvent = React.ChangeEvent&lt;HTMLInputElement&gt;
...

export { FormEvent, MouseEvent, ChangeEvent };
```

Now our `React.FormEvent<HTMLFormElement>` type became _**FormEvent**_ 😎

Again here is how our code will look like now  

```
import { FormEvent } from './types'

const handleSubmit = (event: FormEvent) =&gt; {
 ...
```

Short, Clean and Correct.

Thanks for reading and hope it was helpful
