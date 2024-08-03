## **API Endpoints for Password Reset Functionality**

### 1. **Forgot Password**
   - **URL:** `/api/users/forgotPassword`
   - **Method:** `POST`
   - **Description:** Requests a password reset link to be sent to the user's email.
   - **Request Payload:**
     ```json
     {
       "email": "user@example.com"
     }
     ```
   - **Responses:**
     - **200 OK:** Reset link sent successfully.
       ```json
       {
         "status": true,
         "message": "Reset link sent successfully"
       }
       ```
     - **400 Bad Request:** Email not provided.
       ```json
       {
         "status": false,
         "message": "Enter your email"
       }
       ```
     - **404 Not Found:** User does not exist.
       ```json
       {
         "status": false,
         "message": "User doesn't exist"
       }
       ```
     - **500 Internal Server Error:** Error sending email or server error.
       ```json
       {
         "status": false,
         "message": "Email not sent"
       }
       ```

### 2. **Verify Password Reset Link**
   - **URL:** `/api/users/verifyLink/:id/:token`
   - **Method:** `GET`
   - **Description:** Verifies the validity of the password reset link.
   - **Path Parameters:**
     - `id`: User ID (e.g., `66adfb88377f3aa4d443c403`)
     - `token`: JWT token (e.g., `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2NmFkZmI4ODM3N2YzYWE0ZDQ0M2M0MDMiLCJpYXQiOjE3MjI2NzkxMzQsImV4cCI6MTcyMjkzODMzNH0.CUh2ctpVfKiGS0CAE1wtTbzvawWN66L_Iqp08Fdv-M4`)
   - **Responses:**
     - **200 OK:** Token is valid.
       ```json
       {
         "status": true,
         "message": "Token is valid"
       }
       ```
     - **400 Bad Request:** Invalid or expired token.
       ```json
       {
         "status": false,
         "message": "Invalid or expired token"
       }
       ```
     - **404 Not Found:** User not found.
       ```json
       {
         "status": false,
         "message": "User not found"
       }
       ```
     - **500 Internal Server Error:** Server error.
       ```json
       {
         "status": false,
         "message": "Internal server error"
       }
       ```

### 3. **Update Password**
   - **URL:** `/api/users/updatePassword/:userId`
   - **Method:** `POST`
   - **Description:** Updates the user's password.
   - **Path Parameter:**
     - `userId`: User ID (e.g., `66adfb88377f3aa4d443c403`)
   - **Request Payload:**
     ```json
     {
       "newPassword": "newpassword123"
     }
     ```
   - **Responses:**
     - **200 OK:** Password updated successfully.
       ```json
       {
         "status": true,
         "message": "Password updated successfully"
       }
       ```
     - **400 Bad Request:** Missing user ID or new password.
       ```json
       {
         "status": false,
         "message": "Missing user ID or new password"
       }
       ```
     - **404 Not Found:** User not found.
       ```json
       {
         "status": false,
         "message": "User not found"
       }
       ```
     - **500 Internal Server Error:** Server error.
       ```json
       {
         "status": false,
         "message": "Internal server error"
       }
       ```
