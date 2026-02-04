# Online-Shopping-Managment-System

# Online Shopping System - Complete E-Commerce Platform

## Project Overview
Ek complete online shopping system with modern technologies:
- **Frontend**: HTML, CSS, JavaScript
- **Backend**: Java, Spring Boot, Hibernate
- **Database**: MySQL
- **Architecture**: RESTful API

## Features

### User Features
✅ User Registration & Login with JWT Authentication
✅ Browse Products by Categories
✅ Search & Filter Products
✅ Add to Cart & Manage Cart Items
✅ Place Orders with Multiple Payment Options
✅ View Order History & Track Orders
✅ User Profile Management

### Admin Features
✅ Product Management (CRUD Operations)
✅ Category Management
✅ Order Management & Status Updates
✅ User Management

## Technology Stack

### Backend Dependencies (All Included in pom.xml)
1. **Spring Boot Starter Web** - REST API development
2. **Spring Boot Starter Data JPA** - Database operations with Hibernate
3. **MySQL Connector** - MySQL database connectivity
4. **Spring Boot Starter Validation** - Input validation
5. **Spring Boot Starter Security** - Authentication & Authorization
6. **JWT (JSON Web Tokens)** - Token-based authentication
   - jjwt-api (0.11.5)
   - jjwt-impl (0.11.5)
   - jjwt-jackson (0.11.5)
7. **Lombok** - Reduce boilerplate code
8. **Spring Boot DevTools** - Development productivity
9. **ModelMapper** - DTO conversions
10. **Apache Commons FileUpload** - File upload handling
11. **Apache Commons IO** - File operations
12. **SpringDoc OpenAPI** - API documentation (Swagger)
13. **Spring Boot Starter Mail** - Email support

## Project Structure

```
online-shopping-system/
│
├── backend/
│   ├── pom.xml                          # Maven dependencies
│   └── src/
│       ├── main/
│       │   ├── java/com/shopping/
│       │   │   ├── OnlineShoppingApplication.java   # Main application
│       │   │   ├── model/                           # Entity classes
│       │   │   │   ├── User.java
│       │   │   │   ├── Category.java
│       │   │   │   ├── Product.java
│       │   │   │   ├── Cart.java
│       │   │   │   ├── CartItem.java
│       │   │   │   ├── Order.java
│       │   │   │   └── OrderItem.java
│       │   │   ├── repository/                      # JPA Repositories
│       │   │   │   ├── UserRepository.java
│       │   │   │   ├── CategoryRepository.java
│       │   │   │   ├── ProductRepository.java
│       │   │   │   ├── CartRepository.java
│       │   │   │   ├── CartItemRepository.java
│       │   │   │   ├── OrderRepository.java
│       │   │   │   └── OrderItemRepository.java
│       │   │   ├── service/                         # Business logic
│       │   │   │   ├── UserService.java
│       │   │   │   ├── CategoryService.java
│       │   │   │   ├── ProductService.java
│       │   │   │   ├── CartService.java
│       │   │   │   └── OrderService.java
│       │   │   ├── controller/                      # REST Controllers
│       │   │   │   ├── AuthController.java
│       │   │   │   ├── CategoryController.java
│       │   │   │   ├── ProductController.java
│       │   │   │   ├── CartController.java
│       │   │   │   └── OrderController.java
│       │   │   ├── dto/                             # Data Transfer Objects
│       │   │   │   ├── LoginRequest.java
│       │   │   │   ├── RegisterRequest.java
│       │   │   │   ├── AuthResponse.java
│       │   │   │   └── ApiResponse.java
│       │   │   ├── security/                        # Security configuration
│       │   │   │   ├── JwtUtils.java
│       │   │   │   ├── JwtAuthenticationFilter.java
│       │   │   │   └── UserDetailsServiceImpl.java
│       │   │   ├── config/                          # Configuration classes
│       │   │   │   └── SecurityConfig.java
│       │   │   └── exception/                       # Exception handling
│       │   │       ├── ResourceNotFoundException.java
│       │   │       └── GlobalExceptionHandler.java
│       │   └── resources/
│       │       └── application.properties           # Application configuration
│       └── test/                                    # Test classes
│
├── frontend/
│   ├── index.html                                   # Homepage
│   ├── login.html                                   # Login page
│   ├── register.html                                # Registration page
│   ├── products.html                                # Products listing
│   ├── cart.html                                    # Shopping cart
│   ├── orders.html                                  # Order history
│   ├── css/
│   │   └── style.css                                # Main stylesheet
│   └── js/
│       ├── config.js                                # API configuration
│       ├── auth.js                                  # Authentication logic
│       └── app.js                                   # Main application logic
│
└── database/
    └── schema.sql                                   # Database schema & sample data

```

## Setup Instructions

### Prerequisites
- Java 17 or higher
- Maven 3.6+
- MySQL 8.0+
- Modern web browser

