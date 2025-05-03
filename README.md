# 🏠 Airbnb Clone Project

The **Airbnb Clone Project** is a full-stack web application that replicates the core features of Airbnb’s booking platform. It allows users to list properties, make bookings, write reviews, and manage profiles within a secure and scalable system. This project is designed to simulate a real-world development experience, focusing on backend architecture, database modeling, API development, CI/CD automation, and secure deployments.


---

## 🧑‍🤝‍🧑 Team Roles

This project simulates a professional software development team, where each member takes on a specialized role. These roles ensure smooth collaboration, clear responsibilities, and high-quality delivery.

### 🧠 Project Manager (PM)
- **Responsibilities:** Leads project planning, coordinates tasks, and ensures timely delivery. Acts as a liaison between team members and stakeholders.
- **Contribution:** Keeps the team aligned with goals, removes blockers, and ensures consistent progress.

### 👨‍💻 Backend Developer
- **Responsibilities:** Implements core server-side logic using Django. Develops API endpoints and business logic for features like booking, property listing, and user management.
- **Contribution:** Delivers scalable, secure backend services that power the application.

### 🧮 Database Administrator (DBA)
- **Responsibilities:** Designs the MySQL database schema, ensures data consistency, manages indexes, and performs database tuning.
- **Contribution:** Builds and maintains efficient relational structures for storing and retrieving project data.

### 🌐 API Developer
- **Responsibilities:** Develops GraphQL APIs for dynamic and efficient client-server communication. Handles schema design and resolver logic.
- **Contribution:** Offers a flexible interface for frontend consumption while maintaining tight integration with backend logic.

### 🛡️ Security Engineer
- **Responsibilities:** Enforces secure access through authentication and authorization. Implements rate limiting, input validation, and data encryption.
- **Contribution:** Protects the application from vulnerabilities such as SQL injection, CSRF, and brute-force attacks.

### 🔁 DevOps Engineer
- **Responsibilities:** Sets up CI/CD pipelines using GitHub Actions and Docker. Automates testing, building, and deployment workflows.
- **Contribution:** Ensures reliable, fast deployments and streamlines the development process with minimal manual intervention.


## 🧰 Technology Stack

This project leverages a modern, scalable technology stack that enables rapid development, clean architecture, and secure deployment. Each tool plays a specific role in building and maintaining the platform.

### 🔧 Django
A high-level Python web framework used to build the backend logic of the application. Django facilitates rapid development and includes built-in support for creating RESTful APIs, managing user authentication, and enforcing security best practices.

### 🗃️ MySQL
A relational database management system used to store structured data such as users, bookings, listings, reviews, and transactions. MySQL ensures data integrity, supports complex queries, and integrates seamlessly with Django's ORM.

### 🌐 GraphQL
An API query language that allows clients to request exactly the data they need. GraphQL improves performance and flexibility over traditional REST APIs, reducing over-fetching and under-fetching of data.

### 🐳 Docker
A containerization tool used to package the application and its dependencies into portable containers. Docker ensures consistent environments across development, testing, and production.

### ⚙️ GitHub Actions
A CI/CD automation tool integrated with GitHub. It runs workflows for testing, linting, and deploying code automatically whenever changes are pushed to the repository.

### 🔒 JWT (JSON Web Tokens)
Used to securely transmit authentication data between the client and server. JWT enables stateless authentication by encoding user session data into signed tokens.

### 🛠️ Markdown
Used to format project documentation, including this README. Markdown ensures the documentation is clean, readable, and easy to maintain.



## 🗄️ Database Design

The Airbnb Clone Project uses a relational database structure (MySQL) to manage interconnected data across multiple core entities. Below is an overview of the key tables and their relationships.

### 👤 Users
Stores data related to registered users, including hosts and guests.
- `user_id` (Primary Key): Unique identifier for each user.
- `email`: User’s login credential (must be unique).
- `password_hash`: Encrypted password for secure authentication.
- `full_name`: User's full name.
- `role`: Defines whether the user is a guest, host, or admin.

### 🏠 Properties
Represents the listings that users (hosts) can create and manage.
- `property_id` (Primary Key): Unique ID for the property.
- `owner_id` (Foreign Key → Users): ID of the host who owns the property.
- `title`: Short title or name of the property.
- `location`: Physical address or city of the property.
- `price_per_night`: Cost for one night of booking.

### 📅 Bookings
Handles reservations made by users for available properties.
- `booking_id` (Primary Key): Unique ID for the booking.
- `user_id` (Foreign Key → Users): Guest who made the booking.
- `property_id` (Foreign Key → Properties): The property being booked.
- `start_date`: Check-in date.
- `end_date`: Check-out date.

### ✍️ Reviews
Contains feedback submitted by guests about a property after a stay.
- `review_id` (Primary Key): Unique ID for each review.
- `user_id` (Foreign Key → Users): Author of the review.
- `property_id` (Foreign Key → Properties): Property being reviewed.
- `rating`: Numeric rating (e.g., 1–5 stars).
- `comment`: Optional text feedback.

