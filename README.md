🔗 **Central Documentation:** [https://github.com/fitforge101/fitforge-app-docs](https://github.com/fitforge101/fitforge-app-docs)

# Workout Service

## Overview
The `workout-service` provides full CRUD capabilities for managing personalized workout routines. Users can define plans with specific exercises, sets, reps, and durations.

## Features
*   Create, Read, Update, and Delete structured workout plans.
*   Supports complex exercise lists within a single routine.
*   Feeds data context to the AI service for tailored recommendations.

## Tech Stack
*   Node.js
*   Express.js
*   MongoDB (Mongoose)

## API Endpoints
*   `GET /workout/plans/:userId` - Retrieve all plans for a user
*   `POST /workout/plans` - Create a new plan
*   `PUT /workout/plans/:planId` - Update an existing plan
*   `DELETE /workout/plans/:planId` - Delete a plan
*   `GET /health` - Healthcheck

## Example Request/Response

**POST `/workout/plans`**
*Request:*
```json
{
  "userId": "64a1b2c3d4e5f67890123456",
  "title": "Hypertrophy Push Day",
  "daysPerWeek": 2,
  "exercises": [
    { "name": "Bench Press", "sets": 4, "reps": 8, "durationMin": 15 }
  ]
}
```
*Response:*
```json
{
  "_id": "64c3d4e5f67890123456789b",
  "userId": "64a1b2c3d4e5f67890123456",
  "title": "Hypertrophy Push Day",
  "daysPerWeek": 2,
  "exercises": [
    { "name": "Bench Press", "sets": 4, "reps": 8, "durationMin": 15, "_id": "..." }
  ],
  "createdAt": "...",
  "updatedAt": "..."
}
```

## Setup Instructions
1.  **Install Dependencies:**
    ```bash
    npm ci
    ```
2.  **Run Development Server:**
    ```bash
    npm run dev
    ```

## Environment Variables
*   `PORT` (Default: `5003`)
*   `MONGO_URI` (Default: `mongodb://mongo:27017/workout_db`)

## Folder Structure
```text
.
├── package.json
└── src/
    ├── index.js
    ├── middleware/
    ├── models/
    │   └── WorkoutPlan.js
    └── routes/
        └── workout.js
```

## Deployment
Deployed via Kubernetes using the FitForge Helm charts located in the `fitforge-charts` repository.
