```js
import { useState } from "react";
import Heading from "./components/Heading";
import {Section }from "./components/Section";
import Counter from "./components/Counter";
import List from "./components/List";
 
function App() {
const [count, setCount] = useState<number>(1);

return (
	<>
		<Heading title={"hello world!"}></Heading>
		<Section>This is a section.</Section>
		<Counter setCount={setCount}> Count = {count}</Counter>
		<List 
			items={['Espresso','Pizza','Code']} render={(item: string)=> 
			<span className='bold'>{item}</span>}
		></List>
	</>
	)
}


export default App
```

```js
import React,{ReactElement} from 'react'
type HeadingProps = {
     title: string
};

const Heading = ({title}: HeadingProps):ReactElement => {
  return (
    <h1>{title}</h1>
  )
}

export default Heading
```

```js
import React, {ReactNode} from "react";
type CounterProps = {
  setCount: React.Dispatch<React.SetStateAction<number>>,
  children: ReactNode,
}

const Counter = ({setCount,children}:CounterProps) => {
  
  return (
    <>
      <h1>{children}</h1>
      <button onClick={() => setCount(prev => prev+1)}>&nbsp;+&nbsp;</button>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <button onClick={() => setCount(prev => prev-1)}>&nbsp;-&nbsp;</button>
    </>
  );
};

export default Counter;
```

```js
import React, { ReactNode } from "react";
type SectionProps ={
        title?: string,
        children: ReactNode
}
                                         // Default because title is optional
export const Section = ({ children,title = "Default SubHeading"}:SectionProps) =>{
    return(
        <section>
            <h2>{title}</h2>
            <p>{children}</p>
        </section>
    )
}
```

```js

import React, { ReactNode } from "react";

interface ListProps<T> {
    items: T[],
    render: (item: T) => ReactNode
}


const List = <T,>({items, render}: ListProps<T>) => {
  return (
    <ul>
        {items.map((item, i) =>
            <li key={i}>
                {render(item)}
            </li>
        )}
    </ul>
  )
}

export default List

```