# Scout: Source Code Open for Universal Testing

![Scout Banner](https://github.com/user-attachments/assets/9592e1bc-5cd9-4afe-9ba0-6ac0ac2a2c65)

A full-stack collaborative code sharing and discussion platform that allows users to share source code, collaborate in real-time, and discuss programming concepts. 

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Architecture](#architecture)
- [Technologies](#technologies)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Running the Application](#running-the-application)
- [Development Guide](#development-guide)
- [API Documentation](#api-documentation)

## Project Overview

**Scout** is a comprehensive platform for developers to:
- Share and showcase source code snippets
- Collaborate with other developers in real-time
- Discuss code implementations and best practices
- Build user profiles and communities
- Store and organize code repositories

The project consists of two main applications:
1. **scout_backend** - Node.js/Express REST API server
2. **scout_frontend** - React-based web interface

##  Features

### Backend Features
- User authentication (Login, Register, Logout)
- Post sharing and code snippet management
- Comments and discussions
- Cloud storage integration (Cloudinary)
- Real-time communication with WebSockets
- User profile management
- JWT-based security

### Frontend Features
- Modern, responsive UI/UX
- Real-time post display
- Code editor integration (Monaco Editor)
- Interactive components
- Redux state management
- React Router for navigation
- Tailwind CSS styling

##  Architecture

The application follows a monorepo structure with separated frontend and backend:

```
Scout/
├── scout_backend/          # Node.js/Express API server
│   ├── src/               # Source code
│   ├── build/             # Compiled output
│   ├── package. json
│   └── ... config files
└── scout_frontend/         # React web application
    ├── src/               # React components
    ├── dist/              # Build output
    ├── package. json
    └── ...config files
```

## 🛠️ Technologies

### Backend Stack
- **Runtime:** Node.js v23. 4.0
- **Framework:** Express.js
- **Database:** MongoDB
- **Authentication:** JWT (JSON Web Token)
- **Validation:** Joi
- **Real-time:** Socket.io
- **File Upload:** Multer + Cloudinary
- **Security:** bcryptjs, CORS
- **Build Tools:** Babel, Nodemon

### Frontend Stack
- **Framework:** React 19
- **Build Tool:** Vite
- **State Management:** Redux Toolkit
- **HTTP Client:** Axios
- **Routing:** React Router v7
- **Styling:** Tailwind CSS
- **Code Editor:** Monaco Editor
- **Real-time:** Socket.io-client
- **UI Components:** Headless UI, Heroicons, Lucide React
- **3D Graphics:** Three.js, React Three Fiber

##  Project Structure

### Backend Structure
```
scout_backend/
├── src/
│   ├── server. js          # Main server entry point
│   ├── routes/            # API routes
│   ├── controllers/       # Route handlers
│   ├── models/            # Database schemas
│   ├── middleware/        # Express middleware
│   ├── utils/             # Utility functions
│   └── config/            # Configuration files
├── build/                 # Compiled JavaScript
├── . babelrc              # Babel configuration
├── . prettierrc            # Prettier formatting rules
├── eslint.config.js       # ESLint configuration
└── package.json
```

### Frontend Structure
```
scout_frontend/
├── src/
│   ├── App.jsx            # Main App component
│   ├── main.jsx           # Entry point
│   ├── components/        # React components
│   ├── pages/             # Page components
│   ├── store/             # Redux store configuration
│   ├── slices/            # Redux slices
│   ├── services/          # API services
│   ├── hooks/             # Custom React hooks
│   ├── assets/            # Images, fonts, etc.
│   └── styles/            # Global styles
├── dist/                  # Production build
├── index.html             # HTML entry point
├── vite.config.js         # Vite configuration
├── tailwind.config.js     # Tailwind CSS config
├── postcss.config.js      # PostCSS configuration
└── package.json
```

##  Installation & Setup

### Prerequisites
- Node.js v23.4.0 or higher
- npm or yarn
- MongoDB running locally or cloud instance
- Cloudinary account (for image upload)

### Backend Setup

1. **Navigate to backend directory:**
```bash
cd scout_backend
```

2. **Install dependencies:**
```bash
npm install
```

3. **Create `. env` file:**
```bash
cp .env.example .env
```

Configure your environment variables:
- `MONGODB_URI` - MongoDB connection string
- `JWT_SECRET` - Secret key for JWT tokens
- `PORT` - Server port (default: 8017)
- `CLOUDINARY_NAME` - Cloudinary account name
- `CLOUDINARY_API_KEY` - Cloudinary API key
- `CLOUDINARY_API_SECRET` - Cloudinary API secret
- `NODE_ENV` - Environment (dev or production)

### Frontend Setup

1. **Navigate to frontend directory:**
```bash
cd scout_frontend
```

2.  **Install dependencies:**
```bash
npm install
```

3. **Create `.env` file:**
```bash
cp .env.example . env
```

Configure your environment variables:
- `VITE_API_URL` - Backend API URL (default: http://localhost:8017)
- `VITE_SOCKET_URL` - WebSocket server URL

##  Running the Application

### Development Mode

**Backend:**
```bash
cd scout_backend
npm run dev
```
The backend will start at `http://localhost:8017`

**Frontend:**
```bash
cd scout_frontend
npm run dev
```
The frontend will start at `http://localhost:5173`

### Production Mode

**Backend:**
```bash
cd scout_backend
npm run build        # Compile with Babel
npm run production   # Run compiled version
```

**Frontend:**
```bash
cd scout_frontend
npm run build        # Build optimized version
npm run preview      # Preview production build
```

##  Development Guide

### Code Quality Tools

All code follows consistent style and quality standards:

- **ESLint** - Code linting
- **Prettier** - Code formatting
- **Husky** - Git hooks for pre-commit checks
- **lint-staged** - Run linting on staged files

### Available Commands

#### Backend
```bash
npm run dev           # Start development server with hot reload
npm run build         # Compile with Babel
npm run production    # Run production build
npm run lint          # Check code quality
npm run format        # Format code with Prettier
npm run clean         # Clean build directory
```

#### Frontend
```bash
npm run dev           # Start development server
npm run build         # Create production build
npm run preview       # Preview production build
npm run lint          # Check code quality
npm run format        # Format code with Prettier
```

### Code Style

The project uses Prettier and ESLint to maintain consistent code style:

- **Prettier Configuration** (`.prettierrc`):
  - Semicolons enabled
  - Single quotes
  - Arrow parens always included
  - Tab width: 2 spaces

- **Husky Hooks**: Automatically formats and lints staged files before commit

### Git Workflow

1. Create a feature branch
2. Make your changes
3. Code will be automatically formatted and linted before commit
4. Push to GitHub and create a Pull Request

## 📡 API Documentation

### Base URL
```
http://localhost:8017/api
```

### Authentication
All protected routes require JWT token in the Authorization header:
```
Authorization: Bearer <token>
```

### Key Endpoints

#### Users
- `POST /auth/register` - Register new user
- `POST /auth/login` - Login user
- `POST /auth/logout` - Logout user
- `GET /users/:id` - Get user profile
- `PUT /users/:id` - Update user profile

#### Posts
- `GET /posts` - Get all posts
- `POST /posts` - Create new post
- `GET /posts/:id` - Get post details
- `PUT /posts/:id` - Update post
- `DELETE /posts/:id` - Delete post

#### Comments
- `POST /posts/:postId/comments` - Add comment
- `GET /posts/:postId/comments` - Get post comments
- `DELETE /comments/:id` - Delete comment

#### Real-time (WebSocket)
- `socket. emit('newPost')` - Broadcast new post
- `socket.emit('newComment')` - Broadcast new comment
- `socket.emit('userOnline')` - Notify user online

##  Dependencies Overview

### Critical Backend Dependencies
- **express** - Web framework
- **mongodb** - Database driver
- **jsonwebtoken** - JWT authentication
- **socket.io** - Real-time communication
- **bcrypt** - Password hashing
- **joi** - Data validation
- **cloudinary** - File storage

### Critical Frontend Dependencies
- **react** - UI library
- **react-router-dom** - Client-side routing
- **@reduxjs/toolkit** - State management
- **axios** - HTTP client
- **tailwindcss** - Utility CSS framework
- **@monaco-editor/react** - Code editor component

##  Troubleshooting

### Backend Issues

**Port Already in Use:**
```bash
# Change port in .env or kill process on port 8017
lsof -ti:8017 | xargs kill -9
```

**MongoDB Connection Error:**
- Verify MongoDB is running
- Check connection string in `.env`
- Ensure network access in MongoDB Atlas (if using cloud)

### Frontend Issues

**Module Not Found:**
```bash
rm -rf node_modules package-lock.json
npm install
```

**CORS Errors:**
- Ensure backend is running
- Check `VITE_API_URL` in `. env`

##  Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

##  License

This project is licensed under the ISC License. 

##  Author

**Scout Development Team**
- Repository: [waanney/Scout](https://github.com/waanney/Scout)

##  Support

For issues, questions, or suggestions, please open an issue on the GitHub repository.

---

**Happy Coding!  **
