### Day 12: CRUD Operations with MongoDB

**Performing CRUD Operations**

CRUD stands for Create, Read, Update, and Delete, which are the four basic operations for interacting with a database.

**1. Create:**

To insert new documents into a collection, you use the `insertOne` or `insertMany` methods.

```javascript
// Insert a single document
db.collection('users').insertOne({ name: "Alice", age: 25, email: "alice@example.com" });

// Insert multiple documents
db.collection('users').insertMany([
  { name: "Bob", age: 30, email: "bob@example.com" },
  { name: "Charlie", age: 35, email: "charlie@example.com" }
]);
```

**2. Read:**

To retrieve documents from a collection, you use the `find` method.

```javascript
// Find all documents
db.collection('users').find().toArray((err, users) => {
  if (err) throw err;
  console.log(users);
});

// Find documents with a query
db.collection('users').find({ age: { $gte: 30 } }).toArray((err, users) => {
  if (err) throw err;
  console.log(users);
});
```

**3. Update:**

To modify existing documents, you use the `updateOne` or `updateMany` methods.

```javascript
// Update a single document
db.collection('users').updateOne({ name: "Alice" }, { $set: { age: 26 } });

// Update multiple documents
db.collection('users').updateMany({ age: { $lt: 30 } }, { $set: { status: "young" } });
```

**4. Delete:**

To remove documents from a collection, you use the `deleteOne` or `deleteMany` methods.

```javascript
// Delete a single document
db.collection('users').deleteOne({ name: "Charlie" });

// Delete multiple documents
db.collection('users').deleteMany({ age: { $gte: 35 } });
```

**Using MongoDB Compass**

MongoDB Compass is a GUI tool that allows you to interact with your MongoDB databases in a visual way. You can perform CRUD operations, visualize data, and run complex queries without needing to write code.

1. **Download MongoDB Compass:**
   - Go to the https://www.mongodb.com/products/compass and download the latest version.

2. **Connect to Your Database:**
   - Open MongoDB Compass and enter your connection string to connect to your MongoDB instance.

3. **Perform CRUD Operations:**
   - Use the interface to insert, read, update, and delete documents within your collections. You can use the "Create Database" and "Create Collection" buttons to add new data and the "Indexes" tab to create indexes for your collections.

**Conclusion:**

Today, we've learned how to perform CRUD operations in MongoDB using both the command line and MongoDB Compass. These operations form the foundation of working with any database. Tomorrow, we'll explore Mongoose, an ODM library for MongoDB, to simplify these operations in a Node.js environment.
