### Day 15: Advanced Express.js Features

**Middleware in Express.js**

Middleware functions are functions that have access to the request and response objects and can modify them or terminate the request-response cycle. Middleware can be used for logging, authentication, error handling, and more.

**Example: Logging Middleware:**

```javascript
// Logging middleware
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```

**Error Handling Middleware**

Error handling middleware is used to handle errors that occur during request processing. It should be defined after all other middleware and routes.

**Example: Error Handling Middleware:**

```javascript
// Error handling middleware
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something went wrong!');
});
```

**Routing Techniques and Parameter Handling**

Express.js allows you to define routes with parameters and use different routing techniques.

**Example: Route with Parameters:**

```javascript
app.get('/api/users/:id', (req, res) => {
  const userId = req.params.id;
  const user = users.find(u => u.id === parseInt(userId));
  if (!user) return res.status(404).send('User not found');
  res.send(user);
});
```

**Example: Modular Routing:**

```javascript
// users.js (router module)
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => {
  res.send(users);
});

router.post('/', (req, res) => {
  const user = { id: users.length + 1, name: req.body.name, age: req.body.age };
  users.push(user);
  res.send(user);
});

router.put('/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');

  user.name = req.body.name;
  user.age = req.body.age;
  res.send(user);
});

router.delete('/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');

  const index = users.indexOf(user);
  users.splice(index, 1);
  res.send(user);
});

module.exports = router;

// app.js
const express = require('express');
const app = express();
const usersRouter = require('./users');

app.use(express.json());
app.use('/api/users', usersRouter);

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

**Conclusion:**

Today, we've explored advanced features of Express.js, including middleware, error handling, and routing techniques. These features help you build more robust and modular applications. Tomorrow, we'll focus on user authentication with Express.js and MongoDB.

---
