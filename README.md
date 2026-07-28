# 🛒 E-Commerce Shopping Cart | Spring Boot

<p align="center">
  <img src="https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=openjdk" alt="Java 17"/>
  <img src="https://img.shields.io/badge/Spring%20Boot-3.2.3-brightgreen?style=for-the-badge&logo=springboot" alt="Spring Boot"/>
  <img src="https://img.shields.io/badge/Spring%20Security-6.x-green?style=for-the-badge&logo=springsecurity" alt="Spring Security"/>
  <img src="https://img.shields.io/badge/Spring%20Data%20JPA-blue?style=for-the-badge&logo=spring" alt="Spring Data JPA"/>
  <img src="https://img.shields.io/badge/Hibernate-ORM-brown?style=for-the-badge&logo=hibernate" alt="Hibernate"/>
  <img src="https://img.shields.io/badge/Thymeleaf-Template%20Engine-005F0F?style=for-the-badge&logo=thymeleaf" alt="Thymeleaf"/>
  <img src="https://img.shields.io/badge/PostgreSQL-Database-336791?style=for-the-badge&logo=postgresql" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/Maven-Build-C71A36?style=for-the-badge&logo=apachemaven" alt="Maven"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5"/>
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3"/>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript"/>
  <img src="https://img.shields.io/badge/Lombok-BC4521?style=for-the-badge" alt="Lombok"/>
  <img src="https://img.shields.io/badge/Gmail%20SMTP-Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail SMTP"/>
</p>

<h3 align="center">A Full-Stack E-Commerce Shopping Cart Application built with Spring Boot, Spring Security, JPA/Hibernate, PostgreSQL and Thymeleaf.</h3>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-database-design">Database</a> •
  <a href="#-application-workflow">Workflow</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-screenshots">Screenshots</a>
</p>

---

## 📌 About The Project

This project is a complete **E-Commerce Shopping Cart web application** developed using the **Spring Boot MVC architecture**.

The application provides separate experiences for **customers and administrators**. Customers can register, securely log in, browse products, search products, filter products by category, manage their shopping cart, place orders, view order history, manage their profile and reset forgotten passwords.

Administrators can manage products, categories, users and orders through a dedicated administration area.

The application also integrates **Spring Security** for authentication and authorization and uses **JavaMailSender with Gmail SMTP** for password-reset emails and product-order status notifications.

---

# ✨ Features

## 👤 Customer Features

* User registration
* Secure login using Spring Security
* Password encryption using BCrypt
* User profile management
* Profile image upload
* Account status management
* Failed-login attempt tracking
* Account locking mechanism
* Automatic account unlock after configured duration
* Forgot password functionality
* Password reset using email
* Product browsing
* Product search
* Category-based product filtering
* Product pagination
* Search pagination
* Add products to shopping cart
* Update cart quantity
* Remove cart items
* Checkout functionality
* Order placement
* Multiple payment-type selection
* Order history
* Order details
* Order status tracking
* Email notification after order placement

---

## 🛡️ Administrator Features

The project contains a dedicated admin module for managing the e-commerce platform.

### Product Management

* Add new products
* Edit products
* Delete products
* Upload product images
* Manage product prices
* Configure product discounts
* Calculate discounted product prices
* Manage stock
* Activate/deactivate products
* Search and paginate products

### Category Management

* Add categories
* Edit categories
* Manage product categories

### User Management

* View users
* Manage user account status
* Manage user roles
* Add administrator accounts

### Order Management

* View all orders
* View orders with pagination
* View order details
* Update order status

### Available Order Statuses

```text
In Progress
Order Received
Product Packed
Out for Delivery
Delivered
Cancelled
Success
```

---

# 🔐 Security Features

The application uses **Spring Security** to provide authentication and authorization.

### Implemented Security Concepts

* User authentication
* Admin authentication
* Role-based access control
* `ROLE_USER`
* `ROLE_ADMIN`
* BCrypt password hashing
* Custom `UserDetailsService`
* Custom authentication success handler
* Custom authentication failure handler
* Failed login attempt tracking
* Account locking
* Automatic account unlock mechanism
* Password reset functionality

