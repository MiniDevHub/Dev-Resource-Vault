<div align="center">

# 🔌 WebSockets & Real-time Communication

### _Build interactive, instant, bidirectional applications_ ⚡

![WebSockets](https://img.shields.io/badge/WebSockets-Real--time-purple?style=for-the-badge)
![Socket.IO](https://img.shields.io/badge/Socket.IO-4.6+-black?style=for-the-badge&logo=socket.io)
![Protocol](https://img.shields.io/badge/Protocol-Bidirectional-green?style=for-the-badge)

</div>

---

## 📚 Table of Contents

- [🎯 Real-time Fundamentals](#-real-time-fundamentals)
- [🔌 Socket.IO](#-socketio)
- [⚡ Native WebSockets](#-native-websockets)
- [📡 Server-Sent Events](#-server-sent-events)
- [🚀 Scaling WebSockets](#-scaling-websockets)
- [🔐 Security](#-security)
- [💡 Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Real-time Fundamentals

</div>

### Understanding Real-time Communication 📖

```javascript
// ═══════════════════════════════════════════
// HTTP vs WebSocket
// ═══════════════════════════════════════════

/*
Traditional HTTP (Request-Response):
Client  →  Request  →  Server
Client  ←  Response ←  Server
- One-way at a time
- High latency
- Overhead per request
- Not suitable for real-time

WebSocket (Bidirectional):
Client  ⇄  Full-duplex  ⇄  Server
- Both can send anytime
- Low latency
- Persistent connection
- Perfect for real-time

WebSocket Lifecycle:
1. HTTP Handshake (Upgrade request)
2. Connection established
3. Bidirectional messages
4. Connection closed
*/

// ═══════════════════════════════════════════
// When to Use WebSockets
// ═══════════════════════════════════════════

/*
✅ USE WebSockets for:
- Chat applications
- Real-time notifications
- Live feeds/updates
- Collaborative editing
- Online gaming
- Stock tickers
- Live sports scores
- IoT dashboards
- Video conferencing (with WebRTC)

❌ DON'T use WebSockets for:
- Simple REST APIs
- Static content
- File uploads
- One-way data flow (use SSE)
- Infrequent updates (polling is fine)
*/

// ═══════════════════════════════════════════
// Real-time Technologies Comparison
// ═══════════════════════════════════════════

/*
1. WebSockets
   ✅ Full-duplex
   ✅ Low latency
   ✅ Binary support
   ❌ No auto-reconnect
   ❌ Complex fallbacks

2. Socket.IO
   ✅ WebSocket wrapper
   ✅ Auto-reconnection
   ✅ Rooms & namespaces
   ✅ Fallback to polling
   ❌ Slightly more overhead

3. Server-Sent Events (SSE)
   ✅ Simple HTTP
   ✅ Auto-reconnect
   ✅ Event types
   ❌ One-way (server → client)
   ❌ No binary

4. Long Polling
   ✅ Works everywhere
   ✅ Simple
   ❌ High latency
   ❌ Server overhead
   ❌ Not true real-time

5. WebRTC
   ✅ Peer-to-peer
   ✅ Audio/video
   ✅ Data channels
   ❌ Complex setup
   ❌ Browser support varies
*/
```

---

<div align="center">

## 🔌 Socket.IO

</div>

### The Complete Real-time Framework 🚀

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

# Server
npm install socket.io
npm install @socket.io/redis-adapter redis

# Client
npm install socket.io-client
```

```javascript
// ═══════════════════════════════════════════
// Basic Server Setup
// ═══════════════════════════════════════════

import express from "express";
import { createServer } from "http";
import { Server } from "socket.io";

const app = express();
const server = createServer(app);

const io = new Server(server, {
  cors: {
    origin: process.env.CLIENT_URL || "http://localhost:3000",
    credentials: true,
    methods: ["GET", "POST"],
  },
  // Connection settings
  pingTimeout: 60000,
  pingInterval: 25000,
  // Upgrade settings
  transports: ["websocket", "polling"],
  allowEIO3: true,
});

// Basic connection
io.on("connection", (socket) => {
  console.log("Client connected:", socket.id);

  socket.on("disconnect", (reason) => {
    console.log("Client disconnected:", socket.id, reason);
  });
});

server.listen(3000, () => {
  console.log("🔌 Server running on port 3000");
});

// ═══════════════════════════════════════════
// Authentication Middleware
// ═══════════════════════════════════════════

import jwt from "jsonwebtoken";

io.use(async (socket, next) => {
  try {
    // Extract token from handshake
    const token =
      socket.handshake.auth.token ||
      socket.handshake.headers.authorization?.replace("Bearer ", "");

    if (!token) {
      return next(new Error("Authentication required"));
    }

    // Verify JWT
    const decoded = jwt.verify(token, process.env.JWT_SECRET);

    // Load user
    const user = await db.user.findUnique({
      where: { id: decoded.id },
      select: {
        id: true,
        name: true,
        email: true,
        avatar: true,
        role: true,
      },
    });

    if (!user) {
      return next(new Error("User not found"));
    }

    // Attach user to socket
    socket.userId = user.id;
    socket.user = user;

    next();
  } catch (error) {
    next(new Error("Invalid token"));
  }
});

// ═══════════════════════════════════════════
// Complete Chat Application
// ═══════════════════════════════════════════

io.on("connection", (socket) => {
  console.log(`✅ ${socket.user.name} connected (${socket.id})`);

  // Join user to personal room
  socket.join(`user:${socket.userId}`);

  // Update online status
  socket.broadcast.emit("user:online", {
    userId: socket.userId,
    name: socket.user.name,
  });

  // ═══════════════════════════════════════════
  // Room Management
  // ═══════════════════════════════════════════

  socket.on("room:join", async ({ roomId }) => {
    try {
      // Verify access
      const room = await db.room.findFirst({
        where: {
          id: roomId,
          members: {
            some: { userId: socket.userId },
          },
        },
        include: {
          members: {
            include: {
              user: {
                select: {
                  id: true,
                  name: true,
                  avatar: true,
                },
              },
            },
          },
        },
      });

      if (!room) {
        return socket.emit("error", {
          message: "Room not found or access denied",
          code: "ROOM_ACCESS_DENIED",
        });
      }

      // Join room
      socket.join(`room:${roomId}`);

      // Get recent messages
      const messages = await db.message.findMany({
        where: { roomId },
        include: {
          sender: {
            select: {
              id: true,
              name: true,
              avatar: true,
            },
          },
        },
        orderBy: { createdAt: "desc" },
        take: 50,
      });

      // Send to user
      socket.emit("room:joined", {
        room,
        messages: messages.reverse(),
      });

      // Notify others
      socket.to(`room:${roomId}`).emit("user:joined:room", {
        roomId,
        user: socket.user,
      });

      console.log(`${socket.user.name} joined room ${room.name}`);
    } catch (error) {
      console.error("Room join error:", error);
      socket.emit("error", {
        message: "Failed to join room",
        code: "ROOM_JOIN_ERROR",
      });
    }
  });

  socket.on("room:leave", ({ roomId }) => {
    socket.leave(`room:${roomId}`);

    socket.to(`room:${roomId}`).emit("user:left:room", {
      roomId,
      userId: socket.userId,
    });
  });

  // ═══════════════════════════════════════════
  // Messaging
  // ═══════════════════════════════════════════

  socket.on("message:send", async ({ roomId, content, type = "text" }) => {
    try {
      // Validate
      if (!content || content.trim().length === 0) {
        return socket.emit("error", {
          message: "Message cannot be empty",
          code: "EMPTY_MESSAGE",
        });
      }

      // Create message
      const message = await db.message.create({
        data: {
          roomId,
          senderId: socket.userId,
          content: content.trim(),
          type,
        },
        include: {
          sender: {
            select: {
              id: true,
              name: true,
              avatar: true,
            },
          },
        },
      });

      // Broadcast to room
      io.to(`room:${roomId}`).emit("message:new", message);

      // Update room's last activity
      await db.room.update({
        where: { id: roomId },
        data: {
          lastMessageAt: new Date(),
          lastMessageId: message.id,
        },
      });

      // Send push notifications to offline members
      const offlineMembers = await getOfflineRoomMembers(roomId);
      offlineMembers.forEach((member) => {
        sendPushNotification(member, {
          title: socket.user.name,
          body: content,
          roomId,
        });
      });
    } catch (error) {
      console.error("Message send error:", error);
      socket.emit("error", {
        message: "Failed to send message",
        code: "MESSAGE_SEND_ERROR",
      });
    }
  });

  // ═══════════════════════════════════════════
  // Typing Indicators
  // ═══════════════════════════════════════════

  const typingTimers = new Map();

  socket.on("typing:start", ({ roomId }) => {
    // Clear existing timer
    if (typingTimers.has(roomId)) {
      clearTimeout(typingTimers.get(roomId));
    }

    // Broadcast typing status
    socket.to(`room:${roomId}`).emit("user:typing", {
      roomId,
      userId: socket.userId,
      userName: socket.user.name,
    });

    // Auto-stop after 3 seconds
    const timer = setTimeout(() => {
      socket.to(`room:${roomId}`).emit("user:stopped-typing", {
        roomId,
        userId: socket.userId,
      });
      typingTimers.delete(roomId);
    }, 3000);

    typingTimers.set(roomId, timer);
  });

  socket.on("typing:stop", ({ roomId }) => {
    if (typingTimers.has(roomId)) {
      clearTimeout(typingTimers.get(roomId));
      typingTimers.delete(roomId);
    }

    socket.to(`room:${roomId}`).emit("user:stopped-typing", {
      roomId,
      userId: socket.userId,
    });
  });

  // ═══════════════════════════════════════════
  // Direct Messages
  // ═══════════════════════════════════════════

  socket.on("dm:send", async ({ recipientId, content }) => {
    try {
      const message = await db.directMessage.create({
        data: {
          senderId: socket.userId,
          recipientId,
          content,
        },
        include: {
          sender: {
            select: {
              id: true,
              name: true,
              avatar: true,
            },
          },
        },
      });

      // Send to recipient if online
      io.to(`user:${recipientId}`).emit("dm:received", message);

      // Confirm to sender
      socket.emit("dm:sent", message);

      // Push notification if offline
      const recipient = await db.user.findUnique({
        where: { id: recipientId },
      });

      if (!isUserOnline(recipientId)) {
        sendPushNotification(recipient, {
          title: `New message from ${socket.user.name}`,
          body: content,
        });
      }
    } catch (error) {
      socket.emit("error", {
        message: "Failed to send DM",
        code: "DM_SEND_ERROR",
      });
    }
  });

  // ═══════════════════════════════════════════
  // Presence & Status
  // ═══════════════════════════════════════════

  socket.on("presence:update", async ({ status }) => {
    try {
      // Validate status
      const validStatuses = ["online", "away", "busy", "offline"];
      if (!validStatuses.includes(status)) {
        return socket.emit("error", {
          message: "Invalid status",
          code: "INVALID_STATUS",
        });
      }

      // Update in database
      await db.user.update({
        where: { id: socket.userId },
        data: { presence: status },
      });

      // Get user's friends
      const friends = await db.friendship.findMany({
        where: {
          OR: [{ userId: socket.userId }, { friendId: socket.userId }],
          status: "accepted",
        },
      });

      // Notify friends
      friends.forEach((friendship) => {
        const friendId =
          friendship.userId === socket.userId
            ? friendship.friendId
            : friendship.userId;

        io.to(`user:${friendId}`).emit("friend:presence:changed", {
          userId: socket.userId,
          presence: status,
        });
      });
    } catch (error) {
      socket.emit("error", {
        message: "Failed to update presence",
        code: "PRESENCE_UPDATE_ERROR",
      });
    }
  });

  // ═══════════════════════════════════════════
  // Read Receipts
  // ═══════════════════════════════════════════

  socket.on("message:read", async ({ messageId, roomId }) => {
    try {
      await db.messageRead.create({
        data: {
          messageId,
          userId: socket.userId,
          readAt: new Date(),
        },
      });

      // Notify sender
      const message = await db.message.findUnique({
        where: { id: messageId },
        select: { senderId: true },
      });

      io.to(`user:${message.senderId}`).emit("message:read", {
        messageId,
        userId: socket.userId,
        readAt: new Date(),
      });
    } catch (error) {
      // Silently fail
    }
  });

  // ═══════════════════════════════════════════
  // Disconnect Handler
  // ═══════════════════════════════════════════

  socket.on("disconnect", async (reason) => {
    console.log(`❌ ${socket.user.name} disconnected: ${reason}`);

    // Clear typing timers
    typingTimers.forEach((timer) => clearTimeout(timer));
    typingTimers.clear();

    // Update last seen
    await db.user.update({
      where: { id: socket.userId },
      data: {
        lastSeen: new Date(),
        presence: "offline",
      },
    });

    // Notify others
    socket.broadcast.emit("user:offline", {
      userId: socket.userId,
      lastSeen: new Date(),
    });
  });

  // ═══════════════════════════════════════════
  // Error Handler
  // ═══════════════════════════════════════════

  socket.on("error", (error) => {
    console.error("Socket error:", error);
    socket.emit("error", {
      message: "An error occurred",
      code: "SOCKET_ERROR",
    });
  });
});

// ═══════════════════════════════════════════
// Helper Functions
// ═══════════════════════════════════════════

function isUserOnline(userId) {
  const sockets = io.sockets.sockets;
  for (const [, socket] of sockets) {
    if (socket.userId === userId) {
      return true;
    }
  }
  return false;
}

async function getOfflineRoomMembers(roomId) {
  const members = await db.roomMember.findMany({
    where: { roomId },
    include: { user: true },
  });

  return members
    .filter((member) => !isUserOnline(member.userId))
    .map((member) => member.user);
}
```

**📦 Socket.IO Resources:**

- Docs: https://socket.io/docs/v4/
- Client API: https://socket.io/docs/v4/client-api/
- Server API: https://socket.io/docs/v4/server-api/

> **💡 Pro Tip:** Socket.IO automatically handles reconnection, fallback to polling, and provides rooms for easy message broadcasting. Perfect for production apps!

### Client-Side Socket.IO 🖥️

```javascript
// ═══════════════════════════════════════════
// Socket.IO Client Setup
// ═══════════════════════════════════════════

import { io } from "socket.io-client";

class SocketService {
  constructor() {
    this.socket = null;
    this.listeners = new Map();
    this.reconnectAttempts = 0;
    this.maxReconnectAttempts = 5;
  }

  // ═══════════════════════════════════════════
  // Connection Management
  // ═══════════════════════════════════════════

  connect(token) {
    if (this.socket?.connected) {
      console.log("Already connected");
      return;
    }

    this.socket = io(process.env.SOCKET_URL || "http://localhost:3000", {
      auth: { token },
      reconnection: true,
      reconnectionDelay: 1000,
      reconnectionDelayMax: 5000,
      reconnectionAttempts: this.maxReconnectAttempts,
      timeout: 20000,
      transports: ["websocket", "polling"],
    });

    this.setupEventHandlers();
  }

  disconnect() {
    if (this.socket) {
      this.socket.disconnect();
      this.socket = null;
    }
  }

  // ═══════════════════════════════════════════
  // Event Handlers
  // ═══════════════════════════════════════════

  setupEventHandlers() {
    // Connection events
    this.socket.on("connect", () => {
      console.log("✅ Connected to server");
      this.reconnectAttempts = 0;
      this.emit("connection:established");
    });

    this.socket.on("disconnect", (reason) => {
      console.log("❌ Disconnected:", reason);
      this.emit("connection:lost", reason);

      if (reason === "io server disconnect") {
        // Server disconnected, manually reconnect
        this.socket.connect();
      }
    });

    this.socket.on("connect_error", (error) => {
      console.error("Connection error:", error);
      this.reconnectAttempts++;

      if (this.reconnectAttempts >= this.maxReconnectAttempts) {
        this.emit("connection:failed", error);
      }
    });

    this.socket.on("reconnect", (attemptNumber) => {
      console.log(`✅ Reconnected after ${attemptNumber} attempts`);
      this.emit("connection:restored");
    });

    this.socket.on("reconnect_attempt", (attemptNumber) => {
      console.log(`Reconnection attempt ${attemptNumber}...`);
      this.emit("connection:reconnecting", attemptNumber);
    });

    // Server events
    this.socket.on("error", (error) => {
      console.error("Socket error:", error);
      this.emit("error", error);
    });

    // Message events
    this.socket.on("message:new", (message) => {
      this.emit("message:received", message);
    });

    this.socket.on("dm:received", (message) => {
      this.emit("dm:received", message);
    });

    // User events
    this.socket.on("user:online", (data) => {
      this.emit("user:status", { ...data, status: "online" });
    });

    this.socket.on("user:offline", (data) => {
      this.emit("user:status", { ...data, status: "offline" });
    });

    this.socket.on("user:typing", (data) => {
      this.emit("typing:started", data);
    });

    this.socket.on("user:stopped-typing", (data) => {
      this.emit("typing:stopped", data);
    });

    // Room events
    this.socket.on("room:joined", (data) => {
      this.emit("room:joined", data);
    });

    this.socket.on("user:joined:room", (data) => {
      this.emit("user:joined:room", data);
    });
  }

  // ═══════════════════════════════════════════
  // Emit Events to Server
  // ═══════════════════════════════════════════

  joinRoom(roomId) {
    this.socket.emit("room:join", { roomId });
  }

  leaveRoom(roomId) {
    this.socket.emit("room:leave", { roomId });
  }

  sendMessage(roomId, content, type = "text") {
    this.socket.emit("message:send", { roomId, content, type });
  }

  sendDM(recipientId, content) {
    this.socket.emit("dm:send", { recipientId, content });
  }

  startTyping(roomId) {
    this.socket.emit("typing:start", { roomId });
  }

  stopTyping(roomId) {
    this.socket.emit("typing:stop", { roomId });
  }

  updatePresence(status) {
    this.socket.emit("presence:update", { status });
  }

  markAsRead(messageId, roomId) {
    this.socket.emit("message:read", { messageId, roomId });
  }

  // ═══════════════════════════════════════════
  // Event Listener Management
  // ═══════════════════════════════════════════

  on(event, callback) {
    if (!this.listeners.has(event)) {
      this.listeners.set(event, new Set());
    }
    this.listeners.get(event).add(callback);

    return () => this.off(event, callback);
  }

  off(event, callback) {
    const callbacks = this.listeners.get(event);
    if (callbacks) {
      callbacks.delete(callback);
    }
  }

  emit(event, data) {
    const callbacks = this.listeners.get(event);
    if (callbacks) {
      callbacks.forEach((callback) => callback(data));
    }
  }

  // ═══════════════════════════════════════════
  // Utility Methods
  // ═══════════════════════════════════════════

  isConnected() {
    return this.socket?.connected || false;
  }

  getSocketId() {
    return this.socket?.id;
  }
}

export const socketService = new SocketService();

// ═══════════════════════════════════════════
// React Hook for Socket.IO
// ═══════════════════════════════════════════

import { useEffect, useRef, useCallback } from "react";

export function useSocket(event, handler) {
  const handlerRef = useRef(handler);
  handlerRef.current = handler;

  useEffect(() => {
    const callback = (...args) => handlerRef.current(...args);
    const unsubscribe = socketService.on(event, callback);

    return unsubscribe;
  }, [event]);
}

export function useSocketConnection() {
  const [isConnected, setIsConnected] = useState(false);

  useSocket("connection:established", () => setIsConnected(true));
  useSocket("connection:lost", () => setIsConnected(false));
  useSocket("connection:restored", () => setIsConnected(true));

  return isConnected;
}

// ═══════════════════════════════════════════
// React Chat Component Example
// ═══════════════════════════════════════════

function ChatRoom({ roomId, currentUserId }) {
  const [messages, setMessages] = useState([]);
  const [typing, setTyping] = useState(new Map());
  const [inputValue, setInputValue] = useState("");
  const typingTimeoutRef = useRef(null);
  const isConnected = useSocketConnection();

  // Join room on mount
  useEffect(() => {
    if (isConnected && roomId) {
      socketService.joinRoom(roomId);
    }

    return () => {
      if (roomId) {
        socketService.leaveRoom(roomId);
      }
    };
  }, [roomId, isConnected]);

  // Listen for new messages
  useSocket("message:received", (message) => {
    if (message.roomId === roomId) {
      setMessages((prev) => [...prev, message]);

      // Mark as read if visible
      if (document.hasFocus()) {
        socketService.markAsRead(message.id, roomId);
      }
    }
  });

  // Listen for room joined (initial messages)
  useSocket("room:joined", ({ messages: initialMessages }) => {
    setMessages(initialMessages);
  });

  // Handle typing indicators
  useSocket("typing:started", ({ roomId: typingRoomId, userId, userName }) => {
    if (typingRoomId === roomId && userId !== currentUserId) {
      setTyping((prev) => new Map(prev).set(userId, userName));

      // Auto-clear after 3 seconds
      setTimeout(() => {
        setTyping((prev) => {
          const next = new Map(prev);
          next.delete(userId);
          return next;
        });
      }, 3000);
    }
  });

  useSocket("typing:stopped", ({ roomId: typingRoomId, userId }) => {
    if (typingRoomId === roomId) {
      setTyping((prev) => {
        const next = new Map(prev);
        next.delete(userId);
        return next;
      });
    }
  });

  // Handle input changes (typing indicator)
  const handleInputChange = (e) => {
    setInputValue(e.target.value);

    // Clear existing timeout
    if (typingTimeoutRef.current) {
      clearTimeout(typingTimeoutRef.current);
    }

    // Start typing
    if (e.target.value.length > 0) {
      socketService.startTyping(roomId);

      // Auto-stop after 3 seconds
      typingTimeoutRef.current = setTimeout(() => {
        socketService.stopTyping(roomId);
      }, 3000);
    } else {
      socketService.stopTyping(roomId);
    }
  };

  // Send message
  const handleSubmit = (e) => {
    e.preventDefault();

    if (inputValue.trim() && isConnected) {
      socketService.sendMessage(roomId, inputValue.trim());
      setInputValue("");
      socketService.stopTyping(roomId);

      if (typingTimeoutRef.current) {
        clearTimeout(typingTimeoutRef.current);
      }
    }
  };

  return (
    <div className="chat-room">
      {!isConnected && (
        <div className="connection-warning">Reconnecting...</div>
      )}

      <div className="messages">
        {messages.map((message) => (
          <div key={message.id} className="message">
            <img src={message.sender.avatar} alt={message.sender.name} />
            <div>
              <strong>{message.sender.name}</strong>
              <p>{message.content}</p>
              <small>{new Date(message.createdAt).toLocaleTimeString()}</small>
            </div>
          </div>
        ))}
      </div>

      {typing.size > 0 && (
        <div className="typing-indicator">
          {Array.from(typing.values()).join(", ")}{" "}
          {typing.size === 1 ? "is" : "are"} typing...
        </div>
      )}

      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={inputValue}
          onChange={handleInputChange}
          placeholder="Type a message..."
          disabled={!isConnected}
        />
        <button type="submit" disabled={!inputValue.trim() || !isConnected}>
          Send
        </button>
      </form>
    </div>
  );
}
```

---

<div align="center">

## ⚡ Native WebSockets

</div>

### Pure WebSocket API 🔌

```javascript
// ═══════════════════════════════════════════
// Server-Side (ws library)
// ═══════════════════════════════════════════

import { WebSocketServer } from "ws";
import { createServer } from "http";

const server = createServer();
const wss = new WebSocketServer({ server });

wss.on("connection", (ws, request) => {
  console.log("Client connected");

  // Parse client info
  const ip = request.socket.remoteAddress;
  const userAgent = request.headers["user-agent"];

  // Send welcome message
  ws.send(
    JSON.stringify({
      type: "welcome",
      message: "Connected to WebSocket server",
    })
  );

  // Handle messages
  ws.on("message", (data) => {
    try {
      const message = JSON.parse(data.toString());

      switch (message.type) {
        case "chat":
          // Broadcast to all clients
          wss.clients.forEach((client) => {
            if (client.readyState === WebSocket.OPEN) {
              client.send(
                JSON.stringify({
                  type: "chat",
                  user: message.user,
                  text: message.text,
                  timestamp: new Date(),
                })
              );
            }
          });
          break;

        case "ping":
          ws.send(JSON.stringify({ type: "pong" }));
          break;
      }
    } catch (error) {
      console.error("Message parse error:", error);
    }
  });

  // Handle errors
  ws.on("error", (error) => {
    console.error("WebSocket error:", error);
  });

  // Handle disconnect
  ws.on("close", () => {
    console.log("Client disconnected");
  });

  // Heartbeat (keep connection alive)
  ws.isAlive = true;
  ws.on("pong", () => {
    ws.isAlive = true;
  });
});

// Heartbeat interval
const interval = setInterval(() => {
  wss.clients.forEach((ws) => {
    if (ws.isAlive === false) {
      return ws.terminate();
    }

    ws.isAlive = false;
    ws.ping();
  });
}, 30000);

wss.on("close", () => {
  clearInterval(interval);
});

server.listen(3000);

// ═══════════════════════════════════════════
// Client-Side (Browser)
// ═══════════════════════════════════════════

class WebSocketClient {
  constructor(url) {
    this.url = url;
    this.ws = null;
    this.reconnectInterval = 1000;
    this.maxReconnectInterval = 30000;
    this.reconnectDecay = 1.5;
    this.listeners = new Map();
  }

  connect() {
    this.ws = new WebSocket(this.url);

    this.ws.onopen = () => {
      console.log("WebSocket connected");
      this.reconnectInterval = 1000;
      this.emit("open");
    };

    this.ws.onmessage = (event) => {
      try {
        const data = JSON.parse(event.data);
        this.emit("message", data);

        // Emit specific event type
        if (data.type) {
          this.emit(data.type, data);
        }
      } catch (error) {
        console.error("Message parse error:", error);
      }
    };

    this.ws.onerror = (error) => {
      console.error("WebSocket error:", error);
      this.emit("error", error);
    };

    this.ws.onclose = () => {
      console.log("WebSocket closed");
      this.emit("close");
      this.reconnect();
    };
  }

  reconnect() {
    setTimeout(() => {
      console.log("Reconnecting...");
      this.reconnectInterval = Math.min(
        this.reconnectInterval * this.reconnectDecay,
        this.maxReconnectInterval
      );
      this.connect();
    }, this.reconnectInterval);
  }

  send(type, data) {
    if (this.ws?.readyState === WebSocket.OPEN) {
      this.ws.send(JSON.stringify({ type, ...data }));
    } else {
      console.error("WebSocket not connected");
    }
  }

  on(event, callback) {
    if (!this.listeners.has(event)) {
      this.listeners.set(event, new Set());
    }
    this.listeners.get(event).add(callback);
  }

  off(event, callback) {
    this.listeners.get(event)?.delete(callback);
  }

  emit(event, data) {
    this.listeners.get(event)?.forEach((callback) => callback(data));
  }

  close() {
    this.ws?.close();
  }
}

// Usage
const ws = new WebSocketClient("ws://localhost:3000");
ws.connect();

ws.on("open", () => {
  ws.send("chat", { user: "MrDib", text: "Hello!" });
});

ws.on("chat", (message) => {
  console.log(`${message.user}: ${message.text}`);
});
```

---

<div align="center">

## 📡 Server-Sent Events

</div>

### One-Way Streaming 📤

```javascript
// ═══════════════════════════════════════════
// Server-Side (Express)
// ═══════════════════════════════════════════

import express from "express";

const app = express();

// SSE endpoint
app.get("/events", (req, res) => {
  // Set headers for SSE
  res.setHeader("Content-Type", "text/event-stream");
  res.setHeader("Cache-Control", "no-cache");
  res.setHeader("Connection", "keep-alive");

  // Send initial message
  res.write('data: {"type": "connected"}\n\n');

  // Send updates every 5 seconds
  const interval = setInterval(() => {
    res.write(
      `data: ${JSON.stringify({
        type: "update",
        time: new Date().toISOString(),
        data: Math.random(),
      })}\n\n`
    );
  }, 5000);

  // Cleanup on close
  req.on("close", () => {
    clearInterval(interval);
    res.end();
  });
});

// Send specific events
app.post("/broadcast", (req, res) => {
  // Broadcast to all SSE clients
  // (requires storing clients in memory/Redis)
  clients.forEach((client) => {
    client.write(`event: notification\ndata: ${JSON.stringify(req.body)}\n\n`);
  });

  res.json({ success: true });
});

// ═══════════════════════════════════════════
// Client-Side (Browser)
// ═══════════════════════════════════════════

const eventSource = new EventSource("/events");

eventSource.onopen = () => {
  console.log("SSE connection opened");
};

eventSource.onmessage = (event) => {
  const data = JSON.parse(event.data);
  console.log("Message:", data);
};

// Listen for specific events
eventSource.addEventListener("notification", (event) => {
  const data = JSON.parse(event.data);
  console.log("Notification:", data);
});

eventSource.onerror = (error) => {
  console.error("SSE error:", error);
};

// Close connection
eventSource.close();

// ═══════════════════════════════════════════
// React Hook for SSE
// ═══════════════════════════════════════════

function useServerSentEvents(url) {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    const eventSource = new EventSource(url);

    eventSource.onmessage = (event) => {
      setData(JSON.parse(event.data));
    };

    eventSource.onerror = (error) => {
      setError(error);
    };

    return () => eventSource.close();
  }, [url]);

  return { data, error };
}

// Usage
function LiveFeed() {
  const { data, error } = useServerSentEvents("/api/feed");

  if (error) return <div>Error: {error.message}</div>;
  if (!data) return <div>Loading...</div>;

  return <div>{JSON.stringify(data)}</div>;
}
```

---

<div align="center">

## 🚀 Scaling WebSockets

</div>

### Production-Ready Scaling 🏭

```bash
# ═══════════════════════════════════════════
# Installation
# ═══════════════════════════════════════════

npm install @socket.io/redis-adapter redis ioredis
npm install @socket.io/sticky
```

```javascript
// ═══════════════════════════════════════════
// Redis Adapter for Horizontal Scaling
// ═══════════════════════════════════════════

import { Server } from "socket.io";
import { createAdapter } from "@socket.io/redis-adapter";
import { createClient } from "redis";

// Create Redis clients
const pubClient = createClient({
  url: process.env.REDIS_URL || "redis://localhost:6379",
});

const subClient = pubClient.duplicate();

// Connect clients
await Promise.all([pubClient.connect(), subClient.connect()]);

// Apply adapter to Socket.IO
io.adapter(createAdapter(pubClient, subClient));

console.log("✅ Redis adapter connected");

// Now you can scale horizontally!
// All Socket.IO instances will communicate through Redis

// ═══════════════════════════════════════════
// Sticky Sessions with Load Balancer
// ═══════════════════════════════════════════

import { createServer } from "http";
import { setupMaster, setupWorker } from "@socket.io/sticky";
import cluster from "cluster";
import { cpus } from "os";

const WORKERS = cpus().length;

if (cluster.isMaster) {
  console.log(`Master ${process.pid} is running`);

  // Create HTTP server for sticky sessions
  const httpServer = createServer();

  // Setup master
  setupMaster(httpServer, {
    loadBalancingMethod: "least-connection",
  });

  httpServer.listen(3000);

  // Fork workers
  for (let i = 0; i < WORKERS; i++) {
    cluster.fork();
  }

  cluster.on("exit", (worker) => {
    console.log(`Worker ${worker.process.pid} died`);
    cluster.fork();
  });
} else {
  console.log(`Worker ${process.pid} started`);

  const httpServer = createServer();
  const io = new Server(httpServer);

  // Apply Redis adapter
  io.adapter(createAdapter(pubClient, subClient));

  // Setup worker
  setupWorker(io);

  // Your Socket.IO logic here
  io.on("connection", (socket) => {
    console.log("Client connected to worker", process.pid);
  });
}

// ═══════════════════════════════════════════
// Nginx Configuration for WebSocket
// ═══════════════════════════════════════════

/*
# nginx.conf

upstream socket_nodes {
    ip_hash;  # Sticky sessions
    server 127.0.0.1:3000;
    server 127.0.0.1:3001;
    server 127.0.0.1:3002;
}

server {
    listen 80;
    server_name example.com;

    location /socket.io/ {
        proxy_pass http://socket_nodes;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;

        # Timeouts
        proxy_connect_timeout 7d;
        proxy_send_timeout 7d;
        proxy_read_timeout 7d;
    }
}
*/

// ═══════════════════════════════════════════
// PM2 Cluster Mode
// ═══════════════════════════════════════════

// ecosystem.config.js
module.exports = {
  apps: [
    {
      name: "websocket-server",
      script: "./server.js",
      instances: "max",
      exec_mode: "cluster",
      env: {
        NODE_ENV: "production",
        PORT: 3000,
        REDIS_URL: "redis://localhost:6379",
      },
    },
  ],
};

// Start with PM2
// pm2 start ecosystem.config.js

// ═══════════════════════════════════════════
// Connection Limits & Rate Limiting
// ═══════════════════════════════════════════

import rateLimit from "express-rate-limit";

// Rate limit for HTTP endpoints
const apiLimiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 100,
});

app.use("/api/", apiLimiter);

// Connection rate limiting for Socket.IO
const connectionAttempts = new Map();

io.use((socket, next) => {
  const ip = socket.handshake.address;
  const now = Date.now();

  if (!connectionAttempts.has(ip)) {
    connectionAttempts.set(ip, []);
  }

  const attempts = connectionAttempts.get(ip);

  // Remove old attempts (older than 1 minute)
  const recentAttempts = attempts.filter((time) => now - time < 60000);

  // Allow max 10 connections per minute per IP
  if (recentAttempts.length >= 10) {
    return next(new Error("Too many connection attempts"));
  }

  recentAttempts.push(now);
  connectionAttempts.set(ip, recentAttempts);

  next();
});

// ═══════════════════════════════════════════
// Message Queue for Persistence
// ═══════════════════════════════════════════

import { Queue } from "bullmq";

const messageQueue = new Queue("messages", {
  connection: {
    host: process.env.REDIS_HOST,
    port: process.env.REDIS_PORT,
  },
});

// Queue message for processing
io.on("connection", (socket) => {
  socket.on("message:send", async (data) => {
    // Add to queue
    await messageQueue.add("process-message", {
      userId: socket.userId,
      roomId: data.roomId,
      content: data.content,
      timestamp: new Date(),
    });

    // Acknowledge immediately
    socket.emit("message:queued", { id: data.tempId });
  });
});

// Process messages in background
import { Worker } from "bullmq";

const worker = new Worker(
  "messages",
  async (job) => {
    const { userId, roomId, content, timestamp } = job.data;

    // Save to database
    const message = await db.message.create({
      data: { userId, roomId, content, timestamp },
    });

    // Broadcast via Socket.IO
    io.to(`room:${roomId}`).emit("message:new", message);
  },
  {
    connection: {
      host: process.env.REDIS_HOST,
      port: process.env.REDIS_PORT,
    },
  }
);
```

---

<div align="center">

## 🔐 Security

</div>

### Securing WebSocket Connections 🛡️

```javascript
// ═══════════════════════════════════════════
// 1. Authentication & Authorization
// ═══════════════════════════════════════════

import jwt from "jsonwebtoken";

// JWT authentication middleware
io.use(async (socket, next) => {
  try {
    const token = socket.handshake.auth.token;

    if (!token) {
      return next(new Error("Authentication required"));
    }

    const decoded = jwt.verify(token, process.env.JWT_SECRET);

    // Check token expiry
    if (decoded.exp && decoded.exp < Date.now() / 1000) {
      return next(new Error("Token expired"));
    }

    // Load user
    const user = await db.user.findUnique({
      where: { id: decoded.id },
    });

    if (!user || !user.active) {
      return next(new Error("User not found or inactive"));
    }

    socket.userId = user.id;
    socket.user = user;

    next();
  } catch (error) {
    next(new Error("Invalid token"));
  }
});

// Room access control
socket.on("room:join", async ({ roomId }) => {
  const hasAccess = await db.roomMember.findFirst({
    where: {
      roomId,
      userId: socket.userId,
      status: "active",
    },
  });

  if (!hasAccess) {
    return socket.emit("error", {
      message: "Access denied",
      code: "ROOM_ACCESS_DENIED",
    });
  }

  socket.join(`room:${roomId}`);
});

// ═══════════════════════════════════════════
// 2. Input Validation & Sanitization
// ═══════════════════════════════════════════

import { z } from "zod";
import DOMPurify from "isomorphic-dompurify";

const messageSchema = z.object({
  roomId: z.string().uuid(),
  content: z.string().min(1).max(5000),
  type: z.enum(["text", "image", "file"]).default("text"),
});

socket.on("message:send", async (data) => {
  try {
    // Validate schema
    const validated = messageSchema.parse(data);

    // Sanitize content (prevent XSS)
    const sanitized = DOMPurify.sanitize(validated.content, {
      ALLOWED_TAGS: ["b", "i", "em", "strong", "a"],
      ALLOWED_ATTR: ["href"],
    });

    // Check content length
    if (sanitized.length > 5000) {
      return socket.emit("error", {
        message: "Message too long",
        code: "MESSAGE_TOO_LONG",
      });
    }

    // Process message...
  } catch (error) {
    socket.emit("error", {
      message: "Invalid message format",
      code: "VALIDATION_ERROR",
    });
  }
});

// ═══════════════════════════════════════════
// 3. Rate Limiting Per User
// ═══════════════════════════════════════════

const userRateLimits = new Map();

function checkRateLimit(userId, action, limit = 10, windowMs = 60000) {
  const key = `${userId}:${action}`;
  const now = Date.now();

  if (!userRateLimits.has(key)) {
    userRateLimits.set(key, []);
  }

  const attempts = userRateLimits.get(key);
  const recentAttempts = attempts.filter((time) => now - time < windowMs);

  if (recentAttempts.length >= limit) {
    return false;
  }

  recentAttempts.push(now);
  userRateLimits.set(key, recentAttempts);

  return true;
}

socket.on("message:send", async (data) => {
  // Check rate limit: max 10 messages per minute
  if (!checkRateLimit(socket.userId, "message", 10, 60000)) {
    return socket.emit("error", {
      message: "Too many messages. Please slow down.",
      code: "RATE_LIMIT_EXCEEDED",
    });
  }

  // Process message...
});

// ═══════════════════════════════════════════
// 4. CORS Configuration
// ═══════════════════════════════════════════

const io = new Server(server, {
  cors: {
    origin: (origin, callback) => {
      const allowedOrigins = process.env.ALLOWED_ORIGINS?.split(",") || [];

      if (!origin || allowedOrigins.includes(origin)) {
        callback(null, true);
      } else {
        callback(new Error("Not allowed by CORS"));
      }
    },
    credentials: true,
    methods: ["GET", "POST"],
  },
});

// ═══════════════════════════════════════════
// 5. Prevent Socket Hijacking
// ═══════════════════════════════════════════

io.use((socket, next) => {
  // Store connection metadata
  socket.metadata = {
    ip: socket.handshake.address,
    userAgent: socket.handshake.headers["user-agent"],
    connectedAt: new Date(),
  };

  next();
});

// Verify socket ownership
socket.on("sensitive:action", async (data) => {
  // Re-verify token for sensitive operations
  const token = socket.handshake.auth.token;

  try {
    jwt.verify(token, process.env.JWT_SECRET);
  } catch (error) {
    socket.disconnect(true);
    return;
  }

  // Process action...
});

// ═══════════════════════════════════════════
// 6. Encrypt Sensitive Data
// ═══════════════════════════════════════════

import crypto from "crypto";

function encryptMessage(text, key) {
  const iv = crypto.randomBytes(16);
  const cipher = crypto.createCipheriv(
    "aes-256-cbc",
    Buffer.from(key, "hex"),
    iv
  );

  let encrypted = cipher.update(text, "utf8", "hex");
  encrypted += cipher.final("hex");

  return iv.toString("hex") + ":" + encrypted;
}

function decryptMessage(encrypted, key) {
  const parts = encrypted.split(":");
  const iv = Buffer.from(parts.shift(), "hex");
  const encryptedText = parts.join(":");

  const decipher = crypto.createDecipheriv(
    "aes-256-cbc",
    Buffer.from(key, "hex"),
    iv
  );

  let decrypted = decipher.update(encryptedText, "hex", "utf8");
  decrypted += decipher.final("utf8");

  return decrypted;
}

// Use for sensitive messages
socket.on("secure:message", async (data) => {
  const encrypted = encryptMessage(data.content, process.env.ENCRYPTION_KEY);

  await db.message.create({
    data: {
      ...data,
      content: encrypted,
      encrypted: true,
    },
  });
});
```

---

<div align="center">

## 💡 Best Practices

</div>

### WebSocket Development Guidelines ⭐

````javascript
// ═══════════════════════════════════════════
// 1. Connection Management
// ═══════════════════════════════════════════

/*
✅ DO:
- Implement exponential backoff for reconnection
- Use heartbeats/ping-pong to keep connections alive
- Handle disconnect gracefully
- Store connection state
- Limit connections per user
- Clean up resources on disconnect

❌ DON'T:
- Create new connections unnecessarily
- Forget to close connections
- Block event loop with heavy operations
- Store large data in socket objects
*/

// Good connection handling
class SocketManager {
  constructor() {
    this.connections = new Map();
    this.setupCleanup();
  }

  addConnection(userId, socket) {
    if (this.connections.has(userId)) {
      // Disconnect old connection
      this.connections.get(userId).disconnect();
    }

    this.connections.set(userId, socket);

    socket.on('disconnect', () => {
      this.connections.delete(userId);
    });
  }

  setupCleanup() {
    // Periodic cleanup of stale connections
    setInterval(() => {
      this.connections.forEach((socket, userId) => {
        if (!socket.connected) {
          this.connections.delete(userId);
        }
      });
    }, 60000);
  }
}

// ═══════════════════════════════════════════
// 2. Error Handling
// ═══════════════════════════════════════════

// ✅ GOOD: Comprehensive error handling
io.on('connection', (socket) => {
  socket.on('error', (error) => {
    console.error('Socket error:', error);
    socket.emit('error', {
      message: 'An error occurred',
      code: 'SOCKET_ERROR',
    });
  });

  socket.on('message:send', async (data) => {
    try {
      await processMessage(data);
    } catch (error) {
      console.error('Message processing error:', error);
      socket.emit('error', {
        message: 'Failed to send message',
        code: 'MESSAGE_ERROR',
      });
    }
  });
});

// ❌ BAD: Unhandled errors crash the server
socket.on('message:send', async (data) => {
  await processMessage(data); // Can throw!
});

// ═══════════════════════════════════════════
// 3. Event Naming Conventions
// ═══════════════════════════════════════════

/*
✅ GOOD: Consistent, descriptive names
- user:join
- user:leave
- message:send
- message:received
- room:create
- typing:start
- typing:stop

❌ BAD: Inconsistent names
- joinUser
- userLeft
- sendMsg
- msgReceived
*/

// ═══════════════════════════════════════════
// 4. Acknowledgments
// ═══════════════════════════════════════════

// ✅ GOOD: Use acknowledgments for critical events
socket.on('message:send', async (data, callback) => {
  try {
    const message = await createMessage(data);
    callback({ success: true, message });
  } catch (error) {
    callback({ success: false, error: error.message });
  }
});

// Client side
socket.emit('message:send', data, (response) => {
  if (response.success) {
    console.log('Message sent:', response.message);
  } else {
    console.error('Message failed:', response.error);
}
});

// ═══════════════════════════════════════════
// 5. Memory Management
// ═══════════════════════════════════════════

// ✅ GOOD: Clean up listeners and timers
socket.on('disconnect', () => {
// Clear all timers
if (socket.typingTimer) {
clearTimeout(socket.typingTimer);
}

// Remove from tracking
onlineUsers.delete(socket.userId);

// Clear custom data
delete socket.customData;
});

// Use WeakMaps for temporary data
const socketData = new WeakMap();

io.on('connection', (socket) => {
socketData.set(socket, {
joinedAt: new Date(),
messages: 0,
});
});

// ═══════════════════════════════════════════
// 6. Performance Optimization
// ═══════════════════════════════════════════

// ✅ GOOD: Batch notifications
const pendingNotifications = new Map();

function queueNotification(userId, notification) {
if (!pendingNotifications.has(userId)) {
pendingNotifications.set(userId, []);

    // Send batch after 100ms
    setTimeout(() => {
      const notifications = pendingNotifications.get(userId);
      if (notifications && notifications.length > 0) {
        io.to(`user:${userId}`).emit('notifications:batch', notifications);
        pendingNotifications.delete(userId);
      }
    }, 100);

}

pendingNotifications.get(userId).push(notification);
}

// ✅ GOOD: Use rooms efficiently
// Instead of iterating all sockets
io.sockets.sockets.forEach(socket => {
if (socket.userId === targetUserId) {
socket.emit('notification', data);
}
});

// Do this:
io.to(`user:${targetUserId}`).emit('notification', data);

// ═══════════════════════════════════════════
// 7. Testing WebSockets
// ═══════════════════════════════════════════

import { io as Client } from 'socket.io-client';

describe('WebSocket Chat', () => {
let server;
let clientSocket;

beforeAll((done) => {
server = createServer();
server.listen(0, () => {
const port = server.address().port;
clientSocket = Client(`http://localhost:${port}`, {
auth: { token: 'valid-token' },
});
clientSocket.on('connect', done);
});
});

