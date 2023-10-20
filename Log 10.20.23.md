#### Today 10-20-23
Struggling with `react-router-dom` and Obsidian code formatting. On the latter, I was fighting phantom MD that mis-formatted my layout. I hope that the problem is O can't deal with large files, so I started a 'Log dating' naming convention.

`react-router-dom` is not very intuitive and offers a group of hooks that are not well exampled. It seems that most people/tutorials don't deal with many of the hooks. This [Log Rocket - Using Hooks with React Router](https://blog.logrocket.com/using-hooks-react-router/) is about the best I've found to date. 

`NavLink` is a component of R.R.D. [# React Router DOM: The Differences Between `NavLink`, Link, and `<a>`](https://javascript.plainenglish.io/react-router-dom-the-differences-between-navlink-link-and-a-bb5c27a48bfc)


```js
<Link to='/home'>Home</Link>

<Link
  to={{
    pathname: "/entrees",
    search: "?sort=rating",
    hash: "#the-hash",
    state: { showMenu: true }
  }}
/>
```

### Get Ubuntu setup with continuous updates
