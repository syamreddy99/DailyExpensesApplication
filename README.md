# 🏦 Daily Expenses Sharing Application

## Table of Contents
- [📘 Introduction](#-introduction)
- [✨ Features](#-features)
- [💻 Technologies Used](#-technologies-used)
- [🚀 Getting Started](#-getting-started)
  - [📋 Prerequisites](#-prerequisites)
  - [🔧 Installation](#-installation)
  - [⚙️ Configuration](#%EF%B8%8Fconfiguration)
- [▶️ Running the Application](#%EF%B8%8Frunning-the-application)
- [🔗 API Endpoints](#api-endpoints)
  - [👥 User Endpoints](#user-endpoints)
  - [💰 Expenses Endpoints](#expenses-endpoints)
- [🗄️ Database Structure](#%EF%B8%8Fdatabase-structure)

# 📘 Introduction
The Daily Expenses Sharing Application allows users to add expenses and split them among participants using three different methods: equal splits, exact amounts, and percentages. The application also provides features for user management and generates downloadable balance sheets.

## ✨ Features
### User Management:
  - 👤Create and retrieve user details.
### Expense Management:
  - 💸 Add expenses and split them in multiple ways.
  - ✅ Validate inputs to ensure data integrity.
  - 📊 Generate balance sheets for individual users and overall expenses.

## 💻 Technologies Used
- ☕ **Java 17** ![Java](https://img.shields.io/badge/-Java-007396?style=flat&logo=java&logoColor=white)
- 🖥️ **Spring Boot** ![SpringBoot](https://img.shields.io/badge/-SpringBoot-6DB33F?style=flat&logo=springboot&logoColor=white)
- 🗃️ **Hibernate** ![Hibernate](https://img.shields.io/badge/-Hibernate-59616B?style=flat&logo=hibernate&logoColor=white)
- 🛢️ **MySQL** ![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
- 📦 **Apache Maven** ![Maven](https://img.shields.io/badge/-Maven-C71A36?style=flat&logo=apache-maven&logoColor=white)
- 📝 **Lombok** ![Lombok](https://img.shields.io/badge/-Lombok-2C2D72?style=flat&logo=lombok&logoColor=white)

## 🚀 Getting Started

### 📋 Prerequisites
Before you begin, ensure you have the following installed:
- ☕ **Java 17** or above ![Java](https://img.shields.io/badge/-Java-007396?style=flat&logo=java&logoColor=white)
- 🛠️ **Apache Maven** ![Maven](https://img.shields.io/badge/-Maven-C71A36?style=flat&logo=apache-maven&logoColor=white)
- 🛢️ **MySQL Workbench** ![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
- 🖥️ **Eclipse** or **Spring Tool Suite** ![Eclipse](https://img.shields.io/badge/-Eclipse-2C2D72?style=flat&logo=eclipse&logoColor=white)
- 📨 **Postman** ![Postman](https://img.shields.io/badge/-Postman-FF6C37?style=flat&logo=postman&logoColor=white)


### 🔧 Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/syamreddy99/Daily-Expenses-Sharing-Application
   cd Daily-Expense-Sharing-Application

# ⚙️configuration 
  ### Database Configuration:

   Create a database named "dailyexpenses".
   
  ### Update"application.properties":

 - spring.application.name= `Daily-Expenses-Sharing-Application`
 
 - server.port=   `9982`
    - This property sets the port number on which the Spring Boot application will run.By default, Spring Boot applications run on port 8080, but this can be 
      changed as needed.
 
 - spring.datasource.url= `jdbc:mysql://localhost:3306/DailyExpenses`
  
     - This property defines the JDBC  URL for connecting to the MySQL database. It specifies the database type, host, port, and the nameof the database.
                                                                    
 - spring.datasource.username= `root`

     - Defines the username for the database connection .
 
 - spring.datasource.password= `root`

     - Specifies the password for the database connection. 
 
 - spring.datasource.driver-class-name= `com.mysql.cj.jdbc.Driver`

     - Specifies the fully qualified name of the JDBC driver. 
 
 - spring.jpa.hibernate.ddl-auto= `update`

     - Defines the behavior of the Hibernate's automatic schema generation. update creates the schema if it doesn't exist and updates it if it does. 
 
 - spring.jpa.show-sql= `true`

     - Enables logging of SQL statements generated by Hibernate. 
 
 - logging.level.org.springframework= `DEBUG`

     - Sets the logging level for Spring framework classes.
 
### ▶️Running the Application
 
 - Import the Project: Unzip the project file and import it into your IDE (e.g., Eclipse).
 - Create the Database: Create a MySQL database named DailyExpenses.
 - Adjust Configuration: Modify the application.properties as needed.
 - Run the Application: Start the application from your IDE.


# 🔗API Endpoints
 ### Base URL
 - `http://localhost:9982`
## 👥User Endpoints

### Create User

 - Method: POST
 - URL: `/api/users`
 - Description: Creates a new user.
 ### Request Body:
  
   - {
   - "email": "john.doe@example.com",
   - "name": "John Doe",
   - "mobile": "1234567890"
   - }
   
 - Response: Status: 201 Created
 - Body: UserDTO object
### Retrieve User Details
- Method: GET
- URL: ` /api/users/{id}`
- Description: Retrieves details of a user by ID.
- Example URL: `/api/users/1`
- Response: Status: 200 OK
- Body: UserDTO object

## 💰Expenses Endpoints
### Add Expenses
- Method: POST
- URL: `/api/expenses`
- Description: Adds a new expense.
### Request Body: 
   - {
   -  "description": "Dinner",
   - "amount": 120.50,
   - "date": "2023-07-27",
   - "userId": 1,
   - "splits": [

   - {
   - "userId": 1,
   - "amount": 40.17,
   - "splitType": "EQUAL"
   - }
   - {
   - "userId": 2,
   - "amount": 40.17,
   - "splitType": "EQUAL"
   - }
   - {
   - "userId": 3,
   - "amount": 40.16,
   - "splitType": "EQUAL"
   - }
   - ]

   
 - Response: Status: 201 Created
 -  Body: ExpenseDTO object

### Retrieve Individual User Expenses
 - Method: GET

 - URL: `/api/expenses/user/{userId}`
 - Description: Retrieves all expenses for a specific user by user ID.
 - Example URL: `/api/expenses/user/1`
 - Response: Status: 200 OK
 - Body: List of ExpenseDTO objects
 - 
###  Retrieve Overall Expenses
 - Method: GET
 - URL: `/api/expenses/overall`
 - Description: Retrieves all expenses in the system.
 - Response: Status: 200 OK
 - Body: List of ExpenseDTO objects
### Download Balance Sheet
 - Method: GET
 - URL: `/api/expenses/download/{userId}`
 - Description: Generates and downloads a balance sheet for a specific user.
 - Example URL: `/api/expenses/download/1`
 - Response: Status: 200 OK
 - Headers: 
 - Content-Disposition: attachment; filename=balance_sheet.csv
 - Content-Type: `application/csv`
 -  Body: CSV file
## 🗄️Database Structure

- The database structure consists of the following tables:

 ### users: 
- Stores user details such as email, name, and mobile number.
 ### expenses: 
 - Stores expense details including description, amount, date, and user ID.
### splits: 
- Stores information about how expenses are split among users.