afterAll(() => {
clientSocket.disconnect();
server.close();
});

test('should receive message', (done) => {
clientSocket.on('message:new', (message) => {
expect(message).toHaveProperty('content');
done();
});

    clientSocket.emit('message:send', {
      roomId: 'test-room',
      content: 'Hello!',
    });

});

test('should handle acknowledgment', (done) => {
clientSocket.emit('message:send', {
roomId: 'test-room',
content: 'Test',
}, (response) => {
expect(response.success).toBe(true);
done();
});
});
});

// ═══════════════════════════════════════════
// 8. Logging & Monitoring
// ═══════════════════════════════════════════

// Connection logging
io.on('connection', (socket) => {
console.log('Connection', {
socketId: socket.id,
userId: socket.userId,
ip: socket.handshake.address,
timestamp: new Date().toISOString(),
});
});

// Event logging
socket.on('message:send', async (data) => {
const start = Date.now();

try {
await processMessage(data);

    console.log('Message processed', {
      userId: socket.userId,
      duration: Date.now() - start,
      success: true,
    });

} catch (error) {
console.error('Message failed', {
userId: socket.userId,
duration: Date.now() - start,
error: error.message,
});
}
});

// Metrics tracking
const metrics = {
connections: 0,
messagesPerSecond: 0,
errors: 0,
};

