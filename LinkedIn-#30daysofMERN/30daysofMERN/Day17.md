### Day 17: Authorization and Access Control

**Role-Based Access Control (RBAC) in Express.js**

Authorization is the process of determining what actions a user is allowed to perform. Today, we'll implement role-based access control in our Express.js application to restrict access to certain routes based on user roles.

**1. Add Roles to User Model:**

We'll add a role field to our user model to differentiate between different types of users (e.g., 'user' and 'admin').

```javascript
const userSchema = new mongoose.Schema({
  username: { type: String, required: true, unique: true },
  password: { type: String, required: true },
  role: { type: String, default: 'user' }  // user or admin
});
```

**2. Middleware for Role-Based Access Control:**

Next, we'll create middleware to check if a user has the required role to access a route.

```javascript
const checkRole = (roles) => (req, res, next) => {
  if (!roles.includes(req.user.role)) {
    return res.status(403).send('Access denied');
  }
  next();
};

module.exports = checkRole;
```

**3. Apply Middleware to Routes:**

We'll apply our role-checking middleware to routes to restrict access based on user roles.

```javascript
const express = require('express');
const authMiddleware = require('./middleware/auth');
const checkRole = require('./middleware/checkRole');
const router = express.Router();

// Admin-only route
router.get('/admin', [authMiddleware, checkRole(['admin'])], (req, res) => {
  res.send('Admin access granted');
});

// User and admin route
router.get('/user', [authMiddleware, checkRole(['user', 'admin'])], (req, res) => {
  res.send('User access granted');
});

module.exports = router;
```

**Conclusion:**

Today, we implemented role-based access control in an Express.js application. This allows us to restrict access to certain routes based on user roles. Tomorrow, we'll focus on error handling and validation in Express.js.

---