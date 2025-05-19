# Authentication Backend API

This is a Node.js authentication API built with Express and MongoDB.

## Features

- User registration (signup)
- User authentication (login)
- JWT-based authentication
- Password hashing with bcrypt
- Input validation
- Protected routes
- Error handling

## Setup Instructions

1. Install dependencies:
   ```
   npm install
   ```

2. Create a `.env` file in the root directory with the following variables:
   ```
   PORT=5000
   MONGO_URI=mongodb://localhost:27017/auth-db
   JWT_SECRET=your_jwt_secret_key_change_in_production
   JWT_EXPIRES_IN=1h
   ```

3. Make sure MongoDB is running on your system or update the MONGO_URI to point to your MongoDB instance.

4. Start the server:
   ```
   npm run server
   ```

## API Endpoints

### Register a new user
- **URL**: `/api/auth/signup`
- **Method**: `POST`
- **Body**:
  ```json
  {
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
  }
  ```
- **Response**:
  ```json
  {
    "success": true,
    "message": "User registered successfully",
    "data": {
      "user": {
        "id": "user_id",
        "name": "John Doe",
        "email": "john@example.com"
      },
      "token": "jwt_token"
    }
  }
  ```

### Login
- **URL**: `/api/auth/login`
- **Method**: `POST`
- **Body**:
  ```json
  {
    "email": "john@example.com",
    "password": "password123"
  }
  ```
- **Response**:
  ```json
  {
    "success": true,
    "message": "Login successful",
    "data": {
      "user": {
        "id": "user_id",
        "name": "John Doe",
        "email": "john@example.com"
      },
      "token": "jwt_token"
    }
  }
  ```

### Get Current User
- **URL**: `/api/auth/me`
- **Method**: `GET`
- **Headers**: `Authorization: Bearer jwt_token`
- **Response**:
  ```json
  {
    "success": true,
    "data": {
      "user": {
        "id": "user_id",
        "name": "John Doe",
        "email": "john@example.com"
      }
    }
  }
  ```

## Error Responses

All errors follow this format:
```json
{
  "success": false,
  "message": "Error message",
  "errors": [] // Optional validation errors array
}
```