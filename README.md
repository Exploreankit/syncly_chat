# Syncly — Real-time Chat App

A full-stack real-time chat application built with React, Node.js, Socket.IO, and MongoDB.
**Chat · Connect · Sync**

## Features

- **Real-time messaging** via Socket.IO
- **1-on-1 and group chats**
- **Typing indicators**
- **Read receipts** (double blue ticks)
- **Message reactions** (emoji reactions)
- **Reply to messages**
- **Delete messages**
- **Online/offline presence**
- **User search**
- **JWT authentication**
- **Profile editing**
- **WhatsApp Web-inspired dark UI**

## Tech Stack

| Layer     | Tech                          |
|-----------|-------------------------------|
| Frontend  | React + Vite + TypeScript     |
| Styling   | Tailwind CSS v4               |
| State     | Zustand                       |
| Backend   | Node.js + Express             |
| Database  | MongoDB + Mongoose            |
| Realtime  | Socket.IO                     |
| Auth      | JWT + bcryptjs                |

## Project Structure

```
chat-app/
├── server/
│   ├── models/          # Mongoose models (User, Conversation, Message)
│   ├── routes/          # REST API routes
│   ├── middleware/       # JWT auth middleware
│   ├── socket/          # Socket.IO event handlers
│   └── index.js         # Entry point
├── client/
│   └── src/
│       ├── components/  # React components
│       ├── store/       # Zustand stores
│       ├── hooks/       # Custom hooks
│       ├── lib/         # API client + socket
│       └── types/       # TypeScript types
├── .env                 # Environment variables
└── package.json
```

## Getting Started

### Prerequisites
- Node.js 18+
- MongoDB (local or Atlas)

### 1. Configure environment

Edit `.env` in the root:
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/chatapp
JWT_SECRET=your_super_secret_key_here
CLIENT_URL=http://localhost:5173
```

### 2. Start the backend

```bash
npm run dev
```

### 3. Start the frontend

```bash
cd client
npm run dev
```

Open [http://localhost:5173](http://localhost:5173)

## API Endpoints

| Method | Path                              | Description              |
|--------|-----------------------------------|--------------------------|
| POST   | /api/auth/register                | Register                 |
| POST   | /api/auth/login                   | Login                    |
| GET    | /api/auth/me                      | Get current user         |
| PUT    | /api/auth/profile                 | Update profile           |
| GET    | /api/users/search?q=              | Search users             |
| GET    | /api/conversations                | Get all conversations    |
| POST   | /api/conversations                | Create/get DM            |
| POST   | /api/conversations/group          | Create group             |
| GET    | /api/messages/:conversationId     | Get messages             |
| POST   | /api/messages/:conversationId     | Send message (REST)      |
| DELETE | /api/messages/:messageId          | Delete message           |
| POST   | /api/messages/:messageId/react    | React to message         |

## Socket Events

| Event            | Direction       | Description              |
|------------------|-----------------|--------------------------|
| message:send     | client → server | Send a message           |
| message:new      | server → client | New message received     |
| message:delete   | client → server | Delete a message         |
| message:deleted  | server → client | Message was deleted      |
| message:react    | client → server | Add/toggle reaction      |
| message:reacted  | server → client | Reactions updated        |
| typing:start     | client → server | User started typing      |
| typing:stop      | client → server | User stopped typing      |
| messages:read    | client → server | Mark messages as read    |
| user:online      | server → client | User came online         |
| user:offline     | server → client | User went offline        |
