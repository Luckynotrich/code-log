[Comparing TypeScript and PropTypes in React applications](https://blog.logrocket.com/comparing-typescript-and-proptypes-in-react-applications/)
[Dillion Megida](https://blog.logrocket.com/author/dillion-megida/)

## What is PropTypes?

PropTypes is a runtime type-checking tool for props in React applications. Since React 15.5, the PropTypes utility is available through the [prop-types](https://www.npmjs.com/package/prop-types) package. With PropTypes, you can define the types of props expected in a component, like stating whether props are required or optional. When you pass a different type to a component or skip a required prop, you will get a warning in the JavaScript console:
```
import React from 'react'
import PropTypes from 'prop-types'

const NotificationCard = ({ message, type, id }) => { 
  return <span>Notification</Notification>
}

NotificationCard.propTypes = {
  message: PropTypes.string.isRequired,
  type: PropTypes.oneOf(["error", "warning", "success"]),
  id: PropTypes.string.isRequired
}

export default NotificationCard
```

However, you may not need to sacrifice any features — there are ways to enjoy both runtime and compile-time type checking.

First, you can choose to write type definitions and PropTypes definitions for your application. This will be strenuous in the long run when you have to write both definitions for every component in your application. Let’s review two ways in which you can write one and automatically generate the other.
### 1. `InferProps`

`InferPropTypes` from [@types/prop-types](https://www.npmjs.com/package/@types/prop-types) can be used to create type definitions from PropTypes definitions. Here’s an example:

```
import React from "react";
import PropTypes, { InferProps } from "prop-types";

const BlogCardPropTypes = {
    title: PropTypes.string.isRequired,
    createdAt: PropTypes.instanceOf(Date),
    authorName: PropTypes.string.isRequired,
};

type BlogCardTypes = InferProps<typeof BlogCardPropTypes>;
const BlogCard = ({ authorName, createdAt, title }: BlogCardTypes) => {
    return <span>Blog Card</span>;
};

BlogCard.propTypes = BlogCardPropTypes;

export default BlogCard;
```

### 2. `babel-plugin-typescript-to-proptypes`

You can generate PropTypes from TypeScript type definitions using [babel-plugin-typescript-to-proptypes](https://www.npmjs.com/package/babel-plugin-typescript-to-proptypes). When you specify types for your props, the plugin converts those type definitions to PropTypes definitions.

For example, the following code:
```
import React from "react";
type Props = {
    title: string;
    createdAt: Date;
    authorName: string;
};
const BlogCard = ({ title, createdAt, authorName }: Props) => {
    return <span>Blog card</span>;
};
export default BlogCard;
```