setInterval(() => {
metrics.connections = io.engine.clientsCount;

// Send to monitoring service
sendMetrics(metrics);

// Reset counters
metrics.messagesPerSecond = 0;
metrics.errors = 0;
}, 1000);

// ═══════════════════════════════════════════
// 9. Graceful Shutdown
// ═══════════════════════════════════════════

process.on('SIGTERM', async () => {
console.log('SIGTERM received, closing connections...');

// Stop accepting new connections
server.close(() => {
console.log('HTTP server closed');
});

// Notify all clients
io.emit('server:shutdown', {
message: 'Server is shutting down',
reconnect: true,
});

// Close all socket connections
io.close(() => {
console.log('All connections closed');
});

// Wait for pending operations
setTimeout(() => {
process.exit(0);
}, 5000);
});

// ═══════════════════════════════════════════
// 10. Documentation
// ═══════════════════════════════════════════

/\*
Document your WebSocket events:

# WebSocket Events

## Client → Server

### `message:send`

Send a message to a room.

**Payload:**

```json
{
  "roomId": "string",
  "content": "string",
  "type": "text" | "image" | "file"
}
```

**Response (acknowledgment):**

```json
{
  "success": boolean,
  "message": Message | null,
  "error": string | null
}
```

## Server → Client

### `message:new`

