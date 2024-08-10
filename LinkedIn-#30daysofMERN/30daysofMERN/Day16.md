### Day 16: User Authentication with Express.js and MongoDB

**Implementing User Authentication Using JWT**

User authentication is a crucial aspect of any application. It ensures that only authorized users can access certain parts of your application. Today, we'll implement user authentication in our Express.js app using JWT (JSON Web Tokens) and MongoDB.

**1. Install Necessary Packages:**

```bash
npm install bcryptjs jsonwebtoken
```

**2. Set Up User Model:**

First, we need a user model to store user information. We'll use Mongoose to define our schema and bcryptjs to hash user passwords before saving them to the database.

```javascript
const mongoose = require('mongoose');
const bcrypt = require('bcryptjs');

const userSchema = new mongoose.Schema({
  username: { type: String, required: true, unique: true },
  password: { type: String, required: true }
});

// Hash the password before saving the user
userSchema.pre('save', async function(next) {
  if (!this.isModified('password')) return next();
  const salt = await bcrypt.genSalt(10);
  this.password = await bcrypt.hash(this.password, salt);
  next();
});

const User = mongoose.model('User', userSchema);
```

**3. Register and Login Routes:**

Next, we'll create routes for user registration and login. When a user registers, their password will be hashed and saved to the database. During login, we'll check the hashed password and generate a JWT if the credentials are correct.

```javascript
const express = require('express');
const jwt = require('jsonwebtoken');
const bcrypt = require('bcryptjs');
const router = express.Router();

const User = require('./models/User');

// Register a new user
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

// Login a user
router.post('/login', async (req, res) => {
  try {
    const { username, password } = req.body;
    const user = await User.findOne({ username });
    if (!user || !await bcrypt.compare(password, user.password)) {
      return res.status(401).send('Invalid credentials');
    }
    const token = jwt.sign({ id: user._id }, 'your_jwt_secret');
    res.send({ token });
  } catch (err) {
    res.status(400).send(err.message);
  }
});

module.exports = router;
```

**4. Protect Routes with Middleware:**

To protect routes, we'll create middleware that verifies the JWT token. If the token is valid, the user is allowed access.

```javascript
const jwt = require('jsonwebtoken');

const authMiddleware = (req, res, next) => {
  const token = req.header('Authorization').replace('Bearer ', '');
  if (!token) return res.status(401).send('Access denied');

  try {
    const decoded = jwt.verify(token, 'your_jwt_secret');
    req.user = decoded;
    next();
  } catch (err) {
    res.status(400).send('Invalid token');
  }
};

module.exports = authMiddleware;
```

**Conclusion:**

Today, we covered user authentication using JWT in an Express.js application. We implemented user registration, login, and protected routes with middleware. Tomorrow, we'll explore authorization and access control in Express.js.

---
