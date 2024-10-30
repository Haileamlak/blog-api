# Blog API

A scalable RESTful API for a blog platform that supports user authentication and authorization, CRUD operations for blog posts, advanced search and filtering, and role-based access control. It also includes AI integration for content generation, suggestion, and enhancement. The API is built using Go and designed for high performance, scalability, and maintainability using clean architecture.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Environment Variables](#environment-variables)
- [Running the Application](#running-the-application)
- [Running Tests](#running-tests)
- [API Endpoints](#api-endpoints)

## Features
- **User Authentication**: JWT-based authentication and role management (Admin and User roles).
- **Blog Management**: Create, update, delete, and retrieve blog posts with advanced search and filtering capabilities.
- **AI Content Suggestions**: Integrated AI for generating blog content ideas based on user input.
- **User Management**: Registration, login, password reset, and profile updates.
- **Role-Based Access Control**: Admin and User roles with different permissions for managing content.
- **Popularity Metrics**: Track blog post views, likes, and comments.
- **Secure Password Handling**: Use bcrypt for password storage and validation.
- **Database Integration**: MongoDB for storing user and blog data.
- **Unit Testing**: Comprehensive test suite for ensuring code quality and reliability.

## Tech Stack
- **Language**: Go (Golang)
- **Framework**: Gin for HTTP routing and middleware
- **Database**: MongoDB, Redis
- **Authentication**: JWT (JSON Web Tokens), SMTP
- **AI Integration**: Gemini for content generation
- **Environment Management**: godotenv
- **Testing**: Testify, httptest

## Getting Started

### Prerequisites
Before starting, ensure you have the following installed:
- **Go** (1.18 or higher)
- **MongoDB** (local or cloud instance)
- **Git**

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/haileamlak/blog-api.git
   cd blog-starter-api
   ```

2. Install dependencies:
   ```bash
   go mod tidy
   ```

3. Set up the environment variables by creating a `.env` file in the root directory with the following contents:
   ```bash
    VERIFY_PATH = http://localhost:8080/user/verify/%s
    RESET_PASSWORD_PATH = http://localhost:8080/user/reset/%s
    CLOUDINARY_URL = cloudinary://
    CLOUDINARY_NAME = <your cloudinary>
    CLOUDINARY_API_KEY = <your cloudinary api key
    CLOUDINARY_API_SECRET = <your cloudinary api secret>
    GEMINI_API_KEY = <your gemini api key>
    CACHE_DB_URI=<your cache db uri>
    CACHE_DB_NAME=<your cache db name>
    CACHE_DB_PASSWORD=<your cache db password>
     
    DATABASE_URI=<your db uri>
    DATABASE_NAME=blog-api 
     
    PORT=8080 
     
    ACCESS_SECRET=<your access secret>
    REFRESH_SECRET=<your refresh secret>
    VERIFY_SECRET=<your verify secret>
    RESET_SECRET=<your reset secret>
     
    CONTEXT_TIMEOUT=2
    
    SMTP_PASSWORD = <your smtp password>
    SMTP_EMAIL = <your smtp email>
   ```

## Project Structure

```
blog-starter-api/
├── Delivery/           # HTTP handlers, request/response structures, main.go file (entry point)
├── Domain/             # Core business logic and entities
├── Infrastructure/     # External services (database, JWT, password hashing)
├── Repositories/       # Data persistence and retrieval logic
├── Usecases/           # Application-specific business rules
├── Tests               # Testing files for critical components
├── .env                # Environment variables file
├── go.mod              # Go module dependencies
├── README.md           # Project documentation
```

## Running the Application
To start the server, run:
```bash
go run main.go
```
The server will start at [http://localhost:8080](http://localhost:8080).

## Running Tests
This project includes a suite of unit tests to ensure code quality. To run the tests:
```bash
go test ./...
```
### Testing Considerations
- **Test Coverage**: Critical components are covered, including user management, blog CRUD operations, and authentication.
- **Issues**: Ensure that MongoDB is running locally, or mock database interactions for tests.

## API Endpoints

### User Authentication
- **POST** `/auth/register`: Register a new user
- **POST** `/auth/login`: User login
- **POST** `/auth/logout`: Logout and invalidate tokens
- **POST** `/auth/forgot-password`: Request a password reset
- **POST** `/auth/reset-password`: Reset user password

### Blog Management
- **GET** `/blogs`: Retrieve all blog posts with pagination and filtering
- **GET** `/blogs/:id`: Retrieve a single blog post by ID
- **POST** `/blogs`: Create a new blog post (requires authentication)
- **PUT** `/blogs/:id`: Update a blog post (requires authentication)
- **DELETE** `/blogs/:id`: Delete a blog post (requires authentication)

### AI Content Suggestions
- **POST** `/blogs/generate`: Get generated blog content by AI (requires authentication)
- **POST** `/blogs/enhance`: Get AI-generated content enhancement for a blog post (requires authentication)
- **GET** `/blogs/enhance`: Get AI-generated content suggestions for writing a blog post (requires authentication)
