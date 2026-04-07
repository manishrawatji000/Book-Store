# 📚 BookyVerse

A full-stack book e-commerce web application built with the MERN stack. BookyVerse allows users to browse, favourite, and purchase books, while admins can manage the entire inventory and order system.

![BookyVerse Banner](https://img.freepik.com/free-vector/mysterious-mafia-man-smoking-cigarette_52683-34828.jpg)

---

## 🌐 Live Demo

> Coming Soon

---

## 📋 Table of Contents

- [About The Project](#about-the-project)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Database Models](#database-models)
- [API Endpoints](#api-endpoints)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Project Structure](#project-structure)
- [Screenshots](#screenshots)
- [Known Issues](#known-issues)
- [Future Work](#future-work)
- [Author](#author)

---

## 📖 About The Project

BookyVerse is a complete end-to-end book e-commerce platform that provides a seamless experience for both readers and administrators.

- **Users** can browse books, manage their favourites and cart, place orders, and track order history
- **Admins** can add, edit, and delete books, and manage all orders with real-time status updates

The project was built to learn and demonstrate real-world full-stack development concepts including JWT authentication, role-based access control, REST API design, global state management with Redux, and responsive UI design with Tailwind CSS.

---

## ✨ Features

### 👤 User Features
- 🔐 Secure signup and login with JWT authentication
- 📚 Browse complete book catalogue with grid layout
- 🔍 View detailed book information (author, description, language, price, genre)
- ❤️ Add and remove books from favourites
- 🛒 Add and remove books from cart
- 💳 Place orders directly from cart
- 📦 View complete order history with status tracking
- 👤 Update profile — phone number and full address
- 🔒 Password validation (uppercase, number, special character required)

### 🛠️ Admin Features
- ➕ Add new books with all details (title, author, price, language, genre, description, image URL)
- ✏️ Edit existing book details
- 🗑️ Delete books from the platform
- 📋 View all orders across all users
- 🔄 Update order status (Pending → OrderPlaced → Shipped → Delivered / Cancelled)

### 🌐 General Features
- 📱 Fully responsive design for mobile and desktop
- ⚡ Fast development with Vite
- 🎨 Animated navbar with role-aware navigation
- ⏳ Loading spinner during all async operations
- 🔄 Authentication state persists across page refreshes
- 🏠 Recently added books section on homepage

---

## 🛠️ Tech Stack

### Backend
| Technology | Version | Purpose |
|---|---|---|
| Node.js | >= 16 | Runtime environment |
| Express.js | ^4.21.1 | REST API framework |
| MongoDB | Cloud/Local | NoSQL database |
| Mongoose | ^8.8.0 | MongoDB ODM |
| bcryptjs | ^2.4.3 | Password hashing |
| jsonwebtoken | ^9.0.2 | JWT authentication |
| cors | ^2.8.5 | Cross-origin requests |
| dotenv | ^16.4.5 | Environment variables |
| multer | ^1.4.5 | File upload handling |
| nodemon | ^3.1.7 | Development auto-restart |

### Frontend
| Technology | Version | Purpose |
|---|---|---|
| React | ^18.3.1 | UI framework |
| Vite | ^5.4.10 | Build tool and dev server |
| React Router DOM | ^6.28.0 | Client-side routing |
| Redux Toolkit | ^2.3.0 | Global state management |
| React Redux | ^9.1.2 | Redux-React bindings |
| Axios | ^1.7.7 | HTTP client |
| Tailwind CSS | ^3.4.14 | Utility-first CSS framework |
| React Icons | ^5.3.0 | Icon library |
| PostCSS | ^8.4.49 | CSS processing |
| Autoprefixer | ^10.4.20 | CSS vendor prefixing |

---

---

## 🗄️ Database Models

### User Model
```javascript
{
  username: String (unique, required),
  email: String (unique, required),
  password: String (hashed, required),
  address: {
    street: String,
    city: String,
    state: String,
    postalCode: String,
    country: String
  },
  phoneNumber: String,
  avatar: String (default image URL),
  role: String (enum: ["user", "admin"], default: "user"),
  favourites: [ObjectId → Book],
  cart: [ObjectId → Book],
  orders: [ObjectId → Order],
  timestamps: true
}
```

### Book Model
```javascript
{
  url: String (required),        // Image URL
  title: String (required),
  author: String (required),
  price: Number (required),
  desc: String (required),
  language: String (required),
  genre: String (required),
  timestamps: true
}
```

### Order Model
```javascript
{
  user: ObjectId → User,
  book: ObjectId → Book,
  quantity: Number (default: 1),
  status: String (enum: [
    "OrderPlaced",
    "Shipped", 
    "Pending",
    "Delivered",
    "Cancelled"
  ], default: "Pending"),
  timestamps: true
}
```

---


## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:
- [Node.js](https://nodejs.org/) >= 16.0.0
- [npm](https://www.npmjs.com/) >= 8.0.0
- [MongoDB](https://www.mongodb.com/) (local or MongoDB Atlas account)
- [Git](https://git-scm.com/)

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/bookyverse.git
cd bookyverse
```

**2. Setup the Backend**
```bash
cd Backend
npm install
```

**3. Setup the Frontend**
```bash
cd ../Frontend
npm install
```

**4. Configure environment variables**

Create a `.env` file inside the `Backend` folder:
```env
PORT=1000
URL=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
```

**5. Run the Backend**
```bash
cd Backend
npm start
```
> Server starts at `http://localhost:1000`

**6. Run the Frontend**
```bash
cd Frontend
npm run dev
```
> App starts at `http://localhost:5173`

---

## 🔐 Environment Variables

### Backend (`Backend/.env`)

| Variable | Description | Example |
|---|---|---|
| `PORT` | Port for the Express server | `1000` |
| `URL` | MongoDB connection string | `mongodb+srv://user:pass@cluster.mongodb.net/bookyverse` |
| `JWT_SECRET` | Secret key for signing JWT tokens | `your_super_secret_key_here` |

> ⚠️ Never commit your `.env` file. It is already listed in `.gitignore`.

---

