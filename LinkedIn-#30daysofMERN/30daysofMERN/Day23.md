### Day 23: REST API Best Practices

**Designing and Documenting RESTful APIs**

Designing well-structured REST APIs is crucial for building scalable and maintainable applications. Today, we'll discuss best practices for designing REST APIs and how to document them.

**1. Use Proper HTTP Methods:**

- **GET:** Retrieve data
- **POST:** Create new data
- **PUT:** Update existing data
- **DELETE:** Remove data

**2. Use Meaningful Resource Names:**

Resource names should be nouns and use plural forms.

```plaintext
GET /api/users
POST /api/users
GET /api/users/:id
PUT /api/users/:id
DELETE /api/users/:id
```

**3. Return Proper HTTP Status Codes:**

HTTP status codes convey the result of the operation.

- **200:** OK
- **201:** Created
- **400:** Bad Request
- **401:** Unauthorized
- **403:** Forbidden
- **404:** Not Found
- **500:** Internal Server Error

**4. Handle Errors Gracefully:**

Implement error handling middleware to manage errors consistently.

```javascript
app.use((err, req, res, next) => {
  res.status(err.status || 500).json({ error: err.message });
});
```

**5. Document APIs with Swagger:**

**Install Swagger:**

```bash
npm install swagger-ui-express swagger-jsdoc
```

**Set Up Swagger:**

Use Swagger to create interactive API documentation.

```javascript
const swaggerUi = require('swagger-ui-express');
const swaggerJsdoc = require('swagger-jsdoc');

const options = {
  definition: {
    openapi: '3.0.0',
    info: { title: 'API Documentation', version: '1.0.0' }
  },
  apis: ['./routes/*.js']
};

const specs = swaggerJsdoc(options);
app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(specs));
```

**Conclusion:**

Today, we covered best practices for designing REST APIs, including proper HTTP methods, meaningful resource names, appropriate status codes, and error handling. We also set up Swagger for API documentation. Tomorrow, we'll dive into unit testing in Node.js.

---
