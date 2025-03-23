<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](./Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Using WebSockets in React & React Native</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>


## 🔹 What are WebSockets?
WebSockets provide a full-duplex communication channel over a single TCP connection. Unlike HTTP, which is request-response-based, WebSockets allow real-time bidirectional data exchange between the client and server.

## 🔹 Why Use WebSockets?
- **Real-time updates**: Ideal for chat apps, notifications, live dashboards.
- **Efficient**: Reduces the need for polling and unnecessary HTTP requests.
- **Low latency**: Faster than traditional HTTP request-response models.

---

## 🔹 Implementing WebSockets in React
### 1️⃣ Using Browser WebSockets API
The `WebSocket` API is built into modern browsers and can be used as follows:
```javascript
const socket = new WebSocket('ws://your-websocket-server');

socket.onopen = () => {
  console.log('Connected to WebSocket server');
};

socket.onmessage = (event) => {
  console.log('Message from server: ', event.data);
};

socket.onerror = (error) => {
  console.error('WebSocket Error: ', error);
};

socket.onclose = () => {
  console.log('WebSocket connection closed');
};
```

### 2️⃣ Using Third-Party Libraries (socket.io-client)
`socket.io-client` simplifies WebSocket handling.
```javascript
import { io } from 'socket.io-client';

const socket = io('http://your-server-url');

socket.on('connect', () => {
  console.log('Connected to WebSocket server');
});

socket.on('message', (data) => {
  console.log('Received:', data);
});

socket.emit('message', 'Hello Server!');
```

---

## 🔹 Implementing WebSockets in React Native
React Native does not support the native `WebSocket` API as in the browser, but you can use:
- **WebSocket API (built-in)**
- **socket.io-client (recommended for better compatibility)**

Example using WebSocket API:
```javascript
const socket = new WebSocket('ws://your-websocket-server');

useEffect(() => {
  socket.onopen = () => console.log('Connected');
  socket.onmessage = (event) => console.log('Message:', event.data);
  socket.onerror = (error) => console.error('Error:', error);
  socket.onclose = () => console.log('Closed');

  return () => socket.close(); // Cleanup on unmount
}, []);
```

Example using `socket.io-client`:
```javascript
import { io } from 'socket.io-client';

const socket = io('http://your-server-url');

useEffect(() => {
  socket.on('connect', () => console.log('Connected'));
  socket.on('message', (data) => console.log('Message:', data));

  return () => socket.disconnect();
}, []);
```

---

## 🔹 WebSockets vs. HTTP Polling
| Feature        | WebSockets | HTTP Polling |
|---------------|-----------|-------------|
| Connection Type | Persistent | Repeated requests |
| Latency | Low | High (due to repeated requests) |
| Data Transfer | Bidirectional | Request-response only |
| Best For | Live data, chat, gaming | Periodic updates |

---

## 🔹 WebSockets Interview Questions
1. **How does WebSocket work in React?**
2. **Difference between WebSocket and HTTP polling?**
3. **How to handle WebSocket reconnection in React Native?**
4. **How does socket.io differ from the native WebSocket API?**
5. **How to optimize WebSocket performance in a React application?**

Let me know if you need more details! 🚀



  </div>