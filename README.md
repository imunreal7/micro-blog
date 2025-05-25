# Micro-Blog Application (MERN Microservices Architecture)

This is a Micro-Blog project structured using microservices architecture with Node.js for each service using event-bus and a React-based client.

## 📁 Project Structure

```
micro-blog/
├── client/           # React frontend
│   └── src/
├── comments/         # Comments service (Node.js + Express)
├── event-bus/        # Event bus service for event-driven communication
├── moderation/       # Moderation service to check inappropriate content
├── posts/            # Posts service (Node.js + Express)
├── query/            # Query service to aggregate data for frontend
└── .gitignore        # Git ignore rules
```

## 🚀 Getting Started

### Prerequisites

-   Node.js (v14+)
-   npm or yarn

### Setup Instructions

1. **Install dependencies** for each service and client:

    ```bash
    cd client && npm install
    cd ../comments && npm install
    cd ../event-bus && npm install
    cd ../moderation && npm install
    cd ../posts && npm install
    cd ../query && npm install
    ```

2. **Run all services** (in separate terminals or using a process manager like `concurrently`, `pm2`, or Docker):

    ```bash
    # Example: Run each service individually
    cd comments && npm start
    cd event-bus && npm start
    cd moderation && npm start
    cd posts && npm start
    cd query && npm start
    cd client && npm start
    ```

### Environment Variables

Each service may use environment variables (e.g., for port numbers or DB connections). Create `.env` files as needed.

### Available Scripts (in each folder)

-   `npm start` - Start the service
-   `npm run dev` - Run with nodemon (if configured)

## 🧱 Services Overview

-   **Client**: React application to interact with posts and comments.
-   **Posts**: Create and store blog posts.
-   **Comments**: Add comments to posts.
-   **Event Bus**: Handle communication between microservices using events.
-   **Moderation**: Filter inappropriate words in comments.
-   **Query**: Aggregate posts and comments for the client.

## 📝 License

This project is open-source and free to use.

