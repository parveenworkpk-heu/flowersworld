# Flowers World - Complete Website Documentation

## Table of Contents
1. [Project Overview](#project-overview)
2. [Technology Stack](#technology-stack)
3. [Project Structure](#project-structure)
4. [Installation & Setup](#installation--setup)
5. [Frontend Features](#frontend-features)
6. [Backend Features](#backend-features)
7. [Database Schema](#database-schema)
8. [Admin Panel Guide](#admin-panel-guide)
9. [User Account Features](#user-account-features)
10. [API Endpoints](#api-endpoints)
11. [Deployment Guide](#deployment-guide)
12. [Troubleshooting](#troubleshooting)

---

## 1. Project Overview

**Project Name:** Flowers World
**Project Type:** E-Commerce Web Application
**Core Functionality:** Online flower shop with product catalog, shopping cart, user accounts, order management, and admin dashboard
**Target Users:** Customers seeking flowers online, Shop administrators

---

## 2. Technology Stack

### Frontend
- **Framework:** React 18
- **Styling:** Tailwind CSS
- **Animations:** Framer Motion
- **Routing:** React Router v6
- **HTTP Client:** Axios
- **Icons:** Lucide React
- **SEO:** React Helmet Async

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB (Mongoose)
- **Authentication:** JWT (JSON Web Tokens)
- **Password Hashing:** bcryptjs

### Development Tools
- **Package Manager:** npm
- **Build Tool:** Create React App

---

## 3. Project Structure

```
FlowersWorld/
├── client/                    # React Frontend
│   ├── public/
│   │   └── index.html       # HTML template
│   ├── src/
│   │   ├── components/      # Reusable components
│   │   │   ├── Header.js    # Navigation header
│   │   │   ├── Footer.js   # Footer component
│   │   │   ├── CartDrawer.js   # Shopping cart slide-out
│   │   │   ├── ProductCard.js # Product display card
│   │   │   ├── ProtectedRoute.js # Auth protection
│   │   │   └── AdminRoute.js  # Admin protection
│   │   ├── pages/           # Page components
│   │   │   ├── Home.js     # Landing page
│   │   │   ├── Shop.js     # Product listing
│   │   │   ├── ProductDetail.js # Product details
│   │   │   ├── About.js    # About page
│   │   │   ├── Contact.js  # Contact form
│   │   │   ├── Checkout.js # Order placement
│   │   │   ├── Login.js    # User login
│   │   │   ├── Register.js # User registration
│   │   │   ├── Account.js  # User dashboard
│   │   │   ├── AdminDashboard.js # Admin analytics
│   │   │   ├── AdminOrders.js # Order management
│   │   │   ├── AdminProducts.js # Product CRUD
│   │   │   └── AdminUsers.js  # User management
│   │   ├── context/         # React contexts
│   │   │   ├── AuthContext.js # User authentication
│   │   │   └── CartContext.js # Shopping cart
│   │   ├── utils/          # Utility functions
│   │   │   └── helpers.js  # Formatting & validation
│   │   ├── App.js          # Main app component
│   │   ├── index.js        # Entry point
│   │   └── index.css       # Global styles
│   ├── package.json
│   ├── tailwind.config.js
│   └── postcss.config.js
│
├── server/                   # Express Backend
│   ├── config/
│   │   └── db.js          # Database connection
│   ├── routes/            # API routes
│   │   ├── auth.js       # Authentication routes
│   │   ├── products.js   # Product routes
│   │   ├── orders.js     # Order routes
│   │   ├── cart.js       # Cart routes
│   │   └── admin.js      # Admin routes
│   ├── server.js          # Server entry point
│   ├── data.json         # File-based database
│   ├── package.json
│   └── .env              # Environment variables
│
├── SPEC.md                  # Project specification
├── README.md               # Project readme
└── installation.txt        # Quick setup guide
```

---

## 4. Installation & Setup

### Prerequisites
- Node.js v18 or higher
- MongoDB Atlas account (or local MongoDB)

### Backend Setup
```bash
cd server
npm install
# Create .env file with MongoDB URI
npm start
```

### Frontend Setup
```bash
cd client
npm install
# Create .env file with API URL
npm start
```

### Access Points
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000/api

---

## 5. Frontend Features

### Header Component
- **Logo:** "FlowersWorld" with gold accent
- **Navigation:** Home, Shop, About, Contact links
- **Search Bar:** Expandable search with debounce (300ms)
- **User Menu:** Dropdown with orders, account, logout
- **Wishlist:** Heart icon with badge count
- **Cart Icon:** Shopping bag with slide-out drawer
- **Mobile Menu:** Hamburger menu for responsive design
- **Glassmorphism Effect:** On scroll, header becomes translucent

### Home Page (`/`)
1. **Hero Section**
   - Full viewport height carousel
   - 3 background images with crossfade transition
   - Glassmorphic text container
   - "Blooming Beauty Delivered" heading
   - "Shop Now" and "Know More" CTAs
   - Smooth animations on load

2. **Latest Products Section**
   - Bento grid layout (responsive)
   - Product cards with hover effects:
     - Image zoom (1.1x scale)
     - Quick view overlay
     - Add to cart button
     - Wishlist button
   - "View All Products" link

3. **FAQ/CTA Section**
   - "Have Any Questions?" heading
   - "Contact Us" button

### Shop Page (`/shop`)
- **Sidebar Filters:**
  - Category selection
  - Price range (min/max)
  - Sort options (Newest, Price, Popularity)
- **Product Grid:** 3 columns desktop, 2 tablet, 1 mobile
- **Pagination:** Page navigation
- **Mobile Filters:** Slide-out drawer

### Product Detail Page (`/product/:id`)
- **Image Gallery:** Main image + thumbnail carousel
- **Product Info:**
  - Category, Name, Ratings
  - Price (with discount strikethrough)
  - Stock status indicator
  - Quantity selector (+/-)
- **Add to Cart:** With loading state
- **Tabs:**
  - Description
  - Care Instructions
- **Related Products:** Carousel

### About Page (`/about`)
- **Stats Counter Animation:**
  - Years of Service
  - Happy Customers
  - Bouquets Delivered
  - Expert Florists
- **Timeline:** Scroll-triggered animations
- **Team Section:** Florist profiles
- **CTA:** "Ready to Create Something Beautiful?"

### Contact Page (`/contact`)
- **Split Layout:**
  - Left: Contact form (Name, Email, Phone, Message)
  - Right: Contact information + Business hours
- **Form Validation:** Real-time with error states
- **Live Validation:**
  - Email format check
  - Phone 10-digit check

### Checkout Page (`/checkout`)
- **Step 1 - Shipping Details:**
  - Full Name, Phone, Email
  - Address, City, State, Pincode
  - Validation with error messages

- **Step 2 - Payment Method:**
  - Cash on Delivery (default)
  - UPI Payment option
  - UPI ID display for UPI method

- **Order Summary:**
  - Cart items with images
  - Subtotal calculation
  - Shipping cost (Free above ₹500)
  - Total amount
  - Quantity adjust in summary

- **Place Order Button:**
  - Loading state
  - Success animation
  - Order confirmation page

### User Account Section (`/account`)

**My Orders (`/account/orders`)**
- Order list with:
  - Order ID, Date, Items, Total, Status
  - Status badges (color-coded)
  - Order details expansion
  - Shipping address display

**Account Details (`/account/details`)**
- Editable profile form:
  - Name, Email, Phone
  - Password change section

**Addresses (`/account/addresses`)**
- Add new address form
- Edit existing addresses
- Delete addresses (with confirmation)
- Address list with cards

### Authentication Pages
- **Login (`/login`):**
  - Email/Password fields
  - Show/hide password toggle
  - "Sign Up" link
  - Error messages

- **Register (`/register`):**
  - Name, Email, Phone, Password
  - Password visibility toggle
  - Validation feedback

---

## 6. Backend Features

### Authentication System
- User registration with validation
- Login with JWT token generation
- Token stored in localStorage
- Protected routes middleware
- Token expiration: 7 days

### Product Management
- CRUD operations (file-based storage)
- Search with pagination
- Category filtering
- Price range filtering
- Sort by (price, date, ratings)
- Featured products flag

### Order Management
- Create order from cart
- Order status tracking
- User order history
- Admin order management

### Cart System
- In-memory cart storage
- Add/remove/update quantities
- Product details retrieval
- Clear cart functionality

### Admin Panel APIs
- Dashboard analytics
- Product CRUD
- Order status updates
- User management (block/unblock)

---

## 7. Database Schema

### User Schema
```javascript
{
  _id: String,
  name: String,
  email: String (unique),
  password: String (hashed),
  phone: String,
  addresses: [{
    name: String,
    phone: String,
    address: String,
    city: String,
    state: String,
    pincode: String
  }],
  role: 'user' | 'admin',
  isBlocked: Boolean,
  createdAt: Date
}
```

### Product Schema
```javascript
{
  _id: String,
  name: String,
  description: String,
  price: Number,
  discountPrice: Number,
  images: [String],
  category: String,
  stock: Number,
  ratings: Number,
  isFeatured: Boolean,
  isActive: Boolean,
  createdAt: Date
}
```

### Order Schema
```javascript
{
  _id: String,
  user: String (userId),
  items: [{
    product: String,
    name: String,
    quantity: Number,
    price: Number,
    image: String
  }],
  shippingDetails: {
    name, phone, address, city, state, pincode
  },
  paymentMethod: 'COD' | 'UPI',
  status: 'Pending' | 'Processing' | 'Shipped' | 'Delivered',
  totalAmount: Number,
  createdAt: Date
}
```

---

## 8. Admin Panel Guide

### Access
- URL: `/admin`
- Requires admin role
- Login with admin credentials

### Dashboard (`/admin`)
**KPIs (Key Performance Indicators):**
- Total Revenue (₹)
- Active Users count
- Pending Orders count
- Total Orders count

**Charts:**
- Orders over time (Line chart)
- Payment methods (Pie chart)
- Top selling products (Bar chart)

### Products Management (`/admin/products`)
- **Add Product:**
  - Name, Description
  - Price, Discount Price
  - Category selection
  - Stock quantity
  - Multiple image URLs
  
- **Edit Product:** Pre-filled form
- **Delete Product:** Soft delete (isActive: false)
- **Search:** Filter by name/category

### Orders Management (`/admin/orders`)
- **View All Orders:** Table with pagination
- **Filter by Status:** Pending, Processing, Shipped, Delivered
- **Update Status:** Dropdown to change order status
- **Export CSV:** Download orders data
- **Order Details:** Expandable rows

### Users Management (`/admin/users`)
- **View Users:** Table with search
- **Filter:** Active/Blocked users
- **Block/Unblock:** Toggle user access
- **User Details:** Name, Email, Phone, Last Active

---

## 9. User Account Features

### Registration Flow
1. Navigate to `/register`
2. Fill: Name, Email, Phone, Password
3. Submit → Token stored → Redirect to home

### Login Flow
1. Navigate to `/login`
2. Enter credentials
3. Submit → Token stored → Redirect to previous page

### Order Placement Flow
1. Add products to cart
2. Navigate to `/checkout`
3. Fill shipping details
4. Select payment method
5. Click "Place Order"
6. Success page with Order ID
7. Order appears in My Orders

### Address Management Flow
1. Navigate to `/account/addresses`
2. Click "Add New Address"
3. Fill form (Name, Phone, Address, City, State, Pincode)
4. Save → Address list updates
5. Edit/Delete existing addresses

---

## 10. API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|-----------|--------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login user |
| GET | `/api/auth/me` | Get current user |
| PUT | `/api/auth/profile` | Update user profile |

### Products
| Method | Endpoint | Description |
|--------|-----------|--------------|
| GET | `/api/products` | List products (with filters) |
| GET | `/api/products/featured` | Get featured products |
| GET | `/api/products/categories` | Get categories |
| GET | `/api/products/:id` | Get product details |
| POST | `/api/products` | Create product (admin) |
| PUT | `/api/products/:id` | Update product (admin) |
| DELETE | `/api/products/:id` | Delete product (admin) |

### Orders
| Method | Endpoint | Description |
|--------|-----------|--------------|
| POST | `/api/orders` | Create order |
| GET | `/api/orders/my-orders` | Get user orders |
| GET | `/api/orders/:id` | Get order details |

### Cart
| Method | Endpoint | Description |
|--------|-----------|--------------|
| GET | `/api/cart` | Get cart items |
| POST | `/api/cart/add` | Add to cart |
| PUT | `/api/cart/:itemId` | Update quantity |
| DELETE | `/api/cart/:itemId` | Remove item |
| DELETE | `/api/cart` | Clear cart |

### Admin
| Method | Endpoint | Description |
|--------|-----------|--------------|
| GET | `/api/admin/analytics` | Get dashboard data |
| GET | `/api/admin/users` | List all users |
| PATCH | `/api/admin/users/:id/toggle-block` | Block/unblock user |
| GET | `/api/admin/stats` | Get stats |
| GET | `/api/admin/orders` | List all orders |
| PATCH | `/api/admin/orders/:id/status` | Update order status |

---

## 11. Deployment Guide

### Option 1: Vercel + Render (Recommended)

**Frontend (Vercel):**
1. Create Vercel account
2. Connect GitHub repository
3. Set build command: `npm run build`
4. Set output directory: `build`
5. Add environment variable: `REACT_APP_API_URL`

**Backend (Render):**
1. Create Render account
2. Connect GitHub repository
3. Create Web Service
4. Set root directory: `server`
5. Add environment variables

### Option 2: Netlify + Railway

**Frontend (Netlify):**
1. Run `npm run build` in client
2. Upload build folder to Netlify
3. Set environment variables

**Backend (Railway):**
1. Create Railway account
2. Add MongoDB plugin
3. Deploy from GitHub

### Option 3: Firebase + Cloud Run

---

## 12. Troubleshooting

### Common Issues & Solutions

| Issue | Solution |
|-------|-----------|
| Port already in use | Kill process or use different port |
| MongoDB connection failed | Check Atlas network access |
| CORS errors | Add frontend domain to cors middleware |
| Token expired | Re-login |
| Admin access denied | Manually change role in database |
| Images not loading | Check image URLs are valid |

---

## 13. Color Palette

| Color | Hex Code | Usage |
|-------|----------|-------|
| Primary | #C73086 | Buttons, CTAs, accents |
| Secondary | #FF6B6B | Alerts, highlights |
| Soft Pink | #FFB6C1 | Decorations |
| Cream | #FFF9E6 | Background accents |
| Sage | #8B9A7D | Secondary accents |
| Gold | #D4AF37 | Premium highlights |
| Dark | #212529 | Text |
| Light | #FAFAFA | Backgrounds |

---

## 14. Animation Specifications

- **Page Transitions:** Fade + slide up (0.3s ease-out)
- **Product Cards:** Hover lift (-8px translateY)
- **Cart Drawer:** Slide from right (spring physics)
- **Button:** Scale 0.98 on click
- **Hero:** Crossfade 1s transition

---

*Document Version: 1.0*
*Last Updated: April 2026*