### Database Setup

1. **Install MySQL** aur start karo service
2. **Create Database**:
```sql
CREATE DATABASE shopping_db;
```

3. **Run Schema Script**:
```bash
mysql -u root -p shopping_db < database/schema.sql
```

### Backend Setup

1. **Navigate to backend directory**:
```bash
cd backend
```

2. **Update application.properties**:
```properties
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password
```

3. **Build the project**:
```bash
mvn clean install
```

4. **Run the application**:
```bash
mvn spring-boot:run
```

Backend server will start at `http://localhost:8080`

### Frontend Setup

1. **Navigate to frontend directory**:
```bash
cd frontend
```

2. **Open with Live Server** ya kisi bhi HTTP server se:
```bash
# Using Python
python -m http.server 5500

# Or using Node.js http-server
npx http-server -p 5500
```

Frontend will be available at `http://localhost:5500`

## API Endpoints

### Authentication APIs
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user

### Product APIs
- `GET /api/products` - Get all active products
- `GET /api/products/{id}` - Get product by ID
- `GET /api/products/featured` - Get featured products
- `GET /api/products/latest` - Get latest products
- `GET /api/products/category/{categoryId}` - Get products by category
- `GET /api/products/search?keyword={keyword}` - Search products
- `POST /api/products` - Create product (Admin only)
- `PUT /api/products/{id}` - Update product (Admin only)
- `DELETE /api/products/{id}` - Delete product (Admin only)

### Category APIs
- `GET /api/categories` - Get all categories
- `GET /api/categories/{id}` - Get category by ID
- `POST /api/categories` - Create category (Admin only)
- `PUT /api/categories/{id}` - Update category (Admin only)
- `DELETE /api/categories/{id}` - Delete category (Admin only)

### Cart APIs
- `GET /api/cart` - Get user's cart
- `POST /api/cart/add` - Add item to cart
- `PUT /api/cart/update/{cartItemId}` - Update cart item
- `DELETE /api/cart/remove/{cartItemId}` - Remove item from cart
- `DELETE /api/cart/clear` - Clear cart

### Order APIs
- `POST /api/orders` - Create order
- `GET /api/orders` - Get user's orders
- `GET /api/orders/{id}` - Get order by ID
- `GET /api/orders/order-number/{orderNumber}` - Get order by order number
- `DELETE /api/orders/{id}/cancel` - Cancel order
- `GET /api/orders/admin/all` - Get all orders (Admin only)
- `PUT /api/orders/{id}/status` - Update order status (Admin only)

## API Documentation

Access Swagger UI at: `http://localhost:8080/swagger-ui.html`

## Default Credentials

### Admin Account
- **Email**: admin@shopping.com
- **Password**: admin123

## Features in Detail

### 1. User Management
- Secure registration with password encryption
- JWT-based authentication
- Role-based access control (CUSTOMER, ADMIN)

### 2. Product Management
- Complete CRUD operations
- Image upload support
- Stock management
- Price & discount management
- Featured products
- Category-wise organization

### 3. Shopping Cart
- Add/Update/Remove items
- Real-time price calculation
- Persistent cart across sessions

### 4. Order Management
- Multiple payment methods support
- Order status tracking
- Order history
- Email notifications (configurable)

### 5. Search & Filter
- Search by product name
- Filter by category
- Price range filtering

## Security Features

1. **Password Encryption** - BCrypt hashing
2. **JWT Authentication** - Stateless token-based auth
3. **CORS Configuration** - Secure cross-origin requests
4. **SQL Injection Prevention** - JPA prepared statements
5. **Input Validation** - Bean validation annotations

## Database Schema

### Main Tables:
1. **users** - User information
2. **categories** - Product categories
3. **products** - Product details
4. **carts** - Shopping carts
5. **cart_items** - Cart items
6. **orders** - Order information
7. **order_items** - Order items

## Testing

### Test Admin APIs using Postman/cURL:

1. **Login**:
```bash
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@shopping.com","password":"admin123"}'
```

2. **Create Product**:
```bash
curl -X POST http://localhost:8080/api/products \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -d '{
    "name": "Product Name",
    "description": "Product Description",
    "price": 999.99,
    "stockQuantity": 100,
    "category": {"id": 1}
  }'
```

## Troubleshooting

### Common Issues:

1. **Port already in use**:
```properties
# Change port in application.properties
server.port=8081
```

2. **Database connection error**:
- Check MySQL is running
- Verify credentials in application.properties
- Ensure database exists

3. **CORS errors**:
- Frontend URL is configured in SecurityConfig.java
- Add your frontend URL if different

## Future Enhancements

- Payment gateway integration
- Product reviews & ratings
- Wishlist functionality
- Product recommendations
- Admin dashboard
- Email notifications
- Invoice generation
- Multi-language support

## Support

