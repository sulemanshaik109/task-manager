# Task Manager
A RESTful API for managing tasks, built using Node.js, Express, and MongoDB. The API supports CRUD operations, filtering, sorting, and pagination.

## Features

- Create, read, update, and delete tasks.
- Filter tasks by status and priority.
- Sort tasks by createdAt or dueDate.
- Implement pagination with limit and skip.
- Proper input validation using Joi.
- Error handling with descriptive messages.

## Prerequisites

- Node.js (version >= 16)
- MongoDB Atlas account (or local MongoDB setup)
- Postman for testing

## Setup Instructions

### 1. Clone the Repository

    git clone https://github.com/sulemanshaik109/task-manager.git
    cd task-manager

### 2. Install Dependencies

    npm install

### 3. Configure Environment Variables

Create a .env file in the root directory and add the following:

    PORT=5000
    MONGO_URI=mongodb+srv://sulemanshaik109:15243109Ss@suleman1.mzfvh.mongodb.net/taskdb?retryWrites=true&w=majority&appName=Suleman1

### 4. Start the Server

    node index.js

The server will run on http://localhost:5000.

## Endpoints
### Base URL

    http://localhost:5000

### 1. Create a Task

POST /api/tasks

Request Body:

    {
    "title": "Complete API Documentation",
    "description": "Write detailed documentation for the Task Management API.",
    "status": "TODO",
    "priority": "HIGH",
    "dueDate": "2024-12-15"
    }

Response:

    {
    "_id": "64fa1c5bc12345678",
    "title": "Complete API Documentation",
    "description": "Write detailed documentation for the Task Management API.",
    "status": "TODO",
    "priority": "HIGH",
    "dueDate": "2024-12-15T00:00:00.000Z",
    "createdAt": "2024-12-07T10:00:00.000Z",
    "updatedAt": "2024-12-07T10:00:00.000Z"
    }

### 2. Retrieve All Tasks

GET /api/tasks

Query Parameters:

- status: Filter by task status (e.g., TODO, IN_PROGRESS, COMPLETED).
- priority: Filter by task priority (LOW, MEDIUM, HIGH).
- sort: Sort by createdAt or dueDate (e.g., sort=createdAt:asc).
- page: Specify page number for pagination (default: 1).
- limit: Number of tasks per page (default: 5).

Example Request:

    GET /tasks?status=TODO&priority=HIGH&sort=createdAt:desc&page=1&limit=3

Response:

    {
    "page": 1,
    "limit": 3,
    "totalTasks": 12,
    "totalPages": 4,
    "tasks": [
        {
        "_id": "64fa1c5bc12345678",
        "title": "Complete API Documentation",
        "description": "Write detailed documentation for the Task Management API.",
        "status": "TODO",
        "priority": "HIGH",
        "dueDate": "2024-12-15T00:00:00.000Z",
        "createdAt": "2024-12-07T10:00:00.000Z",
        "updatedAt": "2024-12-07T10:00:00.000Z"
        }
    ]
    }

### 3. Retrieve a Single Task

GET /api/tasks/:id

Example Request:

    GET /tasks/64fa1c5bc12345678

Response:

    {
    "_id": "64fa1c5bc12345678",
    "title": "Complete API Documentation",
    "description": "Write detailed documentation for the Task Management API.",
    "status": "TODO",
    "priority": "HIGH",
    "dueDate": "2024-12-15T00:00:00.000Z",
    "createdAt": "2024-12-07T10:00:00.000Z",
    "updatedAt": "2024-12-07T10:00:00.000Z"
    }

### 4. Update a Task

PUT /api/tasks/:id

Request Body:

    {
    "status": "IN_PROGRESS"
    }

Response:

    {
    "_id": "64fa1c5bc12345678",
    "title": "Complete API Documentation",
    "description": "Write detailed documentation for the Task Management API.",
    "status": "IN_PROGRESS",
    "priority": "HIGH",
    "dueDate": "2024-12-15T00:00:00.000Z",
    "createdAt": "2024-12-07T10:00:00.000Z",
    "updatedAt": "2024-12-07T11:00:00.000Z"
    }

### 5. Delete a Task

DELETE /api/tasks/:id

Example Request:

    DELETE /tasks/64fa1c5bc12345678

Response:

    {
    "message": "Task deleted successfully."
    }

## Deployment

### Backend Deployment on Render

1. Create a Render Account:
    - Sign up for a free account at Render.

2. Create a New Web Service:
    - In the Render dashboard, click on "New" and then "Web Service".
    - Connect your GitHub repository and select the notes-app repository.

3. Configure Build and Start Commands:
    - Root Directory:

        ```
        task-manager
        ```

    - Build Command:

        ```
        npm install
        ```

    - Start Command:

        ```
        node index.js
        ```

4. Set Environment Variables:

    - In the Render service settings, add any necessary environment variables.

5. Deploy:

    - Trigger a new deploy by pushing changes to your GitHub repository or clicking the "Deploy" button in Render.

6. Access the Application:

    - Once the deployment is successful, you can access the backend at the URL provided by Render.

# Show Your Support

Give a ⭐️ if you like this project!