### Day 18: Error Handling and Validation

**Implementing Error Handling Middleware**

Effective error handling is essential for building robust applications. Today, we'll implement error handling middleware in Express.js and use Joi for request validation.

**1. Error Handling Middleware:**

Error handling middleware catches errors that occur during request processing and sends a proper response to the client.

```javascript
const errorMiddleware = (err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something went wrong!');
};

app.use(errorMiddleware);
```

**Using Joi for Validation**

**2. Install Joi:**

Joi is a powerful validation library for JavaScript.

```bash
npm install joi
```

**3. Validate Request Data:**

We'll use Joi to validate incoming request data before processing it.

```javascript
const Joi = require('joi');

const userSchema = Joi.object({
  username: Joi.string().min(3).required(),
  password: Joi.string().min(5).required()
});

// Register route with validation
router.post('/register', async (req, res) => {
  try {
    const { error } = userSchema.validate(req.body);
    if (error) return res.status(400).send(error.details[0].message);

    const { username, password } = req.body;
    let user = new User({ username, password });
    await user.save();
    res.status(201).send('User registered');
  } catch (err) {
    res.status(400).send(err.message);
  }
});
```

**Conclusion:**

Today, we implemented error handling and validation in our Express.js application. Error handling middleware helps manage errors gracefully, while Joi simplifies request data validation. Tomorrow, we'll integrate MongoDB with Express.js using Mongoose.

---