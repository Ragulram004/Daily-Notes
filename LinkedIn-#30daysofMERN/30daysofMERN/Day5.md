### Day 5: useEffect Hook and Lifecycle Methods
Welcome to Day 5 of our #30daysofMERNstack series! Today, we'll dive into the `useEffect` hook and lifecycle methods in React. By the end of this lesson, you'll understand how to manage side effects and use the `useEffect` hook for fetching data and subscribing to changes.

#### Managing Side Effects in React

In React, side effects are operations that can affect other components and can't be done during rendering, such as data fetching, subscriptions, or manually changing the DOM. The `useEffect` hook allows you to perform these side effects in functional components.

#### The useEffect Hook

The `useEffect` hook takes two arguments: a function containing the side effect logic, and an optional array of dependencies that control when the effect should run.

**Basic Syntax**

```jsx
useEffect(() => {   
	// side effect logic here 
	}, [dependencies]);
```

**Example: Fetching Data**:

Let's create an example component that fetches data from an API and displays it:

```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(data => {
        setData(data);
        setLoading(false);
      });
  }, []);

  return (
    <div>
      {loading ? <p>Loading...</p> : <ul>{data.map(item => <li key={item.id}>{item.title}</li>)}</ul>}
    </div>
  );
}

export default DataFetcher;

```
In this example:

- We use `useState` to manage the `data` and `loading` states.
- The `useEffect` hook fetches data from an API when the component mounts (empty dependency array `[]`).
- We update the state with the fetched data and set `loading` to `false` when the data is loaded.

#### Cleanup and Dependencies

The `useEffect` hook can also return a cleanup function to clean up after the side effect. This is useful for unsubscribing from subscriptions or clearing timers.

**Example: Setting up a Timer**:

```jsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log('Tick');
  }, 1000);

  // Cleanup function
  return () => clearInterval(timer);
}, []);

```

#### Conclusion

Today, we've explored how to manage side effects in React using the `useEffect` hook. We've also seen how to fetch data and clean up after side effects. Understanding the `useEffect` hook is crucial for working with asynchronous operations and integrating with external systems.