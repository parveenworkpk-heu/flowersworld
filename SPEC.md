# Flowers World - E-Commerce Application Specification

## Project Overview
- **Project Name:** Flowers World
- **Type:** Full-Stack E-Commerce Web Application (MERN Stack)
- **Core Functionality:** Online flower shop with product catalog, shopping cart, user accounts, order management, and admin dashboard
- **Target Users:** Customers seeking flowers online, Shop administrators

## Tech Stack
- **Frontend:** React 18, Tailwind CSS, Framer Motion, React Router v6
- **Backend:** Node.js, Express.js, MongoDB with Mongoose
- **Authentication:** JWT tokens
- **Icons:** Lucide React, Heroicons
- **Charts:** Recharts (Admin Dashboard)

## Color Palette
- **Primary:** #C73086 (Rose Pink)
- **Secondary:** #FF6B6B, #FFB6C1 (Soft Pink)
- **Background:** #FAFAFA
- **Text:** #212529
- **Sage Green:** #8B9A7D (accents)
- **Cream:** #FFF9E6 (accents)
- **Gold:** #D4AF37 (accents)

## Typography
- **Headings:** Poppins Bold (700)
- **Body:** Inter Regular (400)
- **Display:** Playfair Display (hero sections)

## UI Components

### Header (Fixed/Sticky)
- Logo (left), Navigation (center), Icons (right)
- Search bar with expand animation
- Account dropdown (authenticated state)
- Wishlist with badge + shake animation
- Cart icon with badge + slide-out drawer
- Glassmorphism effect on scroll

### Pages
1. **Home (`/`)**
   - Full-viewport hero with carousel
   - Bento grid latest products
   - FAQ/CTA section

2. **Shop (`/shop`)**
   - Sidebar filters + product grid
   - Sort + pagination

3. **Product Detail (`/product/:id`)**
   - Image gallery, price, stock, quantity selector
   - Tabs: Description, Care, Reviews

4. **Account (`/account/*`)**
   - Protected routes
   - Orders, Details, Addresses

5. **About (`/about`)**
   - Timeline, Team, Stats

6. **Contact (`/contact`)**
   - Form + Info/Map

7. **Checkout (`/checkout`)**
   - Multi-step: Details → Payment → Confirm
   - COD / UPI payment options
   - Order summary

### Admin Dashboard (`/admin`)
- Analytics with Recharts
- Product CRUD
- Order management
- User management

## API Endpoints

### Auth
- `POST /api/auth/register`
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/auth/me`

### Products
- `GET /api/products` (filter/sort/paginate)
- `GET /api/products/:id`
- `POST /api/products` (admin)
- `PUT /api/products/:id` (admin)
- `DELETE /api/products/:id` (admin)

### Orders
- `POST /api/orders`
- `GET /api/orders/my-orders`
- `GET /api/orders` (admin)

### Cart
- `GET /api/cart`
- `POST /api/cart/add`
- `DELETE /api/cart/:itemId`

### Analytics (Admin)
- `GET /api/admin/analytics`

## Database Schema

### User
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  phone: String,
  addresses: [{
    name, phone, address, city, state, pincode
  }],
  role: 'user' | 'admin',
  createdAt: Date
}
```

### Product
```javascript
{
  name: String,
  description: String,
  price: Number,
  discountPrice: Number,
  images: [String],
  category: String,
  stock: Number,
  ratings: Number,
  reviews: [{
    user: ObjectId, rating: Number, comment: String, createdAt: Date
  }],
  createdAt: Date
}
```

### Order
```javascript
{
  user: ObjectId,
  items: [{
    product: ObjectId,
    name: String,
    quantity: Number,
    price: Number,
    image: String
  }],
  shippingDetails: {
    name, phone, address, city, state, pincode
  },
  paymentMethod: 'COD' | 'UPI',
  paymentStatus: 'Pending' | 'Paid',
  status: 'Pending' | 'Processing' | 'Shipped' | 'Delivered',
  totalAmount: Number,
  createdAt: Date
}
```

## Animation Specifications
- Page transitions: Fade + slide up (0.3s)
- Product cards: Hover lift (-8px translateY)
- Cart drawer: Slide from right (spring)
- Button: Scale 0.98 on click
- Scroll: Fade-in sections (Intersection Observer)

## Responsive Breakpoints
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

## Currency
- INR (₹) using `Intl.NumberFormat('en-IN')`
