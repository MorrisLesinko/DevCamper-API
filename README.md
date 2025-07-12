# DevCamper API

## Table of Contents

- [Description](#description)
- [Features](#features)
- [Technologies](#technologies)
- [Installation](#installation)
- [API Documentation](#api-documentation)
- [Infrastructure Design](#infrastructure-design)
- [Infrastructure Details](#infrastructure-details)
  - [VPC and Subnets](#vpc-and-subnets)
  - [Components](#components)
  - [Data Flow](#data-flow)
  - [Network Security](#network-security)
- [Author](#author)

---

## Description

DevCamper is a RESTful API that provides a platform for bootcamps, courses, reviews and users. It supports full CRUD operations, user authentication, image uploads, geolocation search, filtering, and advanced security features. The API is documented using Postman and is deployed on AWS infrastructure.

---

## Features

- ✅ CRUD for bootcamps, courses, users, and reviews  
- ✅ Role-based authentication with JWT  
- ✅ Image/file upload  
- ✅ Password encryption with bcryptjs  
- ✅ Geolocation and map search  
- ✅ Filtering, sorting, and pagination  
- ✅ Secure API (CORS, Helmet, XSS-clean, Rate Limiting)  
- ✅ Redis-based caching  
- ✅ Mail stream and worker  
- ✅ API documentation with Postman

---

## Technologies

- [Node.js](https://nodejs.org/)
- [Express.js](https://expressjs.com/)
- [MongoDB](https://www.mongodb.com/)
- [Mongoose](https://mongoosejs.com/)
- [JWT](https://jwt.io/)
- [BcryptJS](https://www.npmjs.com/package/bcryptjs)
- [express-fileupload](https://www.npmjs.com/package/express-fileupload)
- [node-geocoder](https://www.npmjs.com/package/node-geocoder)
- [helmet](https://www.npmjs.com/package/helmet)
- [hpp](https://www.npmjs.com/package/hpp)
- [cors](https://www.npmjs.com/package/cors)
- [express-mongo-sanitize](https://www.npmjs.com/package/express-mongo-sanitize)
- [AWS EC2](https://aws.amazon.com/ec2/)

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/MorrisLesinko/DevCamper-API.git
cd DevCamper-API
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables in `.env`

```env
PORT=3001

MONGO_URI=your_mongo_connection_string

JWT_COOKIE_EXPIRE=30d
JWT_SECRET=your_jwt_secret
JWT_EXPIRE=30d

GEOCODER_PROVIDER=mapquest
GEOCODER_API_KEY=your_mapquest_api_key

REDIS_SET_EXPIRE=3600
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=your_redis_password
```

### 4. Seed the database

```bash
node seeder -i
```

### 5. Start the server

```bash
npm start
```

### 6. Visit the app

```
http://localhost:3001
```

---

## API Documentation

- 📍 Local: `http://localhost:3001`
- 🌍 Live: `https://51.21.253.85`
- 🧾 Postman Docs: [Postman API](https://documenter.getpostman.com/view/33408943/2sAYkBsghW)

---

## Infrastructure Design

![Infrastructure Diagram](Devcamper%20Architectural%20Diagram%20with%20region.png)

---

## Infrastructure Details

### VPC and Subnets

- **VPC**: Isolated cloud environment for secure architecture  
- **Public Subnet (10.0.0.0/24)**: Web server, open to users  
- **Private Subnet (10.0.2.0/24)**: Redis, DB, background workers

### Components

- **Web Server** (Public): Handles API requests  
- **Redis** (Private): Stores frequently accessed data and queues  
- **Mail Stream & Worker** (Private): Processes user notification emails  
- **MongoDB** (Private): Main NoSQL data storage

### Data Flow

1. User sends request to server  
2. Server reads from Redis or DB  
3. Mail events added to stream  
4. Worker processes mail stream  
5. Response returned to user

### Network Security

- ✅ Public subnet allows secure user access  
- ✅ Private subnet completely isolated  
- ✅ IAM roles & security groups used for protection

---

## Author

**Lesinko Sipitiek**  
- 💼 GitHub: [@MorrisLesinko](https://github.com/MorrisLesinko)  
- 🌐 LinkedIn: [linkedin.com/in/morrislesinko-3796082a2](https://linkedin.com/in/morrislesinko-3796082a2)

---
