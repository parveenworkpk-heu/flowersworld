# Flowers World - E-Commerce Application

A production-ready MERN stack e-commerce application for a flower shop with responsive design, admin dashboard, and modern UI/UX.

## Features

- **User Features:**
  - Product catalog with search, filters, and sorting
  - Shopping cart with persistent storage
  - User authentication (register/login)
  - Order placement with multiple payment methods (COD, UPI)
  - Order tracking and history
  - Account management

- **Admin Features:**
  - Dashboard with analytics (charts, KPIs)
  - Product management (CRUD operations)
  - Order management with status updates
  - User management (block/unblock)

## Tech Stack

- **Frontend:** React 18, Tailwind CSS, Framer Motion, React Router v6
- **Backend:** Node.js, Express.js, MongoDB, Mongoose
- **Authentication:** JWT tokens
- **Charts:** Recharts

## Project Structure

```
FlowersWorld/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Page components
│   │   ├── context/       # React contexts
│   │   └── utils/         # Utility functions
│   └── public/
├── server/                 # Express backend
│   ├── config/           # Database config
│   ├── controllers/     # Route controllers
│   ├── middleware/      # Auth middleware
│   ├── models/          # Mongoose models
│   ├── routes/          # API routes
│   └── server.js        # Entry point
├── SPEC.md               # Project specification
└── README.md
```

## Setup Instructions

### Prerequisites

- Node.js (v18+)
- MongoDB (local or Atlas)

### Backend Setup

```bash
cd server
npm install
```

Create `.env` file in `server/` directory:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/flowersworld
JWT_SECRET=flowersworldsecretkey2024
NODE_ENV=development
```

Start the backend:

```bash
npm start
```

The API will run on `http://localhost:5000`

### Frontend Setup

```bash
cd client
npm install
```

Create `.env` file in `client/` directory:

```env
REACT_APP_API_URL=http://localhost:5000/api
```

Start the frontend:

```bash
npm start
```

The app will run on `http://localhost:3000`

## Creating Admin User

After starting the server, you can create an admin user directly in MongoDB:

1. Use MongoDB Compass or CLI
2. Find the user you want to make admin
3. Update the user's `role` field to `"admin"`

Or modify the registration to set admin role (for development only):

```javascript
// In authController.js register function
const user = new User({ name, email, password, phone, role: 'admin' });
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user
- `PUT /api/auth/profile` - Update profile

### Products
- `GET /api/products` - List products (with filters)
- `GET /api/products/:id` - Get product details
- `GET /api/products/featured` - Get featured products
- `POST /api/products` - Create product (admin)
- `PUT /api/products/:id` - Update product (admin)
- `DELETE /api/products/:id` - Delete product (admin)

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders/my-orders` - Get user orders
- `GET /api/orders/:id` - Get order details

### Cart
- `GET /api/cart` - Get cart items
- `POST /api/cart/add` - Add to cart
- `PUT /api/cart/:itemId` - Update cart item
- `DELETE /api/cart/:itemId` - Remove from cart

### Admin
- `GET /api/admin/analytics` - Get analytics data
- `GET /api/admin/users` - List all users
- `GET /api/admin/orders` - List all orders
- `PATCH /api/admin/orders/:id/status` - Update order status

## Deployment

### Backend (Render/Railway)
1. Push code to GitHub
2. Create new web service
3. Set environment variables
4. Connect MongoDB Atlas

### Frontend (Vercel/Netlify)
1. Connect GitHub repository
2. Build command: `npm run build`
3. Set `REACT_APP_API_URL` environment variable

## Design

- **Primary Color:** #C73086 (Rose Pink)
- **Secondary:** #FF6B6B, #FFB6C1
- **Accent:** #D4AF37 (Gold)
- **Background:** #FAFAFA

### Typography
- Headings: Poppins (700)
- Body: Inter (400)
- Display: Playfair Display

## License

MIT