### Authentication Flow

```text
                  ┌─────────────────┐
                  │      User       │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │   Login Page    │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ Spring Security │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ UserDetailsService│
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │ User Repository │
                  └────────┬────────┘
                           │
                           ▼
                  ┌─────────────────┐
                  │  PostgreSQL DB  │
                  └─────────────────┘
```

---

# 🏗️ Application Architecture

The application follows a layered **Spring Boot MVC architecture**.

```text
                         ┌──────────────────────────┐
                         │          CLIENT          │
                         │                          │
                         │  Browser / Web Interface │
                         └────────────┬─────────────┘
                                      │
                                      │ HTTP Request
                                      ▼
                         ┌──────────────────────────┐
                         │       CONTROLLER         │
                         │                          │
                         │  AdminController         │
                         │  HomeController          │
                         │  UserController          │
                         └────────────┬─────────────┘
                                      │
                                      ▼
                         ┌──────────────────────────┐
                         │         SERVICE          │
                         │                          │
                         │  ProductService          │
                         │  CategoryService         │
                         │  CartService             │
                         │  OrderService            │
                         │  UserService             │
                         └────────────┬─────────────┘
                                      │
                                      ▼
                         ┌──────────────────────────┐
                         │       REPOSITORY         │
                         │                          │
                         │  ProductRepository       │
                         │  CategoryRepository      │
                         │  CartRepository          │
                         │  ProductOrderRepository  │
                         │  UserRepository           │
                         └────────────┬─────────────┘
                                      │
                                      │ JPA / Hibernate
                                      ▼
                         ┌──────────────────────────┐
                         │       PostgreSQL         │
                         │                          │
                         │    ECOM_DB Database      │
                         └──────────────────────────┘
```

### Supporting Components

```text
Spring Security
      │
      ├── CustomUser
      ├── UserDetailsServiceImpl
      ├── SecurityConfig
      ├── AuthSucessHandlerImpl
      └── AuthFailureHandlerImpl

JavaMailSender
      │
      └── CommonUtil
             ├── Password Reset Email
             └── Product Order Email

Thymeleaf
      │
      ├── User Views
      ├── Admin Views
      └── Shared Templates
```

---

# 📂 Project Structure

```text
src
│
├── main
│   │
│   ├── java
│   │   └── com.ecom
│   │       │
│   │       ├── config
│   │       │   ├── AuthFailureHandlerImpl.java
│   │       │   ├── AuthSucessHandlerImpl.java
│   │       │   ├── CustomUser.java
│   │       │   ├── SecurityConfig.java
│   │       │   └── UserDetailsServiceImpl.java
│   │       │
│   │       ├── controller
│   │       │   ├── AdminController.java
│   │       │   ├── HomeController.java
│   │       │   └── UserController.java
│   │       │
│   │       ├── model
│   │       │   ├── Cart.java
│   │       │   ├── Category.java
│   │       │   ├── OrderAddress.java
│   │       │   ├── OrderRequest.java
│   │       │   ├── Product.java
│   │       │   ├── ProductOrder.java
│   │       │   └── UserDtls.java
│   │       │
│   │       ├── repository
│   │       │   ├── CartRepository.java
│   │       │   ├── CategoryRepository.java
│   │       │   ├── ProductOrderRepository.java
│   │       │   ├── ProductRepository.java
│   │       │   └── UserRepository.java
│   │       │
│   │       ├── service
│   │       │   ├── CartService.java
│   │       │   ├── CategoryService.java
│   │       │   ├── CommnServiceImpl.java
│   │       │   ├── CommonService.java
│   │       │   ├── OrderService.java
│   │       │   ├── ProductService.java
│   │       │   ├── UserService.java
│   │       │   │
│   │       │   └── impl
│   │       │       ├── CartServiceImpl.java
│   │       │       ├── CategoryServiceImpl.java
│   │       │       ├── OrderServiceImpl.java
│   │       │       ├── ProductServiceImpl.java
│   │       │       └── UserServiceImpl.java
│   │       │
│   │       ├── util
│   │       │   ├── AppConstant.java
│   │       │   ├── CommonUtil.java
│   │       │   └── OrderStatus.java
│   │       │
│   │       └── ShoppingCartApplication.java
│   │
│   └── resources
│       │
│       ├── static
│       │   ├── css
│       │   │   └── style.css
│       │   ├── js
│       │   │   └── script.js
│       │   └── img
│       │       ├── category_img
│       │       ├── product_img
│       │       └── profile_img
│       │
│       └── templates
│           ├── admin
│           │   ├── add_admin.html
│           │   ├── add_product.html
│           │   ├── category.html
│           │   ├── edit_category.html
│           │   ├── edit_product.html
│           │   ├── index.html
│           │   ├── orders.html
│           │   ├── products.html
│           │   ├── profile.html
│           │   └── users.html
│           │
│           ├── user
│           │   ├── cart.html
│           │   ├── home.html
│           │   ├── my_orders.html
│           │   ├── order.html
│           │   ├── profile.html
│           │   └── success.html
│           │
│           ├── base.html
│           ├── forgot_password.html
│           ├── index.html
│           ├── login.html
│           ├── message.html
│           ├── product.html
│           ├── register.html
│           ├── reset_password.html
│           └── view_product.html
│
└── test
    └── java
        └── com.ecom
            └── ShoppingCartApplicationTests.java
```

