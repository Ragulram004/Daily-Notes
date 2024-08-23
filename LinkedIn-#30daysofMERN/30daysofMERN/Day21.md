### Day 21: File Uploads and Handling in Node.js

**Uploading Files Using Multer Middleware**

File uploads are a common feature in many web applications. Today, we'll use Multer middleware to handle file uploads in our Express.js application.

**1. Install Multer:**

```bash
npm install multer
```

**2. Set Up Multer:**

We'll set up Multer to handle file uploads and store them in a specified directory.

```javascript
const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

// Route to handle file uploads
app.post('/upload', upload.single('file'), (req, res) => {
  res.send('File uploaded successfully');
});
```

**Storing File Uploads in MongoDB**

**3. GridFS for Large Files:**

For large file storage, we can use GridFS, a specification for storing and retrieving large files in MongoDB.

```javascript
const Grid = require('gridfs-stream');
const conn = mongoose.createConnection('mongodb://localhost:27017/mydatabase');

let gfs;
conn.once('open', () => {
  gfs = Grid(conn.db, mongoose.mongo);
  gfs.collection('uploads');
});

const storage = new GridFsStorage({
  url: 'mongodb://localhost:27017/mydatabase',
  file: (req, file) => {
    return { filename: file.originalname };
  }
});

const upload = multer({ storage });

// Route to handle file uploads to GridFS
app.post('/upload', upload.single('file'), (req, res) => {
  res.send('File uploaded to GridFS');
});
```

**Conclusion:**

Today, we learned how to handle file uploads in Node.js using Multer and store large files in MongoDB using GridFS. Tomorrow, we'll explore real-time communication with Socket.IO.

---
