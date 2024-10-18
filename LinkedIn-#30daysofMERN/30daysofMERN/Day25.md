### **Day 25: Structuring Large-Scale Node.js Projects**

**Why Structure Matters:**

As your Node.js applications grow, maintaining a clear structure is essential for scalability, collaboration, and ease of maintenance. In this session, we'll cover best practices for organizing your Node.js project and setting it up for long-term success.

#### **1. Typical Folder Structure**

Here’s a scalable folder structure for a Node.js application:

```
project-root/
├── config/         # Configuration files (env, database, etc.)
├── controllers/    # Route handlers
├── models/         # Data models (e.g., Mongoose schemas)
├── routes/         # API route definitions
├── middleware/     # Custom middleware (authentication, logging)
├── services/       # Business logic or external services
├── tests/          # Unit and integration tests
├── utils/          # Helper functions
├── public/         # Static files (if needed)
└── app.js          # Main application file
```

#### **2. Layered Architecture**

A good approach to organizing a large-scale project is separating concerns into layers:
- **Controllers:** Handle HTTP requests and pass data to/from services.
- **Services:** Business logic, often interacting with the database.
- **Models:** Handle data schemas (e.g., Mongoose for MongoDB).
- **Routes:** Organize your API endpoints logically.

#### **3. Environment Variables**

Using `.env` files ensures that sensitive information like database URIs, API keys, and secret tokens remain outside your codebase.

```bash
# Install dotenv
npm install dotenv
```

Create a `.env` file:

```
PORT=5000
DB_URL=mongodb://localhost:27017/myapp
JWT_SECRET=mySecretKey
```

#### **4. Middleware and Error Handling**

Middleware allows you to handle request logging, authentication, and error management efficiently.

```javascript
// app.js
const express = require('express');
const app = express();

// Example of an error-handling middleware
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Internal Server Error');
});

module.exports = app;
```

#### **Conclusion:**

Today, we explored how to structure a Node.js application for scalability. As your application grows, organizing code effectively becomes critical. Tomorrow, we’ll dive into more advanced React topics.

---
