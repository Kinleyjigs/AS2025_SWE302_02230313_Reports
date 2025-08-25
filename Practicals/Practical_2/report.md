# Software Testing & Quality Assurance Practical Report

## Module Practical: Software Testing & Quality Assurance

### Objective
To implement and test a simple Go HTTP server with CRUD operations for an in-memory "Users" API, using Go's standard library for unit testing and coverage analysis.

---

### Project Setup

- **Directory Created:** `go-crud-testing`
- **Go Module Initialized:**  
  ```
  go mod init crud-testing
  ```
- **Files Created:**
  - `main.go` (server entry point)
  - `handlers.go` (CRUD logic)
  - `handlers_test.go` (unit tests)


### Server Implementation

- **User Structure:**  
  Defined in `handlers.go` as:
  ```go
  type User struct {
      ID   int    `json:"id"`
      Name string `json:"name"`
  }
  ```
- **In-Memory Storage:**  
  Used a map and mutex for thread safety.
- **CRUD Handlers:**  
  - `getAllUsersHandler` (GET /users)
  - `createUserHandler` (POST /users)
  - `getUserHandler` (GET /users/{id})
  - `updateUserHandler` (PUT /users/{id})
  - `deleteUserHandler` (DELETE /users/{id})

- **Server Setup:**  
  Used `chi` router and middleware in `main.go`.

- **Dependency Installed:**  
  ```
  go get github.com/go-chi/chi/v5
  ```


### Unit Testing

- **Testing Tools Used:**  
  - `testing` package
  - `net/http/httptest` for mock requests/responses

- **Test Cases Written:**  
  - Create User
  - Get User (found & not found)
  - Delete User

- **Test Example:**  
  Each test resets the state, simulates HTTP requests, and checks status codes and response bodies.


### Running Tests & Coverage

- **Run Tests:**  
  ```
  go test -v
  ```
  Output shows all tests passing.

- **Check Coverage:**  
  ```
  go test -v -cover
  ```
  Example output:
  ```
  coverage: 85.7% of statements in ./...
  ```

- **Generate Visual Coverage Report:**  
  ```
  go test -coverprofile=coverage.out
  go tool cover -html=coverage.out
  ```
  This opens an HTML report showing which lines were covered (green) and which were not (red).

### Screenshots

- **Terminal Commands:**  

![alt text](<practical2_images/Screenshot 2025-08-25 at 10.11.12 PM.png>)

![alt text](<practical2_images/Screenshot 2025-08-25 at 10.12.34 PM.png>)

- **Code Coverage UI:**  

![alt text](<practical2_images/Screenshot 2025-08-25 at 10.13.44 PM.png>)

### Analysis & Reflection

- **Coverage Achieved:**  
  High coverage (>80%) indicates robust testing.
- **Visual Feedback:**  
  The HTML report helps identify untested code paths, guiding further test writing.
- **Best Practices:**  
  - Isolate logic for easy testing.
  - Use table-driven tests for more scenarios.
  - Aim for high coverage, but focus on critical logic and edge cases.

---

### Conclusion

This practical demonstrates the process of writing, running, and analyzing unit tests for a Go HTTP server. The use of Go's built-in tools makes it straightforward to ensure code reliability and maintainability.

---
### Repository link 

https://github.com/Kinleyjigs/AS2025_SWE302_02230313_practical2.git

---