---

# 🗄️ Database Design

The application uses **PostgreSQL** with **Spring Data JPA and Hibernate**.

The core domain models identified in the source code are:

```text
UserDtls
Category
Product
Cart
ProductOrder
OrderAddress
OrderRequest
```

A high-level relationship model is:

```text
                         ┌─────────────────┐
                         │    UserDtls     │
                         │─────────────────│
                         │ id              │
                         │ name            │
                         │ email           │
                         │ password        │
                         │ role            │
                         │ account status  │
                         │ profile image   │
                         └───────┬─────────┘
                                 │
                 ┌───────────────┼────────────────┐
                 │               │                │
                 │               │                │
                 ▼               ▼                ▼
          ┌────────────┐  ┌────────────┐  ┌───────────────┐
          │    Cart    │  │ProductOrder│  │ Authentication│
          │────────────│  │────────────│  │ & Security    │
          │ quantity   │  │ orderId    │  └───────────────┘
          │ product    │  │ product    │
          │ user       │  │ user       │
          └─────┬──────┘  │ address    │
                │         │ payment    │
                │         │ status     │
                │         └──────┬─────┘
                │                │
                └───────┬────────┘
                        │
                        ▼
                 ┌─────────────┐
                 │   Product   │
                 │─────────────│
                 │ title       │
                 │ description │
                 │ price       │
                 │ discount    │
                 │ stock       │
                 │ image       │
                 │ isActive    │
                 │ category    │
                 └──────┬──────┘
                        │
                        ▼
                 ┌─────────────┐
                 │  Category   │
                 └─────────────┘

ProductOrder
      │
      ▼
OrderAddress
      │
      ├── firstName
      ├── lastName
      ├── email
      ├── mobileNo
      ├── address
      ├── city
      ├── state
      └── pincode
```

### Order Processing Flow

```text
User
 │
 ▼
Browse Products
 │
 ▼
Add Product to Cart
 │
 ▼
Cart
 │
 ▼
Checkout
 │
 ▼
OrderRequest
 │
 ├── Customer Information
 ├── Shipping Address
 └── Payment Type
 │
 ▼
ProductOrder
 │
 ▼
Save Order in PostgreSQL
 │
 ▼
Send Order Confirmation Email
 │
 ▼
Admin Updates Order Status
 │
 ▼
Customer Tracks Order
```

---

# 🔌 Application Modules

## 🏠 Home & Product Module

