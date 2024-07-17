### Day 3: React Components and Props

Welcome to Day 3 of our #30daysofMERNstack series! Today, we’re going to explore React components and props. By the end of this article, you’ll understand how to create functional components and pass data between them using props.

#### What are React Components?

Components are the building blocks of a React application. They let you split the UI into independent, reusable pieces, and think about each piece in isolation. Conceptually, components are like JavaScript functions. They accept inputs (called “props”) and return React elements describing what should appear on the screen.

#### Exploring Functional Components

Functional components are a simpler way to write components that only contain a `render` method and don’t have their own state. They are simply JavaScript functions that accept props as an argument and return React elements.

**Creating a Functional Component**:

Here’s an example of a simple functional component:

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

In this example, `Welcome` is a functional component that accepts a single prop, `name`, and renders a heading element with a greeting message.

**Using the Functional Component**:

To use the `Welcome` component, you can include it in another component’s render method:

```jsx
function App() {
  return (
    <div>
      <Welcome name="Alice" />
      <Welcome name="Bob" />
      <Welcome name="Charlie" />
    </div>
  );
}
```

In this example, the `App` component renders three `Welcome` components, each with a different `name` prop.

#### Passing Props Between Components

Props (short for “properties”) are used to pass data from one component to another. They are read-only and should not be modified by the receiving component. Props are passed to components in a similar way to how arguments are passed to functions.

**Defining Props**:

Here’s an example of a functional component that accepts multiple props:

```jsx
function Greeting(props) {
  return (
    <div>
      <h1>Hello, {props.name}!</h1>
      <p>Your favorite color is {props.favoriteColor}.</p>
    </div>
  );
}
```

**Passing Props**:

To pass props to the `Greeting` component, include them as attributes when rendering the component:

```jsx
function App() {
  return (
    <div>
      <Greeting name="Alice" favoriteColor="blue" />
      <Greeting name="Bob" favoriteColor="green" />
      <Greeting name="Charlie" favoriteColor="red" />
    </div>
  );
}
```

In this example, the `Greeting` component receives `name` and `favoriteColor` props, and uses them to render personalized messages.

#### Destructuring Props

To make your code cleaner and more readable, you can use destructuring to extract props directly in the function parameter list:

```jsx
function Greeting({ name, favoriteColor }) {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>Your favorite color is {favoriteColor}.</p>
    </div>
  );
}
```

Destructuring props can be especially useful when dealing with components that accept many props.

#### Conclusion

Today, we explored functional components and how to pass data between them using props. Understanding these concepts is fundamental to building dynamic and reusable React applications.

In the next lesson, we'll delve deeper into state management in React and learn how to handle dynamic data within components. Stay tuned and happy coding!