For issues or questions:
- Email: support@shopzone.com
- GitHub Issues: [Project Repository]

## License

This project is open source and available under the MIT License.

---
**Developed with ❤️ using Java, Spring Boot & Modern Web Technologies**

# Quick Start Guide - Online Shopping System

## 🚀 5-Minute Setup

### Step 1: Database Setup (2 minutes)
```bash
# MySQL mein login karo
mysql -u root -p

# Database create karo
CREATE DATABASE shopping_db;
exit;

# Schema load karo
mysql -u root -p shopping_db < database/schema.sql
```

### Step 2: Backend Setup (2 minutes)
```bash
# Backend folder mein jao
cd backend

# Application properties update karo (optional)
# Edit src/main/resources/application.properties
# Update MySQL username/password if needed

# Application run karo
mvn spring-boot:run
```

✅ Backend ready at: http://localhost:8080

### Step 3: Frontend Setup (1 minute)
```bash
# New terminal mein frontend folder kholo
cd frontend

# Live server se open karo
# Option 1: VS Code Live Server extension use karo
# Option 2: Python HTTP server
python -m http.server 5500
```

✅ Frontend ready at: http://localhost:5500

## 🎯 Test the Application

### 1. Open Browser
Open `http://localhost:5500` in your browser

### 2. Register New User
- Click on "Login" → "Register here"
- Fill the registration form
- Submit

### 3. Login
- Use your registered credentials
- You'll get JWT token automatically

### 4. Browse Products
- View featured products on homepage
- Click on categories
- Add products to cart

### 5. Place Order
- Go to cart
- Click "Proceed to Checkout"
- Fill shipping details
- Place order

### 6. Admin Access (Optional)
```
Email: admin@shopping.com
Password: admin123
```

Admin can:
- Add/Edit/Delete products
- Manage categories
- View all orders
- Update order status

## 📊 Verify Backend APIs

### Test with cURL or Postman:

**1. Health Check:**
```bash
curl http://localhost:8080/api/products
```

**2. Login:**
```bash
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@shopping.com","password":"admin123"}'
```

**3. Get Categories:**
```bash
curl http://localhost:8080/api/categories
```

## 🔍 Swagger API Documentation

Access complete API documentation:
```
http://localhost:8080/swagger-ui.html
```

## 📁 Project Structure Quick Reference

```
backend/
  src/main/java/com/shopping/
    ├── model/          → Entity classes
    ├── repository/     → Database access
    ├── service/        → Business logic
    ├── controller/     → REST APIs
    ├── security/       → JWT & Auth
    └── config/         → Configuration

frontend/
  ├── index.html       → Homepage
  ├── login.html       → Login page
  ├── css/style.css    → Styling
  └── js/
      ├── config.js    → API endpoints
      ├── auth.js      → Authentication
      └── app.js       → Main logic
```

## 🐛 Common Issues & Solutions

### Issue 1: Port 8080 already in use
**Solution:**
```properties
# Edit application.properties
server.port=8081
```

### Issue 2: Database connection failed
**Solution:**
```properties
# Check MySQL is running
sudo systemctl status mysql

# Verify credentials in application.properties
spring.datasource.username=your_username
spring.datasource.password=your_password
```

### Issue 3: CORS error in browser
**Solution:**
- Frontend URL already configured for localhost:5500
- If using different port, update SecurityConfig.java

### Issue 4: JWT token expired
**Solution:**
- Login again to get new token
- Token expires after 24 hours (configurable in application.properties)

## 🔑 Key Configuration Files

### 1. application.properties
```properties
server.port=8080
spring.datasource.url=jdbc:mysql://localhost:3306/shopping_db
spring.datasource.username=root
spring.datasource.password=root
jwt.secret=mySecretKey
jwt.expiration=86400000  # 24 hours
```

### 2. frontend/js/config.js
```javascript
const API_BASE_URL = 'http://localhost:8080/api';
```

## 📚 Next Steps

1. ✅ Add sample products through admin panel
2. ✅ Test complete user flow (Register → Browse → Cart → Order)
3. ✅ Explore API documentation
4. ✅ Customize frontend design
5. ✅ Add more features as needed

## 🎓 Learning Resources

- **Spring Boot**: https://spring.io/projects/spring-boot
- **JPA/Hibernate**: https://hibernate.org/
- **JWT**: https://jwt.io/
- **REST APIs**: https://restfulapi.net/

## 💡 Pro Tips

1. Use Swagger UI for API testing - easiest way!
2. Check browser console for any JavaScript errors
3. Monitor backend logs for debugging
4. Use Postman collection for API testing
5. Enable logging in application.properties for debugging

## 🆘 Need Help?

- Check README.md for detailed documentation
- Review API endpoints in Swagger UI
- Check application logs in terminal
- Verify database tables are created properly

---
**Happy Coding! 🚀**