### 💳 Payments
Tracks payment transactions related to bookings.
- `payment_id` (Primary Key): Unique ID for the payment.
- `booking_id` (Foreign Key → Bookings): Associated booking.
- `amount`: Total payment amount.
- `payment_date`: Date the transaction was processed.
- `status`: Status of payment (e.g., completed, failed, pending).

---

### 🔗 Entity Relationships

- One **User** can own multiple **Properties**.
- One **User** can make many **Bookings**.
- One **Property** can have many **Bookings** and **Reviews**.
- Each **Booking** is linked to one **User** and one **Property**.
- One **Booking** corresponds to one **Payment**.
- One **User** can write multiple **Reviews**, each for a **Property** they've booked.



## ⚙️ Feature Breakdown

The Airbnb Clone Project is built around core features that replicate the functionality of a real-world booking platform. Each feature has been designed to enhance the user experience and align with best practices in web application development.

### 👤 User Management
Allows users to register, log in, update their profiles, and manage authentication securely. User roles (guest, host, admin) determine access rights and available actions within the platform.

### 🏠 Property Management
Hosts can create, update, and delete property listings. Each listing includes details such as title, location, price per night, and availability, enabling guests to browse and book accommodations.

### 📅 Booking System
Enables guests to book available properties for specific date ranges. It handles validation for overlapping bookings and ensures accurate date tracking and cost calculation.

### ✍️ Review System
Guests can submit reviews after a stay, including a numeric rating and optional feedback. This helps build trust and provides future users with insights into property quality and host reliability.

### 💳 Payment Processing
Handles secure payment transactions for bookings. Includes payment status tracking and ensures that bookings are only confirmed once payments are successfully processed.

### 🔐 Authentication & Authorization
Implements secure login with hashed passwords and JWT-based authentication. Authorization ensures that only permitted users can perform actions such as editing a property or accessing payment records.

### 📊 Admin Dashboard (Optional)
Admins can view all users, listings, and transactions in the system. This feature supports moderation, system health monitoring, and data analytics.


## 🔐 API Security

Securing the backend APIs is essential to protect user data, prevent unauthorized access, and maintain trust within the platform. The Airbnb Clone Project incorporates several critical security measures to ensure safe interactions between clients and the server.

### ✅ Authentication
We use JWT (JSON Web Tokens) for stateless authentication, ensuring that only verified users can access protected resources. This prevents unauthorized users from performing actions like booking a property or accessing account details.

### 🔓 Authorization
Role-based access control is enforced throughout the platform. For example, only hosts can manage properties, and only admins can view system-wide analytics. This ensures users can only perform actions relevant to their role, preventing privilege escalation.

### 📉 Rate Limiting
To prevent brute-force attacks and abuse of public endpoints, rate limiting will be implemented. It restricts the number of requests a user or IP can make within a given time frame, safeguarding the platform from denial-of-service (DoS) threats.

### 🔐 Data Encryption
All sensitive user data, including passwords and payment details, is encrypted in transit (via HTTPS) and at rest (where applicable). Passwords are securely hashed using modern algorithms such as bcrypt.

### 🚫 Input Validation & SQL Injection Protection
All user input is sanitized and validated at both frontend and backend levels. Django’s ORM helps protect against SQL injection, while additional checks ensure proper data formatting and type safety.

---

### 🔒 Why Security Matters

- **User Data Protection:** Ensures personal information (emails, passwords, etc.) is not exposed or misused.
- **Secure Transactions:** Payment data must be handled with care to avoid financial fraud or data theft.
- **Platform Integrity:** Prevents malicious actors from hijacking sessions, exploiting endpoints, or flooding the system.
- **Trust & Compliance:** A secure platform earns user trust and aligns with legal requirements for data privacy and security.


## 🚀 CI/CD Pipeline

CI/CD (Continuous Integration and Continuous Deployment) is a software development practice that automates the process of testing, building, and deploying code. It ensures that every code change is validated through automated tests and is quickly deployed to the production environment without manual intervention.

### 🔄 Why CI/CD is Important

Implementing CI/CD pipelines significantly reduces development time, minimizes human error, and ensures higher code quality. For this project, CI/CD helps automate testing after every commit, detect issues early, and speed up deployment cycles — making the development process more reliable and efficient.

### 🛠️ Tools Used

- **GitHub Actions:** Automates workflows like running tests, linting code, and deploying the app when changes are pushed to the repository.
- **Docker:** Ensures consistent environments across development, staging, and production by containerizing the application and its dependencies.
- **pytest/Django Test Suite:** Used to automatically run unit and integration tests as part of the CI pipeline to verify functionality before deployment.
- **Docker Hub (optional):** Can be used to host container images that are built and deployed automatically via GitHub Actions.

