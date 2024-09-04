### Day 22: Real-time Communication with Socket.IO

**Introduction to WebSocket Communication**

WebSocket is a protocol that enables two-way communication between a client and server over a single, long-lived connection. Today, we'll implement real-time communication in our Express.js application using Socket.IO.

**1. Install Socket.IO:**

```bash
npm install socket.io
```

**2. Set Up Socket.IO on the Server:**

We'll set up a Socket.IO server to handle real-time events.

```javascript
const http = require('http');
const socketIo = require('socket.io');
const server = http.createServer(app);
const io = socketIo(server);

io.on('connection', (socket) => {
  console.log('New client connected');

  socket.on('message', (message) => {
    io.emit('message', message);
  });

  socket.on('disconnect', () => {
    console.log('Client disconnected');
  });
});

server.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

**3. Client-Side Integration:**

We'll integrate Socket.IO on the client side to send and receive real-time messages.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Socket.IO Chat</title>
  <script src="/socket.io/socket.io.js"></script>
</head>
<body>
  <input id="message" type="text" placeholder="Enter message" />
  <button onclick="sendMessage()">Send</button>
  <ul id="messages"></ul>

  <script>
    const socket = io();

    socket.on('message', (message) => {
      const li = document.createElement('li');
      li.textContent = message;
      document.getElementById('messages').appendChild(li);
    });

    function sendMessage() {
      const message = document.getElementById('message').value;
      socket.emit('message', message);
      document.getElementById('message').value = '';
    }
  </script>
</body>
</html>
```

**Conclusion:**

Today, we implemented real-time communication in a Node.js application using Socket.IO. This enables features like live chat and notifications. Tomorrow, we'll discuss REST API best practices.

---
