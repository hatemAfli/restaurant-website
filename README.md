# FoodMine - Food Ordering Application

A full-stack food ordering application built with React and Node.js, featuring user authentication, shopping cart, payment integration, order tracking, and admin dashboard.

## 🚀 Features

### Customer Features

- **Browse Food Items**: View available food items with images, ratings, prices, and descriptions
- **Search & Filter**: Search for specific foods and filter by tags (e.g., FastFood, Pizza, Lunch)
- **Shopping Cart**: Add items to cart, modify quantities, and remove items
- **User Authentication**: Register and login with secure JWT-based authentication
- **Checkout**: Select delivery address using interactive map (Leaflet)
- **Payment**: Secure payment processing with PayPal integration
- **Order Tracking**: Track order status in real-time with order history
- **Profile Management**: Update profile information and change password
- **Order History**: View all past orders with status filters

### Admin Features

- **Dashboard**: Overview of orders and system statistics
- **Food Management**: Add, edit, and delete food items
- **User Management**: View and manage user accounts
- **Order Management**: View and manage all orders
- **Image Upload**: Upload food images using Cloudinary

## 🛠️ Technologies Used

### Frontend

- **React 18.2** - UI library
- **React Router DOM** - Routing
- **Axios** - HTTP client
- **React Leaflet** - Interactive maps
- **PayPal SDK** - Payment processing
- **React Toastify** - Notifications
- **CSS Modules** - Styling

### Backend

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **Bcryptjs** - Password hashing
- **Cloudinary** - Image storage
- **Mailgun** - Email service
- **Multer** - File upload

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/en) (version 18.x)
- [MongoDB](https://www.mongodb.com/try/download/community) (Community Edition)
- [Git](https://git-scm.com)
- A code editor (e.g., [Visual Studio Code](https://code.visualstudio.com))

## 🔧 Installation

1. **Clone the repository**

   ```bash
   git clone <your-repository-url>
   cd projet
   ```

2. **Install backend dependencies**

   ```bash
   cd backend
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd ../frontend
   npm install
   ```

## ⚙️ Environment Variables

### Backend Configuration

Create a `.env` file in the `backend` directory with the following variables:

```env
# Server Port (optional, defaults to 5000)
PORT=5000

# MongoDB Connection String
MONGO_URI=mongodb://localhost:27017/foodmine

# JWT Secret Key (generate a strong random string)
JWT_SECRET=your_super_secret_jwt_key_here

# Cloudinary Configuration (optional, for image uploads)
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Mailgun Configuration (optional, for email services)
MAILGUN_API_KEY=your_mailgun_api_key
```

### Frontend Configuration

The frontend automatically uses `http://localhost:5000` in development mode. For production, update `frontend/src/axiosConfig.js` or use environment variables.

### PayPal Configuration

Update the PayPal Client ID in `frontend/src/components/PaypalButtons/PaypalButtons.js`:

```javascript
clientId: "your_paypal_client_id_here";
```

**Note**: For production, move the PayPal Client ID to an environment variable for security.

## 🚀 Running the Project

### Development Mode

1. **Start MongoDB**

   - Make sure MongoDB is running on your system
   - Default connection: `mongodb://localhost:27017`

2. **Start the Backend Server**

   ```bash
   cd backend
   npm run dev
   ```

   The backend server will start on `http://localhost:5000`

3. **Start the Frontend Development Server**

   ```bash
   cd frontend
   npm start
   ```

   The frontend will start on `http://localhost:3000`

4. **Access the Application**
   - Open your browser and navigate to `http://localhost:3000`

### Production Mode

1. **Build the Frontend**

   ```bash
   cd frontend
   npm run build
   ```

2. **Start the Backend Server**
   ```bash
   cd backend
   npm start
   ```
   The backend serves the built frontend files from the `public` folder.

## 📁 Project Structure

```
projet/
├── backend/
│   ├── src/
│   │   ├── config/          # Configuration files (database, cloudinary, mail)
│   │   ├── constants/       # Constants (HTTP status, order status)
│   │   ├── helpers/         # Helper functions
│   │   ├── middleware/      # Authentication and authorization middleware
│   │   ├── models/          # MongoDB models (User, Food, Order)
│   │   ├── routers/         # API routes (food, user, order, upload)
│   │   └── server.js        # Main server file
│   └── package.json
├── frontend/
│   ├── public/              # Static files
│   └── src/
│       ├── components/      # Reusable React components
│       ├── hooks/           # Custom React hooks
│       ├── interceptors/    # Axios interceptors
│       ├── pages/           # Page components
│       ├── services/        # API service functions
│       └── App.js           # Main App component
└── README.md
```

## 🎯 Main Functionalities

### 1. Food Browsing

- Display all available food items
- View food details (name, price, rating, description, images)
- Filter foods by tags
- Search foods by name

### 2. Shopping Cart

- Add items to cart
- Update item quantities
- Remove items from cart
- Cart persists in local storage
- Calculate total price

### 3. User Authentication

- User registration
- User login with JWT tokens
- Protected routes
- Session management

### 4. Checkout Process

- Select delivery address on map
- Review order items
- Create order

### 5. Payment Integration

- PayPal payment processing
- Order confirmation
- Payment verification

### 6. Order Management

- View order history
- Filter orders by status
- Track order status
- View order details with map

### 7. Profile Management

- Update user profile
- Change password
- View profile information

### 8. Admin Dashboard

- View system statistics
- Manage foods (CRUD operations)
- Manage users
- Manage orders
- Upload food images

## 🔐 Default Users

The application seeds sample users on first run. Check `backend/src/data.js` for default user credentials.

## 📝 API Endpoints

### Food APIs

- `GET /api/foods` - Get all foods
- `GET /api/foods/tags` - Get all tags
- `GET /api/foods/search/:searchTerm` - Search foods
- `GET /api/foods/tag/:tag` - Get foods by tag
- `GET /api/foods/:foodId` - Get food by ID

### User APIs

- `POST /api/users/login` - User login
- `POST /api/users/register` - User registration
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update user profile
- `PUT /api/users/change-password` - Change password

### Order APIs

- `POST /api/orders` - Create order
- `GET /api/orders/newOrderForCurrentUser` - Get current user's new order
- `POST /api/orders/pay` - Process payment
- `GET /api/orders/track/:id` - Track order
- `GET /api/orders/:status?` - Get orders by status
- `GET /api/orders/allStatus/:id` - Get all order statuses

### Upload APIs

- `POST /api/upload` - Upload image

## 🐛 Troubleshooting

### MongoDB Connection Issues

- Ensure MongoDB is running
- Check the `MONGO_URI` in your `.env` file
- Verify MongoDB connection string format

### Port Already in Use

- Change the `PORT` in `.env` file
- Or kill the process using the port

### CORS Issues

- Check `backend/src/server.js` for CORS configuration
- Ensure frontend URL is included in allowed origins

### Payment Issues

- Verify PayPal Client ID is correct
- Check PayPal sandbox credentials for testing
- Ensure PayPal SDK is properly loaded

## 📄 License

This project is licensed under the ISC License.

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Contact

For questions or support, please open an issue in the repository.

---

**Note**: This is a learning project. For production use, ensure proper security measures, error handling, and testing are in place.
