# DummyJSON

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/Node.js-%3E%3D24-brightgreen?logo=node.js)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-4.x-blue?logo=express)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB%20%7C%20In--Memory-green?logo=mongodb)](https://www.mongodb.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker)](https://www.docker.com/)

**DummyJSON** is a high-performance, open-source RESTful API service built with **Node.js** and **Express** that delivers realistic placeholder JSON data and media assets on demand. Designed for frontend engineers, mobile developers, QA testers, and educators, it eliminates the wait for backend APIs during client-side development, prototyping, and UI testing.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Why DummyJSON?](#-why-dummyjson)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation & Setup](#installation--setup)
  - [Environment Variables](#environment-variables)
  - [Running with Docker](#running-with-docker)
- [API Reference & Usage Examples](#-api-reference--usage-examples)
  - [1. Fetching Products](#1-fetching-products)
  - [2. Search & Filtering](#2-search--filtering)
  - [3. Pagination](#3-pagination)
  - [4. Simulating Network Delays](#4-simulating-network-delays)
  - [5. Authentication (JWT)](#5-authentication-jwt)
  - [6. Placeholder Image Generator](#6-placeholder-image-generator)
  - [7. Identicon Avatar Generator](#7-identicon-avatar-generator)
  - [8. Mock HTTP Status Responses](#8-mock-http-status-responses)
- [Available Resources](#-available-resources)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🚀 Overview

During frontend or mobile application development, teams frequently face bottlenecks: backend APIs are not yet ready, third-party staging environments are unstable or rate-limited, and test data is inconsistent.

**DummyJSON** solves these challenges by providing a full-featured mock API server that behaves like a production backend:
- Returns structured JSON payloads across multiple domains (e-commerce, social, users, etc.).
- Simulates real-world conditions including network latency, pagination, authentication tokens, and error responses.
- Generates custom placeholder images and SVG identicons dynamically on the fly.
- Works offline or locally without any mandatory external cloud dependencies.

---

## 💡 Why DummyJSON?

- **Zero-Friction Prototyping**: Build and test UI components without writing a single line of backend boilerplate.
- **Realistic Data Models**: Pre-loaded with comprehensive mock datasets containing IDs, relations, timestamps, and realistic images.
- **Network Latency Simulation**: Test loading spinners, skeleton screens, and async states using customizable delay parameters.
- **Stateless & Extensible**: Works seamlessly with React, Next.js, Vue, Angular, Svelte, React Native, Flutter, Swift, Kotlin, and vanilla JavaScript.
- **Docker-Ready**: Easy container deployment for local dev environments or internal team servers.

---

## ✨ Key Features

- **📦 10+ Pre-populated Resources**: Over 2,500+ records covering Products, Users, Carts, Posts, Comments, Quotes, Recipes, and Todos.
- **🔍 Search & Query Filtering**: Full-text keyword search and category filtering out of the box.
- **📑 Flexible Pagination**: Support for `limit` and `skip` query parameters for list endpoints.
- **⏱️ Delay Simulation**: Pass `?delay=ms` to simulate realistic slow networks or test race conditions.
- **🔐 JWT Authentication**: Simulate authentication flows with `/auth/login` and verify bearer tokens on protected endpoints.
- **🎨 Dynamic Image Generation**: Generate customizable placeholder images with custom dimensions, colors, text, and 14+ supported fonts.
- **👤 Identicon Generator**: Deterministic identicon avatar generation based on hash strings using Jdenticon.
- **🚦 Custom HTTP Response Codes**: Request mock status codes (200, 400, 401, 404, 500, etc.) to validate client-side error handling.
- **⚡ In-Memory & Database Support**: Runs instantly using in-memory mock datasets or connects to MongoDB via Mongoose for persistence.

---

## 🛠️ Tech Stack

- **Runtime**: [Node.js](https://nodejs.org/) (ES Modules, `>= 24.x`)
- **Web Framework**: [Express 4.x](https://expressjs.com/)
- **Database / ODM**: [MongoDB](https://www.mongodb.com/) & [Mongoose 8.x](https://mongoosejs.com/)
- **Authentication**: [JSON Web Tokens (jsonwebtoken)](https://github.com/auth0/node-jsonwebtoken)
- **Image Processing**: [Sharp](https://sharp.pixelplumbing.com/) & [Jdenticon](https://jdenticon.com/)
- **Caching**: [node-cache](https://github.com/node-cache/node-cache)
- **Containerization**: [Docker](https://www.docker.com/)
- **Security & Utilities**: Helmet, CORS, Express Rate Limit, Winston logger

---

## 📂 Project Structure

```text
DummyJSON/
├── database/            # Pre-seeded JSON datasets and database helpers
├── fonts/               # Bundled font assets for dynamic image generation
├── public/              # Static frontend assets (styles, scripts, images)
├── raw/                 # Raw seed datasets
├── scripts/             # Build and maintenance scripts
├── src/
│   ├── aws/             # AWS S3 integration utilities
│   ├── constants/       # Global constants and route configurations
│   ├── controllers/     # Route controller logic for each resource
│   ├── db/              # Mongoose and in-memory connection handlers
│   ├── helpers/         # Formatting, response, and pagination helpers
│   ├── middleware/      # Authentication, rate limiting, and error handling
│   ├── models/          # Data schemas and representations
│   ├── routes/          # Express route definitions
│   └── utils/           # Utility functions (cron, image, logging)
├── views/               # EJS template views
├── .env.example         # Example environment configuration
├── Dockerfile           # Production container configuration
├── index.js             # Application entry point
├── package.json         # Dependencies and project metadata
└── README.md            # Project documentation
```

---

## 🏁 Getting Started

### Prerequisites

Ensure you have the following installed on your local machine:
- **Node.js**: `v24.0.0` or higher ([Download](https://nodejs.org/))
- **npm** (comes with Node.js) or **yarn**
- *(Optional)* **MongoDB**: Local or hosted MongoDB instance (MongoDB is optional; DummyJSON loads mock data in-memory on boot)
- *(Optional)* **Docker**: For running containerized instances

### Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/prathmeshpatil-it/DummyJSON.git
   cd DummyJSON
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**
   ```bash
   cp .env.example .env
   ```
   *(Update the values in `.env` if you wish to configure a custom port, MongoDB URI, or JWT secret).*

4. **Start the development server:**
   ```bash
   npm run dev
   ```
   The application will start on `http://localhost:8888`.

5. **Start in production mode:**
   ```bash
   npm start
   ```

---

### Environment Variables

| Variable | Default Value | Description |
| :--- | :--- | :--- |
| `PORT` | `8888` | The port the HTTP server listens on |
| `NODE_ENV` | `development` | Environment mode (`development` / `production`) |
| `LOG_ENABLED` | `true` | Enable or disable request logging |
| `MONGODB_URI` | `mongodb://localhost:27017` | MongoDB connection connection string |
| `MONGODB_DB_NAME` | `dummyjson-test-db` | MongoDB database name |
| `JWT_SECRET` | `A_VERY_SECRET_KEY` | Secret key used for signing JWT auth tokens |

---

### Running with Docker

You can easily run DummyJSON in an isolated Docker container:

1. **Build the Docker image:**
   ```bash
   docker build -t dummyjson:latest .
   ```

2. **Run the container:**
   ```bash
   docker run -p 8888:8888 --name dummyjson-app dummyjson:latest
   ```

3. Open your browser or API client and visit `http://localhost:8888`.

---

## 📖 API Reference & Usage Examples

### 1. Fetching Products

Retrieve all products or a single product by ID:

```javascript
// Fetch all products
const res = await fetch('http://localhost:8888/products');
const data = await res.json();
console.log(data.products);

// Fetch a single product
const singleRes = await fetch('http://localhost:8888/products/1');
const product = await singleRes.json();
console.log(product);
```

### 2. Search & Filtering

Search resources using the `q` query parameter:

```javascript
// Search products matching query "phone"
const res = await fetch('http://localhost:8888/products/search?q=phone');
const results = await res.json();
console.log(results);
```

### 3. Pagination

Control response size and page offset using `limit` and `skip`:

```javascript
// Retrieve 10 products, skipping the first 10
const res = await fetch('http://localhost:8888/products?limit=10&skip=10');
const paged = await res.json();
console.log(paged);
```

### 4. Simulating Network Delays

Simulate slow network latency by adding `?delay=MILLISECONDS`:

```javascript
// Delays response by 2 seconds (2000 ms)
const res = await fetch('http://localhost:8888/products?delay=2000');
const data = await res.json();
```

### 5. Authentication (JWT)

Simulate user login and request an authentication token:

```javascript
const response = await fetch('http://localhost:8888/auth/login', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    username: 'kminchelle',
    password: '0lelpass',
    expiresInMins: 30, // optional
  }),
});

const user = await response.json();
console.log('JWT Token:', user.token);
```

### 6. Placeholder Image Generator

Generate customized placeholder images directly via URL:

```text
http://localhost:8888/image/{width}x{height}/{background_color}/{text_color}?text={label}
```

**Examples:**
- `http://localhost:8888/image/300x200`
- `http://localhost:8888/image/400x250/282c34/ffffff?text=Product+Thumbnail`

### 7. Identicon Avatar Generator

Generate deterministic identicons based on any unique hash or username:

```text
http://localhost:8888/icon/{hash}/{size}
```

**Example:**
- `http://localhost:8888/icon/user123/150`

### 8. Mock HTTP Status Responses

Test your front-end error handlers against arbitrary HTTP status codes:

```javascript
// Will return HTTP 404 status with custom message
const res = await fetch('http://localhost:8888/http/404');
console.log(res.status); // 404
```

---

## 📊 Available Resources

| Resource | Endpoint | Description |
| :--- | :--- | :--- |
| **Products** | `/products` | E-commerce items with ratings, reviews, stock, categories |
| **Users** | `/users` | User profiles with contact info, addresses, credentials |
| **Carts** | `/carts` | Shopping carts associated with users and items |
| **Posts** | `/posts` | Social media posts with tags, reactions, and views |
| **Comments** | `/comments` | User comments linked to posts |
| **Quotes** | `/quotes` | Inspirational and philosophical quotes with authors |
| **Recipes** | `/recipes` | Cooking recipes with ingredients, instructions, cuisine types |
| **Todos** | `/todos` | Task lists with completion flags |
| **Auth** | `/auth/login` | Authentication endpoint returning user info & JWT token |
| **Images** | `/image` | Dynamic custom placeholder image generator |
| **Icons** | `/icon` | Dynamic SVG / PNG identicon generator |
| **HTTP Mock** | `/http/:code` | Returns requested HTTP status code |

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing new feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.
