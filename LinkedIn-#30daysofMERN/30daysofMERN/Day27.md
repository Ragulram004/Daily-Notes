### **Day 27: Performance Optimization in React**

**Optimizing Performance for Large Applications**

As React applications grow, performance becomes a concern. Today, we’ll explore techniques like memoization and analyzing performance bottlenecks in React.

#### **1. Memoization with `useMemo` and `useCallback`**

Memoization helps you avoid unnecessary re-renders by "remembering" the results of expensive calculations or functions.

- **`useMemo`**: Memoizes a computed value.
  
```javascript
const expensiveCalculation = (num) => {
  console.log("Calculating...");
  return num * 2;
};

function App() {
  const [count, setCount] = useState(0);
  const result = useMemo(() => expensiveCalculation(count), [count]);
  
  return <div>{result}</div>;
}
```

- **`useCallback`**: Memoizes a function, preventing re-creations on re-renders.

```javascript
const handleClick = useCallback(() => {
  console.log('Button clicked');
}, []);
```

#### **2. Identifying Performance Bottlenecks**

Use the React Developer Tools for profiling to find performance bottlenecks. In the Profiler tab, you can see how many times components are re-rendering and why.

#### **Conclusion:**

Performance optimizations can make a significant difference in large-scale applications. We explored memoization techniques and how to spot bottlenecks in React apps. Next, we’ll move on to building our full-stack project.

---
