1. Purpose

Build a secure backend system using Spring Boot 3 + Spring Security + JWT to handle authentication without sessions (stateless).

2. Core Features
User Authentication
Register and login endpoints
JWT issued after successful login
Password Security
Uses BCrypt to hash passwords (not stored in plain text)
JWT Token System
Access Token (short-lived)
Refresh Token (used to generate new access tokens)
Role-Based Authorization
Different access levels (e.g., USER, ADMIN)
Controlled using Spring Security configurations
Logout Mechanism
Invalidates tokens (usually via blacklist or DB flag)
Exception Handling
Custom responses for unauthorized/forbidden access
3. Tech Stack
Spring Boot 3 → Backend framework
Spring Security → Authentication & authorization
JWT → Stateless security mechanism
BCrypt → Password hashing
Maven → Build tool
PostgreSQL → Database
4. Project Flow

Step 1: Registration

User submits details
Password hashed using BCrypt
Stored in DB

Step 2: Login

Credentials validated
JWT token generated
Token returned to client

Step 3: Access Protected APIs

Client sends JWT in header
Server validates token
Grants access based on roles

Step 4: Token Refresh

Refresh token used to get new access token

Step 5: Logout

Token invalidated (DB/blacklist approach)
5. Setup Steps
Clone repo
Create PostgreSQL DB: jwt_security
Configure DB in application.properties

Build:

mvn clean install

Run:

mvn spring-boot:run

Access app:

http://localhost:8080
6. Key Files (Important Components)
SecurityConfig.java → Security rules
JwtService.java → Token creation & validation
AuthController.java → Login/Register APIs
UserDetailsServiceImpl.java → Load user from DB
RefreshTokenService.java → Handle refresh tokens
