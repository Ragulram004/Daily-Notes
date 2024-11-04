### **Day 26: State Management with `useContext` and `useReducer` 

**Why Combine `useContext` with `useReducer`?**

Using `useReducer` with `useContext` helps us manage complex state logic across different components without prop drilling. Today, we’ll build a **Theme Context** to toggle between light and dark themes, using `useReducer` for a clean state update flow.

---

### **Step 1: Setting Up the Theme Context with `useReducer`**

1. **Create a `ThemeContext.js` file** in your project:

```javascript
// ThemeContext.js
import React, { createContext, useReducer } from 'react';

// Define initial theme state
const initialState = { theme: 'light' };

// Define actions
const TOGGLE_THEME = 'TOGGLE_THEME';

// Reducer function to handle theme changes
const themeReducer = (state, action) => {
  switch (action.type) {
    case TOGGLE_THEME:
      return { theme: state.theme === 'light' ? 'dark' : 'light' };
    default:
      return state;
  }
};

// Create context
export const ThemeContext = createContext();

// Provider component
export const ThemeProvider = ({ children }) => {
  const [state, dispatch] = useReducer(themeReducer, initialState);

  // Theme toggle function
  const toggleTheme = () => {
    dispatch({ type: TOGGLE_THEME });
  };

  return (
    <ThemeContext.Provider value={{ theme: state.theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};
```

In this setup:
- `initialState` holds the default theme as `'light'`.
- The reducer function `themeReducer` toggles between `'light'` and `'dark'` themes based on the `TOGGLE_THEME` action.
- `ThemeProvider` provides the theme state and toggle function to any component within it.

---

### **Step 2: Wrapping Your App in the Theme Provider**

To apply the theme globally, wrap your application in the `ThemeProvider` in your `App.js` file.

```javascript
// App.js
import React from 'react';
import { ThemeProvider } from './ThemeContext';
import Home from './components/Home';

function App() {
  return (
    <ThemeProvider>
      <Home />
    </ThemeProvider>
  );
}

export default App;
```

Now, every component inside `ThemeProvider` will have access to the theme state and the `toggleTheme` function.

---

### **Step 3: Accessing Theme Context in a Component**

Let’s create a `Home` component to use the theme context and demonstrate theme switching.

```javascript
// Home.js
import React, { useContext } from 'react';
import { ThemeContext } from '../ThemeContext';

const Home = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div style={{
      backgroundColor: theme === 'light' ? '#ffffff' : '#333333',
      color: theme === 'light' ? '#000000' : '#ffffff',
      height: '100vh',
      display: 'flex',
      flexDirection: 'column',
      alignItems: 'center',
      justifyContent: 'center'
    }}>
      <h1>{theme === 'light' ? 'Light Theme' : 'Dark Theme'}</h1>
      <button onClick={toggleTheme} style={{ padding: '10px', fontSize: '16px' }}>
        Toggle Theme
      </button>
    </div>
  );
};

export default Home;
```

Here’s what each part does:
- **`useContext(ThemeContext)`**: Accesses the theme state and the toggle function from `ThemeContext`.
- **Dynamic Styling**: Applies a light or dark background and text color based on the current theme.

---

### **Summary of Today’s Content**

In this session, we used both `useContext` and `useReducer` to create a robust and scalable theme toggle system:
- `useReducer` helps with clear state transitions, making it easier to handle more complex theme options in the future.
- `useContext` enables global state sharing without prop drilling, allowing any component to access the theme and toggle function.

With this setup, your app is now theme-responsive, and this pattern can be expanded for other global settings like language or authentication!

---
