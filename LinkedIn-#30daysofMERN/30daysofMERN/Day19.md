### Day 19: Integrating MongoDB with Express.js

**Connecting an Express.js Application to MongoDB**

Today, we'll connect our Express.js application to MongoDB using Mongoose and perform database operations.

**1. Setup Mongoose Connection:**

First, we'll set up a connection to our MongoDB database using Mongoose.

```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/mydatabase', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('Connected to MongoDB'))
  .catch(err => console.error('Could not connect to MongoDB', err));
```

**Performing Database Operations**

**2. Create a Model:**

We'll create a user model to interact with our MongoDB database.

```javascript
const userSchema = new mongoose.Schema({
  username: { type: String, required: true, unique: true },
  password: { type: String, required: true }
});

const User = mongoose.model('User', userSchema);
```

**3. Use the Model in Routes:**

We'll use our model in routes to perform CRUD operations.

```javascript
// Register route
router.post('/register', async (req, res) => {
  try {
    const { username, password } = req.body;
    let user = new User({ username, password });
    await user.save();
    res.status(201).send('User registered');
  } catch (err) {
    res.status(400).send(err.message);
  }
});

// Get all users
router.get('/users', async (req, res) => {
  const users = await User.find();
  res.send(users);
});
```

**Conclusion:**

Today, we integrated MongoDB with Express.js using Mongoose. We covered setting up a Mongoose connection, creating models, and performing database operations within Express.js routes. Tomorrow, we'll dive into asynchronous programming in Node.js.

---