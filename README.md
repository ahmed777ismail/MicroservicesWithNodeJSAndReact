# Microservices With NodeJS And React

A simple mini microservices example demonstrating a React frontend with separate Node.js services for posts and comments.

## Repository Structure

- `A Mini-Microservices/client` - React frontend application
- `A Mini-Microservices/posts` - Posts service (Express) on port `4000`
- `A Mini-Microservices/comments` - Comments service (Express) on port `4001`

## Overview

This project shows a lightweight microservices layout:
- The frontend creates posts and fetches the current post list from the posts service.
- The posts service stores posts in memory and exposes REST endpoints.
- The comments service stores comments per post ID and exposes comment endpoints.

> Note: The current React UI is wired to the posts service only.

## Getting Started

### Prerequisites

- Node.js installed
- npm available

### Install dependencies

From the repository root, install dependencies for each service:

```bash
cd "A Mini-Microservices/client"
npm install

cd "..\posts"
npm install

cd "..\comments"
npm install
```

### Run the applications

Start each service in a separate terminal window:

```bash
cd "A Mini-Microservices/posts"
npm start
```

```bash
cd "A Mini-Microservices/comments"
npm start
```

```bash
cd "A Mini-Microservices/client"
npm start
```

The React app will start on `http://localhost:3000` and communicate with the posts service on `http://localhost:4000`.

## API Endpoints

### Posts service (`http://localhost:4000`)

- `GET /posts` - Retrieve all posts
- `POST /posts` - Create a new post
  - Request body: `{ "title": "Post title" }`

### Comments service (`http://localhost:4001`)

- `GET /posts/:id/comments` - Retrieve comments for a specific post
- `POST /posts/:id/comments` - Add a comment to a specific post
  - Request body: `{ "content": "Comment text" }`

## Notes

- Both backend services use in-memory storage and do not persist data after restart.
- CORS is enabled on both services so the React frontend can call them from `localhost:3000`.
- The services use `nodemon` for automatic restart during development.

## Future Improvements

- Add comment creation and display support in the frontend
- Add a query/event bus service to share data across microservices
- Replace in-memory storage with a database
- Add validation and error handling
