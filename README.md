# To-Do List App Backend

A NestJS-based backend for a To-Do List application with MongoDB integration for cross-device task synchronization.

## Features

- RESTful API for task management
- MongoDB integration with Mongoose ODM
- Full CRUD operations for tasks
- Cross-device synchronization support
- Environment-based configuration

## Prerequisites

- Node.js (v14 or later)
- npm or yarn
- MongoDB (local instance or MongoDB Atlas)

## Installation

1. Clone the repository
2. Navigate to the backend directory:
   ```bash
   cd todo-backend
   ```
3. Install dependencies:
   ```bash
   npm install
   ```
4. Set up your environment variables by creating a `.env` file in the root directory:
   ```
   MONGO_URI=mongodb://localhost:27017/todo-app
   PORT=3001
   FRONTEND_URL=http://localhost:3000
   ```

## Running the Application

### Development Mode

```bash
npm run start:dev
```

### Production Mode

```bash
npm run build
npm run start:prod
```

## API Endpoints

| Method | Endpoint      | Description                   |
|--------|---------------|-------------------------------|
| GET    | /tasks        | Get all tasks                 |
| GET    | /tasks/:id    | Get a specific task by ID     |
| POST   | /tasks        | Create a new task             |
| PATCH  | /tasks/:id    | Update a task by ID           |
| DELETE | /tasks/:id    | Delete a task by ID           |

## Project Structure

```
src/
├── tasks/                  # Tasks module
│   ├── dto/                # Data Transfer Objects
│   │   ├── create-task.dto.ts
│   │   └── update-task.dto.ts
│   ├── schemas/            # MongoDB schemas
│   │   └── task.schema.ts
│   ├── tasks.controller.ts # API endpoints
│   ├── tasks.module.ts     # Module definition
│   └── tasks.service.ts    # Business logic
├── app.module.ts           # Main application module
└── main.ts                 # Application entry point
```

## Environment Variables

| Variable      | Description                            | Default                      |
|---------------|----------------------------------------|------------------------------|
| MONGO_URI     | MongoDB connection string              | mongodb://localhost:27017/todo-app |
| PORT          | Port number for the API server         | 3001                         |
| FRONTEND_URL  | URL of the frontend for CORS settings  | http://localhost:3000        |

## Deployment

For production deployment:

1. Set up a MongoDB instance (MongoDB Atlas recommended for cloud deployment)
2. Configure environment variables for your production environment
3. Build the application: `npm run build`
4. Start the application: `npm run start:prod`

## Cross-device Synchronization

The synchronization across devices is achieved by:
- Storing all tasks in a central MongoDB database
- Having the frontend regularly poll for updates
- Implementing proper error handling and status indicators