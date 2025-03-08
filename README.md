# Online Bookstore

An advanced e-commerce platform for book shopping, built using Node.js, Express.js and MongoDB. This platform allows users to browse books, manage their shopping cart, place orders, and leave reviews.

## 📚 Features

- **User Authentication & Authorization**
  - Secure login and registration with JWT
  - Role-based access (Admin/Customer)
  - Password encryption with bcrypt

- **Book Management**
  - Browse books with pagination
  - Search and filter functionality
  - Detailed book information
  - Book cover image uploads

- **Author Management**
  - Create and manage author profiles
  - Link authors to their books

- **Shopping Experience**
  - Add/remove books from cart
  - Place orders with stock validation
  - Order history tracking

- **Reviews & Ratings**
  - Leave reviews on books
  - Rate books on a 5-star scale
  - View other user reviews

- **Admin Features**
  - Manage users, books, authors
  - Process orders
  - View statistics and logs

- **Security**
  - Input validation
  - Error handling
  - Logging with Winston

## 🚀 Getting Started

### Prerequisites

- Node.js
- MongoDB
- npm

### Installation

1. Clone the repository
```bash
git clone https://github.com/ahmeedusamaa/online-bookstore
cd online-bookstore/backend
```

2. Install dependencies
```bash
npm install
```

3. Create a `.env` file in `/backend` directory with the following variables:
```
JWT_SECRET=your_jwt_secret_key
PORT=3000
ATLAS_USER_NAME=your_mongodb_username
ATLAS_PASSWORD=your_mongodb_password
EMAIL_USER=your_system_gmail_address
EMAIL_PASSWORD=your_gmail_password
ADMIN_EMAIL=your_admin_email_address
```

4. Create the `uploads/` directory for book covers
```bash
mkdir uploads
```

5. Start the server
```bash
npm run dev
```

The server should now be running at `http://localhost:3000`.

## 🔗 API Endpoints

### Authentication & User Management
- `POST /api/users/register` - Register a new user
- `POST /api/users/login` - User login
- `POST /api/users/logout` - User logout (requires authentication)
- `PATCH /api/users/:id` - Update user profile (requires authentication)
- `GET /api/users` - Get all users with pagination (requires authentication)
- `GET /api/users/:id` - Get user by ID (requires authentication)
- `GET /api/users/:id/reviews` - Get reviews written by a specific user (requires authentication)
- `GET /api/users/:id/orders` - Get orders made by a specific user (requires authentication)

### Books
- `POST /api/books` - Add a new book (admin only)
- `GET /api/books` - Get all books with pagination (requires authentication)
- `GET /api/books/:id` - Get book details by ID (requires authentication)
- `GET /api/books/:id/reviews` - Get reviews for a specific book (requires authentication)
- `PATCH /api/books/:id` - Update a book (admin only)
- `DELETE /api/books/:id` - Delete a book (admin only)

### Authors
- `POST /api/authors/create` - Create a new author (admin only)
- `GET /api/authors` - Get all authors
- `GET /api/authors/:id` - Get author details by ID
- `PUT /api/authors/:id` - Update an author (admin only)
- `DELETE /api/authors/:id` - Delete an author (admin only)

### Cart
- `POST /api/cart` - Add a book to the user's cart (requires authentication)
- `DELETE /api/cart/:id` - Remove a book from the user's cart (requires authentication)
- `GET /api/cart` - Get the contents of the user's cart (requires authentication)

### Orders
- `POST /api/orders` - Create a new order (requires authentication)
- `GET /api/orders` - Get all orders with pagination (admin only)
- `GET /api/orders/:id` - Get order details by ID (admin only)
- `DELETE /api/orders/:id` - Delete an order (admin only)

### Reviews
- `POST /api/reviews` - Create a new review (requires authentication)
- `GET /api/reviews/:id` - Get review details by ID
- `PUT /api/reviews/:id` - Update a review (requires authentication)
- `DELETE /api/reviews/:id` - Delete a review (requires authentication)

### Backend Structure

```
online-bookstore/
├── backend/
|    ├── controllers/      # Route handlers
|    ├── docs/             # Backend documentation
|    ├── logs/             # Server logs
|    ├── middlewares/      # Express middlewares
|    ├── models/           # Mongoose schemas
|    ├── routes/           # API routes
|    ├── services/         # External services
|    ├── uploads/          # Book cover images
|    ├── utils/            # System utility files
|    ├── validations/      # Request validation schemas
|    ├── index.js          # Entry point
|    └── package.json      # Dependencies
└── frontend
```

## 📊 Database Schema

The application uses MongoDB with Mongoose for data modeling. Key collections include:
- Users
- Books
- Authors
- Orders
- Reviews

## 🔐 Security

This application implements several security measures:
- JWT authentication for API endpoints
- Password hashing with bcrypt
- Input validation with express-validator
- Role-based access control
- Comprehensive error handling and logging

## 🛠️ Technologies Used

- **Backend**: Node.js, Express.js
- **Database**: MongoDB, Mongoose
- **Authentication**: JWT, bcrypt
- **File Upload**: Multer
- **Validation**: Express Validator
- **Logging**: Winston
- **Email Service**: Nodemailer
