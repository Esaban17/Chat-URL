# Chat-URL

A full-stack social networking and real-time messaging application built with the MERN stack (MongoDB, Express, React, Node.js) and Socket.IO.

## Features

- **Authentication** - Sign up and log in with JWT-based security
- **User Profiles** - Customizable profiles with profile picture, cover photo, bio, location, and more
- **Social Timeline** - Create posts, upload images, and like content from people you follow
- **Follow System** - Follow and unfollow other users to curate your timeline
- **Real-Time Chat** - One-on-one messaging powered by Socket.IO
- **Online Status** - See which users are currently online

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Frontend** | React 17, Redux, React Router v6, Axios, React Bootstrap, Mantine UI |
| **Backend** | Node.js, Express.js, Mongoose, JWT, Multer, Bcrypt |
| **Database** | MongoDB (Atlas) |
| **Real-Time** | Socket.IO |

## Project Structure

```
Chat-URL/
├── client/          # React frontend (port 3000)
│   ├── src/
│   │   ├── pages/         # Auth, Home, Profile, Chat
│   │   ├── components/    # Reusable UI components
│   │   ├── api/           # Axios request modules
│   │   ├── actions/       # Redux action creators
│   │   ├── reducers/      # Redux reducers
│   │   └── store/         # Redux store configuration
│   └── package.json
├── server/          # Express API server (port 8080)
│   ├── controllers/       # Business logic
│   ├── models/            # Mongoose schemas (User, Post, Chat, Message)
│   ├── routes/            # API route definitions
│   ├── middleware/         # Auth middleware
│   └── package.json
└── socket/          # Socket.IO server (port 8800)
    └── package.json
```

## Getting Started

### Prerequisites

- Node.js (v14+)
- MongoDB instance (local or Atlas)

### Environment Variables

**Server** (`server/.env`):
```env
MONGO_URL=<your-mongodb-connection-string>
JWTKEY=<your-jwt-secret>
```

**Client** (`client/.env`):
```env
REACT_APP_PUBLIC_FOLDER=http://localhost:8080/images/
```

### Installation & Run

Install dependencies and start each service:

```bash
# Backend
cd server
npm install
npm start

# Socket server
cd socket
npm install
npm start

# Frontend
cd client
npm install
npm start
```

The app will be available at `http://localhost:3000`.

## API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/register` | Register a new user |
| POST | `/auth/login` | Log in |

### Users
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/user` | Get all users |
| GET | `/user/:id` | Get user by ID |
| PUT | `/user/:id` | Update user profile |
| PUT | `/user/:id/follow` | Follow a user |
| PUT | `/user/:id/unfollow` | Unfollow a user |

### Posts
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/posts` | Create a post |
| GET | `/posts/:id` | Get a user's posts |
| PUT | `/posts/:id` | Update a post |
| DELETE | `/posts/:id` | Delete a post |
| PUT | `/posts/:id/like` | Like / unlike a post |
| GET | `/posts/:id/timeline` | Get timeline posts |

### Chat & Messages
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/chat` | Create a conversation |
| GET | `/chat/:userId` | Get user's conversations |
| GET | `/chat/find/:firstId/:secondId` | Find a specific conversation |
| POST | `/message` | Send a message |
| GET | `/message/:chatId` | Get messages in a conversation |

### Upload
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/upload` | Upload an image |
