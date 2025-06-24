# MERN-Product-Store
**MERN Stack Backend Setup Guide**

A comprehensive guide to building a scalable MERN stack backend withExpress.js, MongoDB, and modern JavaScript practices.

**Table of Contents**



*   Prerequisites
    
*   Project Setup
    
*   Dependencies
    
*   Server Configuration
    
*   Database Connection
    
*   Environment Variables
    
*   Running the Application
    
*   Project Structure
    
*   Next Steps

**Prerequisites**

Before you begin, ensure you have the following installed:

*   Node.js (v14 or higher)
    

*   npm or yarn
    

*   MongoDB Atlas Account (free tier available)
    

*   Visual Studio Code (recommended)
    

**Project Setup**

**1\. Initialize Project**

Create a new project directory and initialize it:

mkdir mern-crash-course

cd mern-crash-course

npm init -y

**2\. Project Structure**

Create the following folder structure:

mern-crash-course/

├── config/

├── frontend/          # React app (future implementation)

├── .env

├── .gitignore

├── package.json

└── server.js

**Dependencies**

Install the required packages:

\# Production dependencies

npm install express mongoose dotenv

\# Development dependencies

npm install -D nodemon

**Package Overview**

*   **express** - Web application framework for Node.js
    

*   **mongoose** - MongoDB object modeling for Node.js
    

*   **dotenv** - Loads environment variables from .env file
    

*   **nodemon** - Automatically restarts server on file changes
    

**Server Configuration**

**1\. Enable ES Modules**

Update your package.json to use modern ES modules:

 add "type": "module",




**2\. Create Main Server File**

Create server.js in the root directory:

import express from 'express';

import dotenv from 'dotenv';

import { connectDB } from'./config/db.js';

// Load environment variables

dotenv.config();

// Connect to MongoDB

connectDB();

const app = express();

// Middleware

app.use(express.json()); // Parse JSONbodies

// Routes

app.get('/', (req, res) => {

 res.json({ message: 'API is running successfully!' });

});

app.get('/api/products', (req, res)=> {

 res.json({ message: 'Product endpoints coming soon...' });

});

const PORT = process.env.PORT || 5000;

app.listen(PORT, () => {

 console.log(\`Server running on port ${PORT}\`);

});

**Database Connection**

**1\. MongoDB Atlas Setup**

2.  Create a MongoDB Atlas account
    

4.  Create a new cluster (free tier available)
    

6.  Create a database user with read/write permissions
    

8.  Whitelist your IP address (or use 0.0.0.0/0 for development)
    

10.  Get your connection string
    

**2\. Database Configuration**

Create config/db.js:

import mongoose from 'mongoose';

export const connectDB = async ()=> {

 try {

   const conn = await mongoose.connect(process.env.MONGO\_URI);

   console.log(\`MongoDB Connected: ${conn.connection.host}\`);

 } catch (error) {

   console.error(\`MongoDB Connection Error: ${error.message}\`);

   process.exit(1);

 }

};

**Environment Variables**

Create a .env file in the rootdirectory:

\# MongoDB Connection

MONGO\_URI=mongodb+srv://:@cluster.mongodb.net/?retryWrites=true&w=majority

\# Server Configuration

PORT=5000

NODE\_ENV=development

**Important**: Add .env to your .gitignore file to avoid committing sensitivedata!

**.gitignore**

Create a .gitignore file:

\# Dependencies

node\_modules/

\# Environment variables

.env

\# Logs

\*.log

npm-debug.log\*

\# Runtime data

pids

\*.pid

\*.seed

\# Coverage directory used by toolslike istanbul

coverage/

\# Build outputs

dist/

build/

\# IDE files

.vscode/

.idea/

**Running the Application**

**Development Mode**

npm run dev

**Production Mode**

npm start

**Expected Output**

MongoDB Connected:cluster0-shard-00-02.xxxxx.mongodb.net

Server running on port 5000

**Testing the API**

Open your browser or use curl to test:

\# Test main endpoint

curl http://localhost:5000

\# Test products endpoint

curlhttp://localhost:5000/api/products

**Project Structure**

After following this guide, your project structure should look like:

mern-crash-course/

├── config/

│  └── db.js              # Databaseconnection logic

├── frontend/              # Future React application

├── .env                   # Environment variables (notin git)

├── .gitignore            # Git ignore rules

├── package.json          # Project dependencies and scripts

├── package-lock.json     # Dependency lock file

└── server.js             # Main server file

**Next Steps**

Now that you have a solid backend foundation, you can:

2.  **Create Data Models** - Define Mongoose schemas for your application
    

4.  **Build API Routes** - Implement CRUD operations for your resources
    

6.  **Add Middleware** - Implement authentication, validation, and error handling
    

8.  **Frontend Integration** - Connect your React frontend
    

10.  **Deployment** - Deploy to platforms like Heroku, Vercel, or Railway
    

**Contributing**

Contributions are welcome! Please feel free to submit a Pull Request.

**License**

This project is licensed under the MIT License.

**Useful Links**

*   [Express.js Documentation](https://expressjs.com/)
    

*   [Mongoose Documentation](https://mongoosejs.com/)
    

*   [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
    

*   [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)