The application supports:

* Product listing
* Active-product filtering
* Category filtering
* Product search
* Case-insensitive product/category search
* Pagination
* Product details
* Product image handling

The `ProductServiceImpl` implements product operations including:

```text
saveProduct()
getAllProducts()
getAllProductsPagination()
deleteProduct()
getProductById()
updateProduct()
getAllActiveProducts()
searchProduct()
searchProductPagination()
getAllActiveProductPagination()
searchActiveProductPagination()
```

---

## 🛒 Cart Module

The cart module manages the user's selected products before checkout.

```text
Product
   │
   ▼
Add to Cart
   │
   ▼
Cart
   │
   ├── Product
   ├── User
   └── Quantity
   │
   ▼
Update / Remove
   │
   ▼
Checkout
```

---

## 📦 Order Module

The order service processes cart items and creates `ProductOrder` records.

The order process includes:

1. Retrieve user's cart items
2. Generate unique order ID
3. Set order date
4. Associate product and user
5. Store product price
6. Store quantity
7. Set initial order status
8. Store payment type
9. Create shipping/order address
10. Persist order
11. Send email notification

Initial status:

```text
In Progress
```

Available status transitions include:

```text
In Progress
     ↓
Order Received
     ↓
Product Packed
     ↓
Out for Delivery
     ↓
Delivered
```

Additional statuses:

```text
Cancelled
Success
```

---

# 📧 Email Notification System

The application uses:

```text
Spring Boot Starter Mail
        │
        ▼
JavaMailSender
        │
        ▼
CommonUtil
        │
        ├─────────────────────┐
        │                     │
        ▼                     ▼
Password Reset          Product Order
Email                   Notification
```

### Password Reset Email

The application generates a password-reset URL and sends an email containing a link that allows the user to change their password.

### Product Order Email

After an order is saved, the application sends an HTML email containing:

* Customer name
* Order status
* Product name
* Product category
* Quantity
* Price
* Payment type

---

# 🔎 Product Search & Pagination

The application supports search using product title and category.

```text
Search Keyword
      │
      ▼
Product Title
      │
      ├── Case-insensitive matching
      │
      ▼
Product Category
      │
      ├── Case-insensitive matching
      │
      ▼
Search Results
      │
      ▼
Pagination
```

Pagination is implemented using Spring Data:

```java
Pageable pageable = PageRequest.of(pageNo, pageSize);
```

This functionality is available for:

* Products
* Active products
* Search results
* Orders

---

# 📸 Screenshots

The project contains application images under:

```text
src/main/resources/static/img/
```

The application includes visual resources for:

* E-commerce homepage
* Product images
* Product categories
* User profiles

### 🏠 Homepage

Add your actual screenshot here:

```markdown
![Homepage](./screenshots/homepage.png)
```

### 🛍️ Product Listing

```markdown
![Products](./screenshots/products.png)
```

### 🛒 Shopping Cart

```markdown
![Shopping Cart](./screenshots/cart.png)
```

### 👨‍💼 Admin Dashboard

```markdown
![Admin Dashboard](./screenshots/admin-dashboard.png)
```

> Create a `screenshots` folder in the repository and add your actual application screenshots for the best GitHub presentation.

---

# 🌐 Live Demo

🚧 **Live Demo: Coming Soon**

The application currently runs locally using Spring Boot.

```text
http://localhost:8081
```

The configured application port is:

```properties
server.port=8081
```

### Planned Deployment

The application can be deployed using:

* AWS
* Render
* Railway
* Azure
* Docker

After deployment, update this section with your live URL:

```text
🔗 Live Demo:
https://your-live-domain.com
```

---

# ⚙️ Requirements

Before running the application, install:

* Java 17+
* Maven 3.8+
* PostgreSQL
* Git
* IDE such as IntelliJ IDEA or Eclipse

---

# 🚀 Installation & Setup

## 1. Clone the Repository

```bash
git clone https://github.com/diwakarshahi9507/Ecom_Projecr_Master.git
```

