# User Routes Documentation

## Endpoints

### 1. Register User
**Endpoint:** `/users/register`  
**Method:** `POST`  
**Description:** Registers a new user.  

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Responses:**
- **201 Created:**  
  ```json
  {
    "user": { "email": "user@example.com", ... },
    "token": "jwt_token"
  }
  ```
- **400 Bad Request:**  
  ```json
  {
    "errors": [
      { "msg": "Email must be a valid email address", ... },
      { "msg": "Password must be at least 3 characters long", ... }
    ]
  }
  ```

---

### 2. Login User
**Endpoint:** `/users/login`  
**Method:** `POST`  
**Description:** Logs in an existing user.  

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Responses:**
- **200 OK:**  
  ```json
  {
    "user": { "email": "user@example.com", ... },
    "token": "jwt_token"
  }
  ```
- **401 Unauthorized:**  
  ```json
  {
    "errors": "Invalid credentials"
  }
  ```
- **400 Bad Request:**  
  ```json
  {
    "errors": [
      { "msg": "Email must be a valid email address", ... },
      { "msg": "Password must be at least 3 characters long", ... }
    ]
  }
  ```

---

### 3. Get User Profile
**Endpoint:** `/users/profile`  
**Method:** `GET`  
**Description:** Retrieves the profile of the authenticated user.  

**Headers:**
- `Authorization: Bearer <jwt_token>`

**Responses:**
- **200 OK:**  
  ```json
  {
    "user": { "email": "user@example.com", ... }
  }
  ```
- **401 Unauthorized:**  
  ```json
  {
    "errors": "Unauthorized access"
  }
  ```

---

### 4. Logout User
**Endpoint:** `/users/logout`  
**Method:** `GET`  
**Description:** Logs out the authenticated user.  

**Headers:**
- `Authorization: Bearer <jwt_token>`

**Responses:**
- **200 OK:**  
  ```json
  {
    "message": "Logged out successfully"
  }
  ```
- **400 Bad Request:**  
  ```json
  {
    "errors": "Error message"
  }
  ```

---