New message received in a room.

**Payload:**

```json
{
  "id": "string",
  "roomId": "string",
  "sender": {
    "id": "string",
    "name": "string",
    "avatar": "string"
  },
  "content": "string",
  "type": "text",
  "createdAt": "ISO8601"
}
```

\*/

````

---

### Quick Reference 📋

```javascript
// ═══════════════════════════════════════════
// Socket.IO Cheat Sheet
// ═══════════════════════════════════════════

// Server-Side
io.on("connection", (socket) => {}); // Handle connection
socket.emit("event", data); // Send to this socket
socket.broadcast.emit("event", data); // Send to all except sender
io.emit("event", data); // Send to all
socket.to("room").emit("event", data); // Send to specific room
io.to("room").emit("event", data); // Send to room from server
socket.join("room"); // Join room
socket.leave("room"); // Leave room
socket.rooms; // Get joined rooms
socket.disconnect(); // Disconnect socket
io.close(); // Close server

// Client-Side
socket.connect(); // Connect to server
socket.disconnect(); // Disconnect from server
socket.emit("event", data); // Send event
socket.on("event", callback); // Listen for event
socket.off("event", callback); // Remove listener
socket.once("event", callback); // Listen once
socket.connected; // Connection status
socket.id; // Socket ID

// Events
connect; // Connected
disconnect; // Disconnected
connect_error; // Connection error
reconnect; // Reconnected
reconnect_attempt; // Attempting reconnect
reconnect_error; // Reconnection error
```

