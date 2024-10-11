# Food Calorie Calculator Web Application

## Overview

The **Food Calorie Calculator Web Application** is a full-stack web application designed to help users log meals, set daily calorie goals, and visualize their calorie intake over time. It leverages **React** for the frontend, **Flask** for the backend, **MongoDB** for data storage, and the **USDA FoodData Central API** for calorie data. **JWT authentication** secures user data, ensuring that only authenticated users can access personalized information.

---

## Table of Contents

1. [Project Objectives](#project-objectives)
2. [Technology Stack](#technology-stack)
3. [System Architecture](#system-architecture)
4. [Authentication & Authorization](#authentication--authorization)
5. [APIs and Data Sources](#apis-and-data-sources)
6. [Frontend](#frontend)
7. [Backend](#backend)
8. [Database](#database)
9. [Deployment](#deployment)
10. [Future Improvements](#future-improvements)

---

## Project Objectives

1. **Track Calories**: Allow users to search food items, log daily meals, and track calorie intake.
2. **Daily Goals**: Set daily calorie goals and track progress in real-time.
3. **Dashboard & Analytics**: Visualize calorie intake trends over various time frames.
4. **User Authentication**: Implement JWT-based authentication for secure user management.
5. **API Integration**: Use USDA FoodData Central for nutritional data.

---

## Technology Stack

| Component      | Technology                            |
| -------------- | ------------------------------------- |
| Frontend       | React                                 |
| Backend        | Flask (Python)                        |
| Database       | MongoDB                               |
| Authentication | JWT (JSON Web Tokens)                 |
| External API   | USDA FoodData Central API             |
| Hosting        | Cloud (e.g., AWS, Heroku, or similar) |

---

## System Architecture

The application follows a **Client-Server** model:

1. **Frontend (React)**: Handles user interface and input. Communicates with the backend via HTTP requests.
2. **Backend (Flask)**: Processes requests, interacts with the database, and handles API calls for food data.
3. **Database (MongoDB)**: Stores user profiles, logged meals, and calorie goals.
4. **JWT Authentication**: Secures data, allowing only authorized users to access their information.

---

## Authentication & Authorization

JWT (JSON Web Token) is used for authenticating users:

1. **Login**: Users log in and receive a JWT if credentials are valid.
2. **Authorization Header**: Each request to protected endpoints includes the JWT in the `Authorization` header.
3. **Token Verification**: The backend verifies the JWT to ensure only authenticated users access resources.

### JWT Structure

- **Header**: Algorithm and token type.
- **Payload**: User information (e.g., user ID) and expiration.
- **Signature**: Ensures token integrity using a secret key.

---

## APIs and Data Sources

### USDA FoodData Central API

- **Purpose**: Fetch calorie data and nutritional information for various food items.
- **Advantages**: Large food database, no request limitations for non-commercial use.
- **Implementation**: The backend uses this API to fetch calorie data for food items searched by the user.

---

## Frontend

The frontend is built using **React** with the following features:

1. **User Interface**: Components for login, meal logging, goal setting, and data visualization.
2. **Form Validation**: Validates user inputs for login and meal logging.
3. **API Integration**: Sends requests to the Flask backend to log meals, set goals, and fetch calorie data.
4. **State Management**: Manages session and user state to provide a consistent user experience.
5. **Authorization**: Attaches the JWT to all requests that require user-specific data.

---

## Backend

The backend is built using **Flask** and provides the following endpoints:

| Endpoint    | Method | Description                              |
| ----------- | ------ | ---------------------------------------- |
| `/login`    | POST   | Authenticates user and returns JWT       |
| `/register` | POST   | Registers a new user and returns JWT     |
| `/meals`    | GET    | Retrieves logged meals for the user      |
| `/meals`    | POST   | Logs a meal with food items and calories |
| `/goals`    | POST   | Sets daily calorie goals                 |
| `/calories` | GET    | Fetches calorie data for food items      |

### JWT Implementation

- Uses `PyJWT` to encode and decode tokens.
- Validates tokens on each request to protected routes.
- Expiry of 30 minutes for each token, with refresh options as needed.

### Third-party Integration

- Connects to **USDA FoodData Central API** to fetch food data and calories for logging meals.

---

## Database

**MongoDB** is used as the data storage solution. Key collections include:

1. **Users**: Stores user credentials and profile information.
2. **Meals**: Records each meal, linked to a specific user.
3. **Goals**: Tracks daily calorie goals for each user.

Each document structure includes:

- **Users**: `{ _id, username, hashed_password, created_at }`
- **Meals**: `{ _id, user_id, food_items: [{ name, calories }], date }`
- **Goals**: `{ _id, user_id, daily_goal, date }`

---

## Deployment

1. **Frontend**: Deployed on platforms like Netlify or Vercel.
2. **Backend**: Hosted on a cloud provider (AWS, Heroku, or DigitalOcean).
3. **Database**: MongoDB Atlas for remote, cloud-based database storage.

---

## Future Improvements

1. **Real-Time Notifications**: Remind users to log meals and update daily goals.
2. **Machine Learning Predictions**: Suggest food items based on historical data.
3. **Additional Nutritional Data**: Include macros (protein, fats, carbs) and vitamins.
4. **Progress Tracking**: Visualize weekly or monthly goal achievement progress.

---

This document provides a comprehensive overview for developing and implementing the **Food Calorie Calculator Web Application**. It covers system architecture, technology stack, API integration, and authentication, providing a clear roadmap for development.
