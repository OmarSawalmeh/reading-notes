# **Message Queues**
## **Message Queue Overview :**
Writing a chat application with popular web applications stacks like LAMP (PHP) has normally been very hard. It involves polling the server for changes, keeping track of timestamps, and it’s a lot slower than it should be.

Sockets have traditionally been the solution around which most real-time chat systems are architected, providing a bi-directional communication channel between a client and a server.

This means that the server can push messages to clients. Whenever you write a chat message, the idea is that the server will get it and push it to all other connected clients.

Offloading work to a separate process is key to building scalable web applications and APIs. You need to be able to transfer compute intensive tasks from the request/response lifecycle. When building applications you can use one of two interaction patterns:

Request-Response (synchronous): An answer is returned with a response. For example, in e-commerce applications, a user is notified immediately if a submitted order has been processed or if there are any issues.

Fire-and-forget (asynchronous): A request has been received and an alternative means to get the response is provided. For example, when users import a large amount of data that needs to be processed, they receive acknowledgement that the data has been received and instructed to check an import queue to view the status. Or, a message is sent upon import completion.

In both synchronous and asynchronous operations, you can offload processing and free up resources so that the application can handle other requests. This is done using message queue. Message queues come in many shapes and sizes, and can organize the flow of messages in different ways. A very important advantage of using message queues in your project is feature growth, because what may start as a simple project can easily grow into a monster if not planned properly. We suggest considering RabbitMQ.

The web framework
The first goal is to set up a simple HTML webpage that serves out a form and a list of messages. We’re going to use the Node.JS web framework express to this end. Make sure Node.JS is installed.

First let’s create a package.json manifest file that describes our project. I recommend you place it in a dedicated empty directory (I’ll call mine chat-example).

```js
{
  "name": "socket-chat-example",
  "version": "0.0.1",
  "description": "my first socket.io app",
  "dependencies": {}
}
```

Now, in order to easily populate the dependencies property with the things we need, we’ll use npm install:


```js
npm install express@4

```
Once it's installed we can create an index.js file that will set up our application.


```js
const express = require('express');
const app = express();
const http = require('http');
const server = http.createServer(app);

app.get('/', (req, res) => {
  res.send('<h1>Hello world</h1>');
});

server.listen(3000, () => {
  console.log('listening on *:3000');
});
```

## **Namespaces**
A Namespace is a communication channel that allows you to split the logic of your application over a single shared connection (also called "multiplexing").
![](https://socket.io/assets/images/namespaces-088745a8a8882118740f50b6b1232588.png)

---

## **Rooms :**
- With single Socket.IO servers
A room is an arbitrary channel that sockets can join and leave. It can be used to broadcast events to a subset of clients:
![](https://socket.io/images/rooms.png)

- With multiple Socket.IO servers
Like global broadcasting, broadcasting to rooms also works with multiple Socket.IO servers.
You just need to replace the default Adapter by the Redis Adapter. More information about it here.
![](https://socket.io/images/rooms-redis.png)

---
## **Sources :**
- [socket.io get-started](https://socket.io/get-started/chat/)
- [socket.io rooms](https://socket.io/docs/v4/rooms)
- [socket.io namespaces](https://socket.io/docs/v4/namespaces/)
- [socket.io emit-cheatsheet](https://socket.io/docs/v4/emit-cheatsheet/)

---
- [BACK (Main Page)](./README.md)
---

