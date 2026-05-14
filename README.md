# Inventory Management System
## JSP + JDBC + Oracle Database Project

---

## 📋 Table of Contents
1. [Project Overview](#project-overview)
2. [Technologies Used](#technologies-used)
3. [System Requirements](#system-requirements)
4. [Project Structure](#project-structure)
5. [Database Setup](#database-setup)
6. [Installation Steps](#installation-steps)
7. [Configuration](#configuration)
8. [Running the Application](#running-the-application)
9. [User Guide](#user-guide)
10. [Features](#features)
11. [Troubleshooting](#troubleshooting)

---

## 🎯 Project Overview

A complete **Inventory Management System** built using JSP and JDBC **without servlets or frameworks**. All backend logic including CRUD operations, validation, session management, and database operations are implemented directly in JSP files.

### Key Highlights:
- ✅ **No Servlets** - Pure JSP architecture
- ✅ **No Frameworks** - Vanilla JSP + JDBC
- ✅ **Oracle Database** - Enterprise-grade database
- ✅ **Role-based Access** - Admin and User roles
- ✅ **Email Validation** - Only @gmail.com allowed
- ✅ **Session Management** - Secure authentication
- ✅ **Responsive UI** - Bootstrap-based design

---

## 💻 Technologies Used

| Component | Technology |
|-----------|-----------|
| **Frontend** | HTML5, CSS3, Bootstrap 5.3 |
| **Backend** | JSP (JavaServer Pages) |
| **Database** | Oracle Database 11g/19c/21c XE |
| **Connectivity** | JDBC (Oracle JDBC Driver) |
| **Server** | Apache Tomcat 9.x/10.x |
| **Icons** | Font Awesome 6.4 |
| **Architecture** | JSP-based MVC (No Servlets) |

---

## 🔧 System Requirements

### Software Requirements:
1. **Java Development Kit (JDK)** 8 or higher
2. **Oracle Database** 11g XE or higher
3. **Apache Tomcat** 9.x or 10.x
4. **Eclipse IDE** / NetBeans / IntelliJ IDEA
5. **Oracle JDBC Driver** (ojdbc8.jar or ojdbc11.jar)

### Hardware Requirements:
- Minimum 4GB RAM
- 2GB free disk space
- Intel i3 or equivalent processor

---

## 📁 Project Structure

```
InventoryManagementSystem/
│
├── WebContent/
│   ├── WEB-INF/
│   │   └── web.xml                    # Web application configuration
│   │
│   ├── admin/                          # Admin pages (Admin-only access)
│   │   ├── admin-dashboard.jsp         # Admin dashboard with statistics
│   │   ├── add-category.jsp            # Add new category
│   │   ├── view-category.jsp           # View and delete categories
│   │   ├── add-product.jsp             # Add new product
│   │   ├── view-product.jsp            # View all products
│   │   ├── update-product.jsp          # Update product details
│   │   ├── delete-product.jsp          # Delete product
│   │   ├── stock-management.jsp        # Manage stock (add/remove)
│   │   ├── stock-report.jsp            # Stock movement report
│   │   └── sales-report.jsp            # Sales and revenue report
│   │
│   ├── user/                           # User pages
│   │   ├── user-dashboard.jsp          # User dashboard
│   │   ├── product-list.jsp            # Browse products
│   │   └── search-product.jsp          # Search products
│   │
│   ├── index.jsp                       # Landing page
│   ├── login.jsp                       # Login page with authentication
│   ├── register.jsp                    # Registration page (Gmail validation)
│   ├── logout.jsp                      # Logout and session destroy
│   ├── header.jsp                      # Common header with navbar
│   ├── footer.jsp                      # Common footer
│   └── dbconnection.jsp                # Database connection utility
│
└── lib/
    └── ojdbc8.jar                      # Oracle JDBC Driver
```

---

## 🗄️ Database Setup

### Step 1: Start Oracle Database
```bash
# For Windows
sqlplus / as sysdba

# For Linux/Mac
sudo su - oracle
sqlplus / as sysdba
```

### Step 2: Create Database Schema

Run the provided **Oracle SQL script** (`database_setup.sql`):

```sql
-- Connect to Oracle as system user
sqlplus system/oracle@localhost:1521/xe

-- Run the setup script
@database_setup.sql
```

### Database Tables Created:
1. **users** - User authentication and roles
2. **categories** - Product categories
3. **products** - Product inventory
4. **stock** - Stock movement tracking
5. **sales** - Sales transactions

### Default Admin Account:
- **Email**: admin@gmail.com
- **Password**: admin123
- **Role**: admin

---

## 🚀 Installation Steps

### Step 1: Install Prerequisites

1. **Install JDK**
   ```bash
   # Verify installation
   java -version
   javac -version
   ```

2. **Install Oracle Database XE**
   - Download from Oracle website
   - Install and note down the credentials
   - Default: username=system, password=oracle

3. **Install Apache Tomcat**
   - Download Tomcat 9.x
   - Extract to `C:\apache-tomcat-9.0.xx`

4. **Install Eclipse IDE**
   - Download Eclipse IDE for Enterprise Java Developers

### Step 2: Setup Database

1. Start Oracle Database
2. Run `database_setup.sql` script
3. Verify tables are created:
   ```sql
   SELECT table_name FROM user_tables;
   ```

### Step 3: Configure Eclipse

1. Open Eclipse
2. Go to **Window → Preferences**
3. Configure **Server → Runtime Environments**
4. Add **Apache Tomcat 9.x**
5. Set JDK path

### Step 4: Import Project

1. **Create Dynamic Web Project**:
   - File → New → Dynamic Web Project
   - Project name: `InventoryManagementSystem`
   - Target runtime: Apache Tomcat 9.x
   - Dynamic web module version: 4.0

2. **Add Oracle JDBC Driver**:
   - Copy `ojdbc8.jar` to `WebContent/WEB-INF/lib/`
   - Right-click project → Build Path → Add to Build Path

3. **Create Folder Structure**:
   - Create folders as per project structure
   - Copy all JSP files to respective folders

---

## ⚙️ Configuration

### 1. Database Connection Configuration

Edit `dbconnection.jsp` with your Oracle credentials:

```jsp
// Database credentials
String dbURL = "jdbc:oracle:thin:@localhost:1521:xe";
String dbUser = "system";        // Change to your username
String dbPassword = "oracle";    // Change to your password
```

### 2. Update All JSP Files

If you changed the database credentials, update them in:
- `register.jsp`
- `login.jsp`
- All admin and user JSP files that use direct connection

### 3. Server Configuration

In Eclipse:
1. Right-click project → Properties
2. Project Facets → Java: 1.8 or higher
3. Targeted Runtimes: Apache Tomcat 9.x

---

## ▶️ Running the Application

### Method 1: Using Eclipse

1. Right-click project
2. **Run As → Run on Server**
3. Select **Apache Tomcat 9.x**
4. Click **Finish**

Application will open at: `http://localhost:8080/InventoryManagementSystem/`

### Method 2: Manual Deployment

1. Export project as WAR file:
   - Right-click project → Export → WAR file
   
2. Deploy to Tomcat:
   - Copy WAR to `tomcat/webapps/`
   - Start Tomcat: `startup.bat` (Windows) or `./startup.sh` (Linux)

3. Access application:
   - `http://localhost:8080/InventoryManagementSystem/`

---

## 📖 User Guide

### For Users (Regular Role)

1. **Registration**:
   - Click **Register** on home page
   - Enter name, email (@gmail.com only), and password
   - Submit to create account

2. **Login**:
   - Enter registered Gmail and password
   - Click **Login**

3. **Dashboard**:
   - View total products and categories
   - See product distribution by category

4. **Browse Products**:
   - Navigate to **Products** menu
   - View all available products with details

5. **Search Products**:
   - Go to **Search Products**
   - Enter product name or category
   - View filtered results

### For Admin

1. **Login as Admin**:
   - Email: admin@gmail.com
   - Password: admin123

2. **Dashboard**:
   - View statistics: Total Products, Stock, Sales, Categories
   - See recent products

3. **Category Management**:
   - **Add Category**: Create new product categories
   - **View Categories**: List all categories with delete option

4. **Product Management**:
   - **Add Product**: Add new products with details
   - **View Products**: See all products with edit/delete
   - **Update Product**: Modify product information
   - **Delete Product**: Remove products from inventory

5. **Stock Management**:
   - Add stock to products
   - Remove stock (creates sale record)
   - Real-time quantity updates

6. **Reports**:
   - **Stock Report**: View stock movements (in/out)
   - **Sales Report**: See sales history and revenue
   - **Top Products**: View best-selling items

---

## ✨ Features

### Authentication & Authorization
- ✅ Registration with Gmail validation
- ✅ Login with session management
- ✅ Role-based access (Admin/User)
- ✅ Duplicate email prevention
- ✅ Secure logout

### Admin Features
- ✅ Dashboard with statistics
- ✅ Category CRUD operations
- ✅ Product CRUD operations
- ✅ Stock management (add/remove)
- ✅ Stock movement tracking
- ✅ Sales tracking and reporting
- ✅ Revenue calculation

### User Features
- ✅ Product browsing
- ✅ Category-wise product view
- ✅ Product search functionality
- ✅ Stock availability check

### Technical Features
- ✅ JSP-only architecture (No Servlets)
- ✅ JDBC database connectivity
- ✅ Oracle PreparedStatement (SQL injection prevention)
- ✅ Session-based authentication
- ✅ Bootstrap responsive design
- ✅ Form validation (frontend + backend)
- ✅ Error handling and messages

---

## 🐛 Troubleshooting

### Common Issues & Solutions

#### 1. Database Connection Error
**Error**: `SQLException: ORA-12154: TNS:could not resolve the connect identifier`

**Solution**:
```jsp
// Check connection string in dbconnection.jsp
String dbURL = "jdbc:oracle:thin:@localhost:1521:xe";

// Verify Oracle is running
lsnrctl status
```

#### 2. JDBC Driver Not Found
**Error**: `ClassNotFoundException: oracle.jdbc.driver.OracleDriver`

**Solution**:
- Download `ojdbc8.jar`
- Place in `WebContent/WEB-INF/lib/`
- Right-click project → Build Path → Add to Build Path

#### 3. 404 Error on Startup
**Error**: `HTTP Status 404 – Not Found`

**Solution**:
- Verify project is deployed to Tomcat
- Check `web.xml` configuration
- Ensure `index.jsp` exists in WebContent

#### 4. Session Expired
**Error**: Redirected to login repeatedly

**Solution**:
- Check session timeout in `web.xml`
- Verify session attributes are set correctly
- Clear browser cookies

#### 5. Email Validation Error
**Error**: "Only Gmail IDs are allowed"

**Solution**:
- Use email ending with `@gmail.com`
- Example: `test@gmail.com` ✅
- Example: `test@yahoo.com` ❌

#### 6. Tomcat Port Already in Use
**Error**: `Address already in use: bind`

**Solution**:
```bash
# Change Tomcat port in server.xml
# From 8080 to 8081
<Connector port="8081" protocol="HTTP/1.1" ...
```

#### 7. Bootstrap/CSS Not Loading
**Solution**:
- Check internet connection (CDN links)
- Verify HTML head section includes Bootstrap CDN

#### 8. Oracle Identity Column Issue
**Error**: `ORA-00904: "GENERATED": invalid identifier`

**Solution**:
- Use Oracle 12c or higher
- Or modify SQL to use SEQUENCE instead of IDENTITY

---

## 📝 Important Notes

### Gmail Validation Rules
- ✅ Only emails ending with `@gmail.com` are allowed
- ✅ One email can register only once
- ✅ Email is stored in lowercase
- ❌ Other email providers are blocked

### Security Considerations
- Passwords are stored in **plain text** (educational project)
- For production: Use **password hashing** (BCrypt/SHA-256)
- Implement **HTTPS** for secure transmission
- Add **CSRF tokens** for form security

### Performance Tips
- Close database connections in `finally` block
- Use connection pooling for production
- Add pagination for large datasets
- Implement caching for frequently accessed data

---

## 🎓 Learning Objectives

This project helps you understand:
1. JSP architecture and lifecycle
2. JDBC database operations
3. Session management
4. Form validation (client + server side)
5. Role-based access control
6. MVC pattern without frameworks
7. Oracle database integration
8. Bootstrap responsive design

---

## 📞 Support

If you encounter issues:
1. Check **Troubleshooting** section
2. Verify **Database Setup**
3. Review **Configuration** settings
4. Check Eclipse **Console** for errors
5. Verify **Tomcat logs** in `tomcat/logs/`

---

## 📄 License

This project is for **educational purposes only**.

---

## 👨‍💻 Author

**Inventory Management System**  
Pure JSP + JDBC Implementation  
No Servlets | No Frameworks | Oracle Database

---

**Happy Coding! 🚀**
