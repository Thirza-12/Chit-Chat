# Chit-Chat

## Backend Setup

1. Initialize the backend project:
   ```sh
   npm init -y
   ```
   This will create a `package.json` file.

2. Install required dependencies:
   ```sh
   npm i express mongoose dotenv jsonwebtoken bcryptjs cookie-parser cloudinary socket.io
   ```

3. Install `nodemon` as a development dependency:
   ```sh
   npm i nodemon -D
   ```

4. Create an `index.js` file for the backend.
   - If using CommonJS (default):
     ```js
     const express = require("express");
     ```
   - If using ES module:
     ```js
     import express from "express";
     ```

5. Add a script to run the backend:
   ```json
   "scripts": {
     "start": "node src/index.js",
     "dev": "nodemon src/index.js"
   }
   ```

6. Move `index.js` inside the `src` folder.

7. Create a `routes` folder inside `src`.
   - If using ES modules, append `.js` when importing routes.

## Database Connectivity

1. Create a MongoDB Atlas database.
2. Add the connection string in your code.

### User Table Schema:
- Email
- Full Name
- Password
- Profile Pic

### Message Table Schema:
- Sender ID
- Receiver ID
- Text
- Image

### Important Notes:
- `app.use(express.json());` enables parsing of JSON request bodies.
- `app.use(cookieParser());` enables access to `req.cookies.jwt`.
- Use `req.params.id` for dynamic routes like `/:id`.

## Frontend Setup

1. Create a Vite app inside the `frontend` folder:
   ```sh
   npm create vite@latest .
   ```
   - Choose `JavaScript` and `React`.

2. Install dependencies:
   ```sh
   npm install
   npm i react-router-dom react-hot-toast axios zustand lucide-react
   ```

3. Create a `lib` folder inside `frontend` and add `axios.js` in it.

4. Run the frontend:
   ```sh
   npm run dev
   ```

## Socket.io Integration

1. Install `socket.io` in the backend:
   ```sh
   npm i socket.io
   ```

2. Install `socket.io-client` in the frontend:
   ```sh
   npm i socket.io-client
   ```

### Strict Mode Behavior
- `<StrictMode>` in React causes `useEffect` to run twice. Remove it if needed to ensure it runs once.

## Deployment Steps

1. Create a `package.json` in the root directory:
   ```sh
   npm init -y
   ```

2. Add build and start scripts:
   ```json
   "scripts": {
     "build": "npm run build --prefix frontend",
     "start": "npm run start --prefix backend"
   }
   ```

3. In the backend, add a start script:
   ```json
   "scripts": {
     "start": "node src/index.js"
   }
   ```

4. Create a `.gitignore` in the root directory.
   - Copy `.gitignore` from `frontend` and delete it from there.
   - Add `.env` to the `.gitignore` file.

5. Install all dependencies and build the frontend:
   ```sh
   npm i --prefix backend && npm i --prefix frontend && npm run build --prefix frontend
   ```

6. Start the backend server:
   ```sh
   npm run start --prefix backend
   ```

7. Cleanup before final deployment:
   ```sh
   rm -rf backend/node_modules frontend/node_modules
   npm run build
   ```

Your project is now set up and ready for deployment!

