Backend Development
This repository contains backend development practice and implementation using Node.js, Express.js, MongoDB, and REST APIs. The project demonstrates how to build a backend server with authentication, database connectivity, middleware handling, and reusable services for registration and login.

The project is designed to understand backend architecture, API development, and authentication workflows for different user roles such as USER and AUTHOR.

Project Overview
The backend application provides:

REST API development

User authentication

Role-based login and registration

Database integration

Middleware handling

Environment variable management

The project follows a structured backend development workflow and reusable service architecture.

Backend Development Steps
1. Create Git Repository
Initialize a Git repository for version control.

Bash

git init
2. Add .gitignore File
Create a .gitignore file to ignore:

node_modules

environment files

logs

Example:

Bash

node_modules/
.env
3. Create .env File
Store environment variables securely inside the .env file.

Install dotenv package:

Bash

npm install dotenv
Example .env file:

env

PORT=5000
DB_URL=your_database_url
SECRET_KEY=your_secret_key
Read environment variables using dotenv:

JavaScript

import dotenv from "dotenv";
dotenv.config();
4. Generate package.json
Initialize Node.js project configuration.

Bash

npm init -y
5. Create Express Application
Install Express.js:

Bash

npm install express
Create server:

JavaScript

import express from "express";

const app = express();

app.listen(5000, () => {
  console.log("Server running...");
});
6. Connect to Database
Install MongoDB and Mongoose:

Bash

npm install mongoose
Database connection example:

JavaScript

import mongoose from "mongoose";

mongoose.connect(process.env.DB_URL)
  .then(() => console.log("Database Connected"))
  .catch(err => console.log(err));
7. Add Middlewares
Install middleware packages if required.

Body Parser Middleware
JavaScript

app.use(express.json());
Error Handling Middleware
JavaScript

app.use((err, req, res, next) => {
  res.status(500).send({ message: err.message });
});
8. Design Schemas and Models
Create database schemas using Mongoose.

Example User Schema:

JavaScript

import mongoose from "mongoose";

const userSchema = new mongoose.Schema({
  username: String,
  email: String,
  password: String,
  role: String
});

export const UserModel = mongoose.model("users", userSchema);
9. Design REST APIs
Create REST APIs for application resources.

Example APIs:

Method	Endpoint	Description
POST	/user/register	Register User
POST	/user/login	Login User
GET	/users	Get Users
POST	/author/register	Register Author
POST	/author/login	Login Author

Registration & Login
10. Common Registration & Login Service
Create reusable authentication services for both USER and AUTHOR roles.

Install required packages:

Bash

npm install bcryptjs jsonwebtoken
Authentication Service Example
JavaScript

import bcrypt from "bcryptjs";
import jwt from "jsonwebtoken";

export const authenticate = async (user, password) => {
  const matched = await bcrypt.compare(password, user.password);

  if (!matched) {
    return null;
  }

  const token = jwt.sign(
    { username: user.username, role: user.role },
    process.env.SECRET_KEY,
    { expiresIn: "1d" }
  );

  return token;
};
11. Role-Based API Handling
The client does not send the role directly.

Instead:

The frontend redirects requests to different APIs based on selected role.

The API route assigns the role internally.

Example:

User Registration Route
JavaScript

user.role = "USER";
Author Registration Route
JavaScript

user.role = "AUTHOR";
This approach improves security and avoids manual role manipulation from the client side.

Technologies Used
Node.js

Express.js

MongoDB

Mongoose

JWT Authentication

bcryptjs

dotenv

Folder Structure
Bash

Backend/
│
├── config/
├── models/
├── routes/
├── services/
├── middlewares/
├── .env
├── server.js
├── package.json
└── README.md
Learning Outcomes
By completing this backend project, you will learn:

Backend project setup

Express.js server creation

MongoDB database integration

REST API development

Middleware handling

JWT authentication

Password hashing using bcrypt

Environment variable management

Reusable service creation

Role-based authentication

Future Enhancements
Add refresh tokens

Add role-based authorization

Add validation middleware

Add file upload support

Add API documentation

Add unit testing