---

<div align="center">

## 🎯 Common Use Cases

</div>

### Real-world Applications 💼

```javascript
// ═══════════════════════════════════════════
// 1. Real-time Notifications
// ═══════════════════════════════════════════

async function sendNotification(userId, notification) {
  // Save to database
  await db.notification.create({
    data: {
      userId,
      type: notification.type,
      title: notification.title,
      message: notification.message,
    },
  });

  // Send via WebSocket if online
  io.to(`user:${userId}`).emit("notification", notification);

  // Send push notification if offline
  if (!isUserOnline(userId)) {
    await sendPushNotification(userId, notification);
  }
}

// ═══════════════════════════════════════════
// 2. Live Dashboard Updates
// ═══════════════════════════════════════════

setInterval(async () => {
  const stats = await getSystemStats();

  // Broadcast to all connected dashboards
  io.to("dashboard").emit("stats:update", {
    cpu: stats.cpu,
    memory: stats.memory,
    requests: stats.requests,
    timestamp: new Date(),
  });
}, 5000);

// ═══════════════════════════════════════════
// 3. Collaborative Editing
// ═══════════════════════════════════════════

socket.on("document:edit", async ({ documentId, changes }) => {
  // Apply changes to document
  await applyChanges(documentId, changes);

  // Broadcast to all editors except sender
  socket.to(`doc:${documentId}`).emit("document:changed", {
    changes,
    userId: socket.userId,
    timestamp: new Date(),
  });
});

// ═══════════════════════════════════════════
// 4. Live Cursor Tracking
// ═══════════════════════════════════════════

socket.on("cursor:move", ({ documentId, position }) => {
  socket.to(`doc:${documentId}`).emit("cursor:update", {
    userId: socket.userId,
    userName: socket.user.name,
    position,
  });
});

// ═══════════════════════════════════════════
// 5. Online Status Tracking
// ═══════════════════════════════════════════

const onlineUsers = new Set();

io.on("connection", (socket) => {
  onlineUsers.add(socket.userId);

  // Broadcast user came online
  socket.broadcast.emit("user:online", {
    userId: socket.userId,
  });

  socket.on("disconnect", () => {
    onlineUsers.delete(socket.userId);

    socket.broadcast.emit("user:offline", {
      userId: socket.userId,
      lastSeen: new Date(),
    });
  });
});

// ═══════════════════════════════════════════
// 6. Live Sports Scores
// ═══════════════════════════════════════════

async function updateScore(matchId, newScore) {
  await db.match.update({
    where: { id: matchId },
    data: { score: newScore },
  });

  io.to(`match:${matchId}`).emit("score:update", {
    matchId,
    score: newScore,
    timestamp: new Date(),
  });
}
```

---

<div align="center">

**Built with 🔌 by MrDib, for Real-time Developers**

_"Real-time isn't just fast - it's instant!"_

**Happy Building!** ⚡

**If you found this helpful, give it a ⭐ star and share with fellow developers!**

</div>

---

### Contributing 🤝

Found better WebSocket patterns? Want to add examples? Contributions are welcome!

1. Fork the repository
2. Add your WebSocket examples
3. Update best practices
4. Submit a pull request

---

### License 📄

This guide is open source and available under the MIT License.

---

<div align="center">

**Stay connected. Keep building. Ship real-time!** 💪✨

🔌 **#WebSockets** 🔌 **#DevResourceVault** 🔌 **#MrDib** 🔌

### Remember

> _"WebSockets: Because polling is so 2010"_

> _"Always authenticate, always validate"_

> _"Scale horizontally with Redis adapter"_

> _"Handle disconnects gracefully"_

> _"Real-time is a feature, not a bug"_

</div>

---

<div align="center">

**Now go forth and build amazing real-time applications!** 🌟🔌

</div>