## 2. Navigate to the Project

```bash
cd Ecom_Projecr_Master
```

## 3. Create PostgreSQL Database

Create a PostgreSQL database:

```sql
CREATE DATABASE ECOM_DB;
```

## 4. Configure Application

Update:

```text
src/main/resources/application.properties
```

Example configuration:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/ECOM_DB
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

server.port=8081
```

For email configuration:

```properties
spring.mail.host=smtp.gmail.com
spring.mail.username=${MAIL_USERNAME}
spring.mail.password=${MAIL_PASSWORD}
spring.mail.port=587

spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

### ⚠️ Security

Never commit credentials directly into:

```text
application.properties
```

Use environment variables instead:

```text
DB_USERNAME
DB_PASSWORD
MAIL_USERNAME
MAIL_PASSWORD
```

---

# ▶️ Run the Application

### Using Maven

```bash
mvn spring-boot:run
```

### Using Maven Wrapper — Windows

```bash
mvnw.cmd spring-boot:run
```

### Using Maven Wrapper — Linux/macOS

```bash
./mvnw spring-boot:run
```

Open the application:

```text
http://localhost:8081
```

---

# 📦 Maven Dependencies

The project uses the following major Spring Boot dependencies:

```text
Spring Boot 3.2.3
        │
        ├── Spring Web
        ├── Spring Data JPA
        ├── Spring Security
        ├── Spring Thymeleaf
        ├── Spring Mail
        ├── Spring DevTools
        └── Spring Boot Test

Database
        └── PostgreSQL

Additional
        └── Lombok
```

---

# 🧪 Testing

The project contains a Spring Boot application context test:

```java
@SpringBootTest
class ShoppingCartApplicationTests {

    @Test
    void contextLoads() {
    }
}
```

Run tests using:

```bash
mvn test
```

---

# 🧠 Technical Concepts Demonstrated

This project demonstrates practical knowledge of:

### Java

* Object-Oriented Programming
* Interfaces
* Service implementations
* Collections
* Exception handling
* Enums

### Spring Boot

* Dependency Injection
* Spring MVC
* Service Layer
* Repository Layer
* Application Configuration

### Spring Data JPA

* Repository interfaces
* CRUD operations
* Query method generation
* Pagination
* Entity persistence

### Hibernate

* ORM
* Entity mapping
* PostgreSQL integration

### Spring Security

* Authentication
* Authorization
* Role-based access
* Password encryption
* Custom UserDetailsService
* Authentication handlers

### Thymeleaf

* Server-side rendering
* Dynamic HTML templates
* User and admin views

### Email

* JavaMailSender
* SMTP
* HTML email templates
* Password reset notifications
* Order notifications

---

# 🔮 Future Enhancements

* [ ] JWT-based REST API authentication
* [ ] Swagger / OpenAPI documentation
* [ ] Online payment gateway integration
* [ ] Product reviews and ratings
* [ ] Wishlist functionality
* [ ] Redis caching
* [ ] Docker containerization
* [ ] CI/CD pipeline
* [ ] Cloud deployment
* [ ] Advanced automated testing
* [ ] Improved account-lock duration configuration
* [ ] Centralized exception handling
* [ ] DTO-based API architecture
* [ ] Production-ready environment configuration

---

# 👨‍💻 Author

## Diwakar Kumar

**Java Backend Developer | Spring Boot Developer**

### Technical Skills

`Java` `Spring Boot` `Spring Security` `Spring MVC` `JPA` `Hibernate` `PostgreSQL` `Thymeleaf` `Maven` `HTML` `CSS` `JavaScript` `Git` `GitHub`

---

# 🔗 Repository

⭐ **GitHub Repository**

https://github.com/diwakarshahi9507/Ecom_Projecr_Master

---

# ⭐ Support

If you found this project useful, please consider giving the repository a ⭐ on GitHub.

Your feedback and suggestions are welcome!

---

## 📄 License

This project is developed for **educational, learning, and portfolio purposes**.
