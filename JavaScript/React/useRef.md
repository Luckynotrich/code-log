`useRef` is similar to `useState` in that it can hold and use a  value that you can use in a component. The difference is that, unlike `useState`, `useRef` does not trigger a re-render of the component and `useRef` values are not used in the `return body` of the component. Meaning its not used for something you are rendering.

##### Its a hook that is used for values that are not needed for rendering because `userRef` does not cause the component to re-render.



