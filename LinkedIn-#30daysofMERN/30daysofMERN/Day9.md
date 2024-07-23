### Day 9: React Router for Navigation

Welcome to Day 9 of our #30daysofMERNstack series! Today, we're going to learn how to set up navigation in React applications using React Router. By the end of this lesson, you'll know how to create nested routes and navigation menus.

#### Setting Up Routing in React Applications

React Router is a popular library for adding navigation and routing to React applications. It allows you to define routes and link to different parts of your app.

**Installing React Router**:

First, install React Router:

```bash
npm install react-router-dom
```

**Basic Setup**:

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Switch, Link } from 'react-router-dom';

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
          </ul>
        </nav>
        <Switch>
          <Route exact path="/">
            <Home />
          </Route>
          <Route path="/about">
            <About />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

In this example:
- We import necessary components from `react-router-dom`.
- We define `Home` and `About` components.
- We use the `Router`, `Route`, `Switch`, and `Link` components to set up routing.

#### Creating Nested Routes

React Router allows you to create nested routes, which is useful for structuring more complex applications.

**Example: Nested Routes**:

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Switch, Link, useRouteMatch } from 'react-router-dom';

function Topic({ match }) {
  return <h3>Requested topic ID: {match.params.topicId}</h3>;
}

function Topics() {
  let { path, url } = useRouteMatch();

  return (
    <div>
      <h2>Topics</h2>
      <ul>
        <li>
          <Link to={`${url}/components`}>Components</Link>
        </li>
        <li>
          <Link to={`${url}/props-v-state`}>Props v. State</Link>
        </li>
      </ul>

      <Switch>
        <Route exact path={path}>
          <h3>Please select a topic.</h3>
        </Route>
        <Route path={`${path}/:topicId`}>
          <Topic />
        </Route>
      </Switch>
    </div>
  );
}

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/topics">Topics</Link>
            </li>
          </ul>
        </nav>

        <Switch>
          <Route exact path="/">
            <h2>Home</h2>
          </Route>
          <Route path="/topics">
            <Topics />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

In this example:
- We use `useRouteMatch` to create nested routes for topics.
- The `Topics` component renders links to nested routes and displays the selected topic.

#### Conclusion

Today, we've learned how to set up routing in React applications using React Router, create nested routes, and build navigation menus. Mastering React Router is essential for creating multi-page applications and ensuring a smooth user experience.

---