# Node.js Express Authentication API

This is a simple authentication API built with Node.js, Express, and MongoDB. It includes user registration, login, and JWT-based authentication.

## Features
- User registration with `username`, `email`, and `password`.
- Password hashing using `bcrypt`.
- User login with JWT token generation.
- Middleware for JWT authentication.
- MongoDB database integration with Mongoose.
- Environment variable support using `dotenv`.

## Installation

### Prerequisites
- Node.js installed
- MongoDB instance (local or cloud-based, e.g., MongoDB Atlas)

### Steps
1. Clone the repository:
   ```sh
   git clone https://github.com/vaibhavvatsbhartiya/podcast-registration-backend1
   cd auth-api
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Create a `.env` file and add:
   ```env
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_secret_key
   PORT=5000
   ```
4. Start the server:
   ```sh
   npm start
   ```
   The server will run at `http://localhost:5000`.

## API Endpoints

### Register a User
**POST** `/api/register`
#### Request Body:
```json
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "securepassword123"
}
```
#### Response:
```json
{
  "message": "User registered successfully"
}
```

### User Login
**POST** `/api/login`
#### Request Body:
```json
{
  "email": "john@example.com",
  "password": "securepassword123"
}
```
#### Response:
```json
{
  "token": "your_generated_jwt_token",
  "user": {
    "_id": "user_id",
    "username": "john_doe",
    "email": "john@example.com"
  }
}
```

### Get User Profile (Protected Route)
**GET** `/api/profile`
#### Headers:
```json
{
  "Authorization": "Bearer your_jwt_token"
}
```
#### Response:
```json
{
  "_id": "user_id",
  "username": "john_doe",
  "email": "john@example.com"
}
```

## Deployment
1. Set up a production database (e.g., MongoDB Atlas).
2. Update the `.env` file with the production `MONGO_URI` and `JWT_SECRET`.
3. Use a hosting provider like **Render, Railway, or AWS** to deploy the API.

## Security Best Practices
- Use **HTTP-only cookies** instead of storing JWT in local storage.
- Enable **CORS** to restrict access to allowed domains.
- Implement **rate limiting** to prevent brute-force attacks.
- Use **helmet** middleware for security enhancements.

## License
MIT License

