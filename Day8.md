### Day 8: Styling in React

Welcome to Day 8 of our #30daysofMERNstack series! Today, we're going to explore different approaches to styling React components. By the end of this lesson, you'll know how to style components using CSS, CSS-in-JS libraries, and component libraries like Material-UI or styled-components.

#### Styling with CSS

The simplest way to style React components is by using standard CSS. You can import a CSS file and apply styles using class names.

**Example: Styling with CSS**:

```jsx
import React from 'react';
import './App.css';

function App() {
  return (
    <div className="app">
      <h1 className="app-title">Hello, React!</h1>
    </div>
  );
}

export default App;
```

In this example:
- We import the `App.css` file.
- We apply styles using the `className` attribute.

**App.css**:

```css
.app {
  text-align: center;
}

.app-title {
  color: blue;
}
```

#### CSS-in-JS Libraries

CSS-in-JS libraries allow you to write CSS directly within your JavaScript code. This approach provides more flexibility and helps to scope styles to specific components.

**Example: Styled Components**:

```jsx
import React from 'react';
import styled from 'styled-components';

const Title = styled.h1`
  color: blue;
`;

function App() {
  return (
    <div>
      <Title>Hello, React!</Title>
    </div>
  );
}

export default App;
```

In this example:
- We use the `styled-components` library to define a styled `Title` component.
- We apply styles directly within the JavaScript code.

#### Component Libraries

Component libraries like Material-UI provide pre-built, customizable components that come with their own styles.

**Example: Material-UI**:

```jsx
import React from 'react';
import { Button } from '@material-ui/core';

function App() {
  return (
    <div>
      <Button variant="contained" color="primary">
        Hello, React!
      </Button>
    </div>
  );
}

export default App;
```

In this example:
- We use the `Button` component from the `@material-ui/core` library.
- We apply Material-UI styles by setting the `variant` and `color` props.

#### Conclusion

Today, we've explored different approaches to styling React components, including CSS, CSS-in-JS libraries, and component libraries like Material-UI. Choosing the right approach depends on your project's needs and your team's preferences.