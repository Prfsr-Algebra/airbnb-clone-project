# Airbnb Clone Project
The goal oof this project is to practice my knowledge of advanced concepts in Backend Development

## Team Roles:
Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
Database Administrator: Manages database design, indexing, and optimizations.
DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.

## Technology Stack:
Django: A high-level Python web framework used for building the RESTful API.
Django REST Framework: Provides tools for creating and managing RESTful APIs.
PostgreSQL: A powerful relational database used for data storage.
GraphQL: Allows for flexible and efficient querying of data.
Celery: For handling asynchronous tasks such as sending notifications or processing payments.
Redis: Used for caching and session management.
Docker: Containerization tool for consistent development and deployment environments.
CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

## Database Design

This section outlines the core entities and their relationships for the Airbnb Clone project.

### Users
Represents registered users of the platform.

**Fields:**
- `id`: Unique identifier
- `name`: Full name of the user
- `email`: Email address (unique)
- `password`: Encrypted password
- `is_host`: Boolean flag indicating if the user can list properties

**Relationships:**
- A user **can own multiple properties**
- A user **can make multiple bookings**
- A user **can leave multiple reviews**

---

### 🏡 Properties
Represents a place listed for booking.

**Fields:**
- `id`: Unique identifier
- `user_id`: Foreign key to the user who listed the property
- `title`: Name of the property
- `description`: Detailed description
- `location`: Address or city
- `price_per_night`: Cost to rent per night

**Relationships:**
- A property **belongs to one user (host)**
- A property **can have many bookings**
- A property **can have many reviews**

---

### 📅 Bookings
Represents reservations made by users.

**Fields:**
- `id`: Unique identifier
- `user_id`: Foreign key to the guest (user)
- `property_id`: Foreign key to the booked property
- `start_date`: Check-in date
- `end_date`: Check-out date
- `total_price`: Calculated price based on nights

**Relationships:**
- A booking **belongs to one user**
- A booking **belongs to one property**

---

### ✍️ Reviews
Represents feedback left by users after a stay.

**Fields:**
- `id`: Unique identifier
- `user_id`: Foreign key to the reviewer
- `property_id`: Foreign key to the reviewed property
- `rating`: Numerical rating (e.g., 1–5)
- `comment`: Textual review

**Relationships:**
- A review **belongs to one user**
- A review **belongs to one property**

---

### 💳 Payments
Represents payment transactions for bookings.

**Fields:**
- `id`: Unique identifier
- `booking_id`: Foreign key to the associated booking
- `amount`: Amount paid
- `payment_date`: Date of payment
- `payment_status`: Status (e.g., Paid, Pending, Failed)

**Relationships:**
- A payment **is tied to one booking**

---

### 🔁 Summary of Relationships
- A **user** can have many **properties**, **bookings**, and **reviews**
- A **property** can have many **bookings** and **reviews**
- A **booking** belongs to a **user** and a **property**
- A **payment** is connected to one **booking**
- A **review** belongs to a **user** and a **property**

## Feature Breakdown:
### API Documentation
- OpenAPI Standard: The backend APIs are documented using the OpenAPI standard to ensure clarity and ease of integration.
Django REST Framework: Provides a comprehensive RESTful API for handling CRUD operations on user and property data.
GraphQL: Offers a flexible and efficient query mechanism for interacting with the backend.
- User Authentication
Endpoints: /users/, /users/{user_id}/
Features: Register new users, authenticate, and manage user profiles.
- Property Management
Endpoints: /properties/, /properties/{property_id}/
Features: Create, update, retrieve, and delete property listings.
- Booking System
Endpoints: /bookings/, /bookings/{booking_id}/
Features: Make, update, and manage bookings, including check-in and check-out details.
- Payment Processing
Endpoints: /payments/
Features: Handle payment transactions related to bookings.
- Review System
Endpoints: /reviews/, /reviews/{review_id}/
Features: Post and manage reviews for properties.
- Database Optimizations
Indexing: Implement indexes for fast retrieval of frequently accessed data.
Caching: Use caching strategies to reduce database load and improve performance.
