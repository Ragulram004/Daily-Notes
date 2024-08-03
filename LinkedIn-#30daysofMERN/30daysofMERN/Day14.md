### Day 14: Building RESTful APIs with Express.js

**Introduction to Express.js**

Express.js is a minimal and flexible Node.js web application framework that provides a robust set of features to develop web and mobile applications.

**Advantages of Express.js:**

1. **Simplicity:** Easy to set up and start building web servers.
2. **Middleware:** Use a wide range of middleware for handling requests.
3. **Routing:** Define routes to handle different HTTP methods and endpoints.
4. **Scalability:** Suitable for building scalable applications.
5. **Community Support:** Extensive documentation and a large community of developers.

**Implementing Basic REST Endpoints**

**1. Installing Express.js:**

```bash
npm install express
```

**2. Setting Up an Express Server:**

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.use(express.json());

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

**3. Creating REST Endpoints:**

```javascript
const express = require('express');
const app = express();
const port = 3000;

app.use(express.json());

let users = [
  { id: 1, name: 'Alice', age: 25 },
  { id: 2, name: 'Bob', age: 30 }
];

// GET endpoint
app.get('/api/users', (req, res) => {
  res.send(users);
});

// POST endpoint
app.post('/api/users', (req, res) => {
  const user = { id: users.length + 1, name: req.body.name, age: req.body.age };
  users.push(user);
  res.send(user);
});

// PUT endpoint
app.put('/api/users/:id', (req, res

) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');

  user.name = req.body.name;
  user.age = req.body.age;
  res.send(user);
});

// DELETE endpoint
app.delete('/api/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');

  const index = users.indexOf(user);
  users.splice(index, 1);
  res.send(user);
});

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

**Conclusion:**

Today, we've introduced Express.js and demonstrated how to set up a basic server with RESTful endpoints. These endpoints allow us to handle HTTP requests and perform CRUD operations. Tomorrow, we'll explore advanced features of Express.js.

---
