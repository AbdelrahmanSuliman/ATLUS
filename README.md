# ATLUS - Modern Ecommerce Platform

<div align="center">
  <img src="https://img.shields.io/badge/Next.js-15.3.5-black?style=for-the-badge&logo=next.js" alt="Next.js" />
  <img src="https://img.shields.io/badge/React-19.0.0-blue?style=for-the-badge&logo=react" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript-5.8.3-blue?style=for-the-badge&logo=typescript" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Node.js-18-alpine-green?style=for-the-badge&logo=node.js" alt="Node.js" />
  <img src="https://img.shields.io/badge/PostgreSQL-16-blue?style=for-the-badge&logo=postgresql" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Prisma-6.11.1-black?style=for-the-badge&logo=prisma" alt="Prisma" />
  <img src="https://img.shields.io/badge/Stripe-18.4.0-blue?style=for-the-badge&logo=stripe" alt="Stripe" />
  <img src="https://img.shields.io/badge/TailwindCSS-4.1.11-38B2AC?style=for-the-badge&logo=tailwind-css" alt="TailwindCSS" />
</div>

<br>

A modern, full-stack ecommerce platform built with Next.js, Node.js, and TypeScript. ATLUS features a beautiful UI, secure authentication, real-time cart management, and seamless payment processing with Stripe.

## ✨ Features

### 🛍️ **Ecommerce Functionality**
- **Product Catalog** with seasonal collections (Summer, Winter, Kids, Comfort)
- **Advanced Filtering** by collection and price sorting
- **Shopping Cart** with real-time updates using Zustand state management
- **Secure Checkout** powered by Stripe payment processing
- **Order Management** with status tracking (Pending/Completed)

### 🔐 **Authentication & Security**
- **JWT-based Authentication** with secure token management
- **Google OAuth 2.0** integration for social login
- **Role-based Access Control** (User/Admin roles)
- **Password Hashing** with bcrypt
- **Rate Limiting** to prevent abuse
- **CORS Protection** for secure API communication

### 🎨 **User Experience**
- **Responsive Design** optimized for all devices
- **Smooth Animations** with Framer Motion
- **Modern UI/UX** with TailwindCSS
- **Toast Notifications** for user feedback
- **Loading States** and error handling
- **Image Optimization** with AWS S3 integration

### 🚀 **Performance & Scalability**
- **TypeScript** for type safety and better development experience
- **Prisma ORM** for efficient database operations
- **Docker Containerization** for easy deployment
- **Structured Logging** with Pino
- **API Rate Limiting** for stability

## 🏗️ Architecture

```
ATLUS/
├── ATLUS-backend/          # Node.js + Express API
│   ├── src/
│   │   ├── controllers/    # Business logic
│   │   ├── middleware/     # Auth, rate limiting, S3
│   │   ├── routes/         # API endpoints
│   │   ├── services/       # External integrations
│   │   └── utils/          # Helpers and utilities
│   ├── prisma/             # Database schema and migrations
│   └── docker-compose.yml  # Development environment
└── ATLUS-frontend/         # Next.js React application
    ├── src/
    │   ├── components/     # Reusable UI components
    │   ├── pages/          # Next.js pages
    │   ├── stores/         # Zustand state management
    │   ├── api/            # API client functions
    │   └── types/          # TypeScript type definitions
    └── public/             # Static assets
```

## 🛠️ Tech Stack

### Frontend
- **Next.js 15.3.5** - React framework with SSR
- **React 19.0.0** - UI library
- **TypeScript 5.8.3** - Type safety
- **TailwindCSS 4.1.11** - Utility-first CSS framework
- **Framer Motion** - Animation library
- **Zustand** - State management
- **Axios** - HTTP client
- **React Hot Toast** - Notifications
- **Stripe.js** - Payment processing

### Backend
- **Node.js 18** - Runtime environment
- **Express.js 5.1.0** - Web framework
- **TypeScript 5.8.3** - Type safety
- **Prisma 6.11.1** - Database ORM
- **PostgreSQL 16** - Database
- **JWT** - Authentication
- **Passport.js** - OAuth authentication
- **Stripe 18.4.0** - Payment processing
- **AWS S3** - File storage
- **Pino** - Logging
- **Zod** - Schema validation

### DevOps
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- Docker and Docker Compose
- PostgreSQL (or use Docker)
- Stripe account
- AWS S3 bucket (optional)

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/ATLUS.git
cd ATLUS
```

### 2. Backend Setup
```bash
cd ATLUS-backend

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Run database migrations
npx prisma migrate dev

# Start development server
npm run dev
```

### 3. Frontend Setup
```bash
cd ATLUS-frontend

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Start development server
npm run dev
```

### 4. Using Docker (Alternative)
```bash
# From the backend directory
docker-compose up -d

# The API will be available at http://localhost:5050
# PostgreSQL will be available at localhost:5432
```

## 📁 Environment Variables

### Backend (.env)
```env
DATABASE_URL="postgresql://username:password@localhost:5432/atlus_db"
JWT_SECRET="your-jwt-secret"
STRIPE_SECRET_KEY="sk_test_..."
STRIPE_WEBHOOK_SECRET="whsec_..."
AWS_ACCESS_KEY_ID="your-aws-access-key"
AWS_SECRET_ACCESS_KEY="your-aws-secret-key"
AWS_REGION="us-east-1"
AWS_S3_BUCKET="your-s3-bucket"
GOOGLE_CLIENT_ID="your-google-client-id"
GOOGLE_CLIENT_SECRET="your-google-client-secret"
FRONTEND_URL="http://localhost:3000"
PORT=5000
```

### Frontend (.env.local)
```env
NEXT_PUBLIC_API_URL="http://localhost:5000/api"
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_..."
NEXT_PUBLIC_GOOGLE_CLIENT_ID="your-google-client-id"
```

## 🗄️ Database Schema

The application uses PostgreSQL with the following main entities:

- **Users** - Authentication and user management
- **Products** - Product catalog with collections
- **Orders** - Customer orders with status tracking
- **OrderItems** - Individual items in orders

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/login` - User login
- `POST /api/auth/signup` - User registration
- `GET /api/auth/google` - Google OAuth

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get product by ID
- `POST /api/products` - Create product (Admin)
- `PUT /api/products/:id` - Update product (Admin)
- `DELETE /api/products/:id` - Delete product (Admin)

### Orders
- `GET /api/orders` - Get user orders
- `POST /api/orders` - Create order
- `PUT /api/orders/:id` - Update order status

### Users
- `GET /api/users/me` - Get current user
- `PUT /api/users/me` - Update user profile

## 🎯 Key Features in Detail

### Shopping Experience
- Browse products by seasonal collections
- Filter and sort products by price
- Add items to cart with quantity management
- Secure checkout with Stripe integration
- Order history and status tracking

### Admin Features
- Product management (CRUD operations)
- Order status management
- User role management
- File upload to AWS S3

### Security Features
- JWT token-based authentication
- Password hashing with bcrypt
- Rate limiting on API endpoints
- CORS protection
- Input validation with Zod schemas

## 🚀 Deployment

### Backend Deployment
```bash
# Build the application
npm run build

# Start production server
npm start
```

### Frontend Deployment
```bash
# Build for production
npm run build

# Start production server
npm start
```

### Docker Deployment
```bash
# Build and run with Docker Compose
docker-compose up -d --build
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the APACHE License - see the [LICENSE](LICENSE) file for details.
